- AddComponent->给物体添加组件
```C#
GameObject go = GameObject.CreatePrimitive(PrimitiveType.Cube);
go.AddComponent<Rigidbody>();//添加刚体组件
go.AddComponent<API_Time>();//添加脚本组件
```
- activeInHierarchy->判断一个物体在场景中是否是活动状态
```c#
Debug.Log(xxx.activeInHierarchy);//输出true或false
xxx.SetActive(false);//将xxx物体的活动属性设置为false(包括孩子)，可节约性能
```
- activeSelf->判断该物体自己是否是活动状态(只可读)
- tag->物体的标签
```c#
//官网中给出的添加tag的方案是，先在inspector菜单中的tag添加新的tag，然后在代码中激活
//还有一种方法是在代码中动态添加，可见(http://www.xuanyusong.com/archives/3169)
```
- transform->物体的位置信息(无法移除，每个物体都会有)
- GetComponent->获取组件实例
```c#
Debug.Log(xx.GetComponent<Transform>().name)
```
- FindObjectOfType->寻找对象
```c#
Light l = FindObjectOfType<Light>();//获取一个灯光
Transform[] ts = FindObjectsOfType<Transform>();//获取所有Transform组件
foreach(Transform t in ts) {
  
}
```
- Find->根据名称来查找，返回单个值
```c#
GameObject go = GameObject.Find("xxx");
```
- FindGameObjectsWithTag->根据tag来查找，返回数组
```c#
GameObject[] gos = GameObject.FindGameObjectsWithTag("xxx"); 
```
- FindGameObjectWithTag->根据tag来查找，返回单个值
```c#
GameObject go = GameObject.FindGameObjectWithTag("xxx");
```
