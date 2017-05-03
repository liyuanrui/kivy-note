
#### 方法1

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






