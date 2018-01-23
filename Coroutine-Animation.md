### 使用协程来实现颜色渐变
```c#
void updata() {
  if (Input.GetKeyDown(KeyCode.Space)) {
    StartCoroutine(fade());
  }
}

IEnumerator fade() {
  for (int i=0;i<1;i+=0.1f) {
    cube.GetComponent<MeshRenderer>().material.color = new Color(i,i,i,i);
    yield return WaitForSeconds(0.1f);
  }
}
```
