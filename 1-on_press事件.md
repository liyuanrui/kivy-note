
#### 方法0

*kv文件 main.kv*
```
BoxLayout:
    orientation: 'vertical'

    Label:
        id: time
        text: ''

    Button:
        id: lr
        text: 'hello'
```

*py文件 ki.py*
```
from kivy.app import App

class MainApp(App):
    def on_start(self):
        self.root.ids.lr.on_press=self.test
        
    def test(self):
        self.root.ids.time.text='hello world'
        
MainApp().run()
```

#### 方法1

*kv文件 main.kv*
```
<MyLayout>:

    orientation: 'vertical'

    Label:
        id: time
        text: ''

    Button:
        id: lr
        text: 'hello'
```

*py文件 ki.py*
```
from kivy.app import App
from kivy.uix.boxlayout import BoxLayout

class MyLayout(BoxLayout):
    pass

class MainApp(App):
    def build(self):
        return MyLayout()
    def on_start(self):
        self.root.ids.lr.on_press=self.on_press

    def on_press(self):
        self.root.ids.time.text='hello world'
MainApp().run()
```


#### 方法2

*kv文件 main.kv*
```
<MyLayout>:

    orientation: 'vertical'

    Label:
        id: time
        text: ''

    Button:
        id: lr
        text: 'hello'
        on_press:root.on_press()
```

*py文件 ki.py*
```
from kivy.app import App
from kivy.uix.boxlayout import BoxLayout

class MyLayout(BoxLayout):
    def on_press(self):
        self.ids.time.text='hello world'

class MainApp(App):
    def build(self):
        return MyLayout()
MainApp().run()
```

#### 方法3

*kv文件 main.kv*
```
<MyLayout>:
    label:time
    label2:label
    orientation: 'vertical'

    Label:
        id: time
        text: ''

    Label:
        id: label
        text:''

    Button:
        id: lr
        text: 'hello'
        on_press: root.on_press()
```

*py文件 ki.py*
```
from kivy.app import App
from kivy.uix.boxlayout import BoxLayout
from kivy.properties import ObjectProperty

class MyLayout(BoxLayout):
    label=ObjectProperty()
    label=ObjectProperty()

    def on_press(self):
        self.label.text='hello world'
        self.label2.text='world'


class MainApp(App):
    def build(self):
        return MyLayout()
MainApp().run()
```
