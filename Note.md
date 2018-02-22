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
- 改变物体的位置或旋转，推荐对刚体进行操作，会比较快
- 在StreamingAssets文件夹中的资源文件在build中不会被合并
- 在编辑器下退出游戏
```c#
UnityEditor.EditorApplication.isPlaying = false;
```
- 有一个比较好的手势插件：easytouch
- 不显示编号为cs0777的警告
```c#
#pragma warning disable 0777
```

- 在StreamingAssets文件夹中的资源文件在build中不会被合并编号
- 在StreamingAssets文件夹中的资源文件在build中不会被合并
- 打开动画快捷键ctrl+6
- get请求
```c#
using LitJson
IEnumerator getText(string url) {
		using (UnityWebRequest www = UnityWebRequest.Get(url)) {
			yield return www.Send();
			if (www.isNetworkError || www.isHttpError) {
				Debug.Log(www.error);
			} else {
				jsonData = JsonMapper.ToObject<NetModel>(www.downloadHandler.text);
			}
		}
	}
```
- 在构建物品时，可先创建一个父类(价格，名字等共有信息)，然后在让武器，防具，物体继承自父类
- 可以把canvas scaler的UIScaleMode设置为scale with screen size让ui自适应
- UI层只负责改变ui的显示，不进行其他负责操作
- 可以使用Resources来加载资源文件
- 使用model来做中间桥梁
