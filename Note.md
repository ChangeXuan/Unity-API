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
- 使用content size fitter来进行文本框的大小自适应
- 检测鼠标是否在某个组件上的回调函数
```c#
public void OnPointerEnter(PointerEventData eventData){}
public void OnPointerExit(PointerEventData eventData){}
```
- text组件中的Raycast targer可以控制是否会被射线检测到
- c#的事件机制
```c#
// 在某个类中定义两个事件变量
public static Action<Transform> oneAction;
public statci Action twoAction;
// 定义两个事件函数
public void action_1(Transform actionTransform) {}
public void action_2() {}
// 向事件变量中加入事件函数
xxx.oneAction += action_1;
xxx.twoAction += action_2;
// 检测事件是否为空,并调用
if(oneAction!=null) {
    oneAction(transform)
}
```
- 使用stringBuilder来显示文本框是个很好的选择
- 把鼠标点转换为画布点
```c#
Vector2 position;
RectTransformUtility.ScreenPointToLocalPointInRectangle(GameObject.Find("Canvas").transform as RectTransform,Input.mousePosition,null,out position);
```
- 使用#regison可以让代码折叠
```c#
#region someCode
xxxx
xxx
xxx
#endregion
```
- 鼠标拖拽回调函数
```c#
public void OnBeginDrag(PointerEventData eventData) {
    if (eventData.button == PointerEventData.InputButton.Left) {
    	//
    }
}
public void OnDrag(PointerEventData eventData) {}
public void OnEndDrag(PointerEventData eventData) {}
```
- 拖拽的思路是
```
1.当开始拖拽时，复制当前拖拽的组件跟随鼠标，并记录当前拖拽的组件的原来位置
2.当拖拽到空格子时，射线找寻格子组件并放入
3.当拖拽到有物体的格子时，把格子内的物体放入拖拽组件的原来位置，并把拖拽组件放入该格子
```
- shift+alt等比放大，alt对称放大
- Unity自带的小型数据储存(在windows中存放在注册表)
```c#
PlayerPrefs.SetInt("key",value);
PlayerPrefs.GetInt("key",0);//若该key没有对应的值，则返回0
```
