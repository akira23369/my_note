#Unity #永久 
![[Pasted image 20240304151356.png]]
![[markmap 2.html]]


### 成员变量
```csharp
// 名字
this.gameObject.name = "改名desu";
// 是否激活
bool activeSelf = this.gameObject.activeSelf;
// 是否静态
bool isStatic = this.gameObject.isStatic;
// 层级
int layer = this.gameObject.layer;
// 给游戏对象分的标签
string tag1 = this.gameObject.tag;
```

### 静态方法
#### 创建自带几何体
```csharp
// 创建自带几何体
GameObject gameObject1 = GameObject.CreatePrimitive(PrimitiveType.Cube);
gameObject1.name = "自己起的名字";
```

#### 在场景中查找对象
```csharp
// 在场景中查找对象         
// 1.1 单个查找    名字(同名不行)
// 查找效率低    会查询所有场景中所有的对象
GameObject gameObject2 = GameObject.Find("自己起的名字");
print(gameObject2?.name);

// 1.2 单个查找     tag
GameObject gameObject3 = GameObject.FindWithTag("MainCamera");
print(gameObject3?.name);

// 1.3 通过Inspector面板去拖到本地的public

// 2 多对象查找      tag
GameObject[] gameObjects = GameObject.FindGameObjectsWithTag("Player");
print(gameObjects?.Length);

// FindObjectOfTypes    效率低

```


#### 克隆对象
根据一个GameObject对象, 创建一个一模一样的对象
```csharp
GameObject.Instantiate(MyObj);
```


#### 删除
1. 删除一个指定游戏对象
2. 删除一个指定脚本对象

**注意:**
Destroy方法不会马上移除对象, 只是加了一个移除标识
一般情况下, 会在下一帧时把这个对象从内存中移除
```csharp
// 删除对象
GameObject.Destroy(gameObject4, 5);         // 第二个参数是延时几秒
// 删除脚本对象
GameObject.Destroy(this);

// 一定要马上移除
GameObject.DestroyImmediate(gameObject4);
```


#### 切场景不移除
默认情况下, 切场景会移除该场景的所有对象
```csharp
GameObject.DontDestroyOnLoad(this.gameObject);      // 不移除该脚本依附的游戏对象
```

### 成员方法
#### 创建空物体
```csharp
GameObject gameObject5 = new GameObject("创建的空物体名字", typeof(Test2));
```

#### 动态给GameObject对象添加脚本
```csharp
// 给gameObject5加上Test2脚本
Test2 test2 = gameObject5.AddComponent<Test2>();
```

#### 获取脚本对象 和[[Mono中的重要内容#^155e67 | 继承Mono的类]]获取脚本对象的方法一毛一样

#### 标签比较
```csharp
if (gameObject5.CompareTag("Player"))
{
	print("对象标签是Player");
}
if (gameObject5.tag == "Player")
{
	print("这和上面是一样的");
}
```

#### 设置 失活 和 激活
```csharp
gameObject5.SetActive(false);       // 失活
```


#### 不建议使用的成员方法
通过广播或者发送消息的形式, 让自己或者别人 执行某些行为和方法
```csharp
// 让自己去执行TestFun这个函数, 会在自己挂着的所有脚本去找这个名字的函数, 有一个执行一个
// 涉及到反射    比较影响性能
this.gameObject.SendMessage("TestFun");

// 广播行为 让自己及其子对象 执行相同的名字的方法
this.gameObject.BroadcastMessage("TestFun");

// 让自己及其父对象发送消息并执行
this.gameObject.SendMessageUpwards("函数名");
```


继承自Object自然可以用Object.xxx的方式来调用静态函数




