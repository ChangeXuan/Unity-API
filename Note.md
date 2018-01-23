- 关闭某个组件
```c#
xx.enabled = false;
```
- 键盘的按键映射
```
Normal keys: “a”, “b”, “c” …
Number keys: “1”, “2”, “3”, …
Arrow keys: “up”, “down”, “left”, “right”
Keypad keys: “[1]”, “[2]”, “[3]”, “[+]”, “[equals]”
Modifier keys: “right shift”, “left shift”, “right ctrl”, “left ctrl”, “right alt”, “left alt”, “right cmd”, “left cmd”
Mouse Buttons: “mouse 0”, “mouse 1”, “mouse 2”, …
Joystick Buttons (from any joystick): “joystick button 0”, “joystick button 1”, “joystick button 2”, …
Joystick Buttons (from a specific joystick): “joystick 1 button 0”, “joystick 1 button 1”, “joystick 2 button 0”, …
Special keys: “backspace”, “tab”, “return”, “escape”, “space”, “delete”, “enter”, “insert”, “home”, “end”, “page up”, “page down”
Function keys: “f1”, “f2”, “f3”, …
```
- Verctor是一个结构体，若要修改其中一个坐标
```c#
transform.position = new Verctor3(0,0,0);
// 错误
transform.position.x = 10;
// 正确
Verctor3 newPosition = transform.position;
newPosition.x = 10;
transform.position = newPosition;

```
- 使用时间戳做为随机种子
```c#
Random.InitState((int)System.DateTime.Now.Ticks);
```
