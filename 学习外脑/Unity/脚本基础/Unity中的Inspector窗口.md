#Unity #永久 
### 知识点一 私有和保护无法显示编辑
```csharp
private int i1;
protected string str1;
```

### 知识点二 让私有的和保护的也可以被显示SerializeField
加上强制序列化字段[[特性]] `[SerializeField]`
所谓序列化就是把一个对象保存到一个文件或数据库字段中去
```csharp
[SerializeField]
private int privateInt;
[SerializeField]
protected string protectedStr;
```

### 知识点三 公共的可以显示编辑
```csharp
public int publicInt = 10;
public bool publicBool = false;
```

### 知识点四 公共的也不让其显示编辑HideInInspector
在变量前加上[[特性]] `[HideInInspector]`
```csharp
[HideInInspector]
public int publicInt2 = 50;
```

### 知识点五 大部分类型都能显示编辑
```csharp
public int[] array;
public List<int> list;
public E_TestEnum type;
public GameObject gameObj;

//字典不能被Inspector窗口显示
public Dictionary<int, string> dic;
//自定义类型变量
public MyStruct myStruct;
public MyClass myClass;
```

### 知识点六 让自定义类型可以被访问
加上序列化[[特性]]`[System.Serializable]`
字典怎样都不行
```csharp
[System.Serializable]
public struct MyStruct
{
    public int age;
    public bool sex;
}

[System.Serializable]
public class MyClass
{
    public int age;
    public bool sex;
}
```

### 知识点七 一些辅助[[特性]]
```csharp
//1.分组说明特性Header    **************有用**************
//为成员分组
//Header特性
//[Header("分组说明")]
[Header("基础属性")]
public int age;
public bool sex;
[Header("战斗属性")]
public int atk;
public int def;

//2.悬停注释Tooltip
//为变量添加说明
//[Tooltip("说明内容")]
[Tooltip("闪避")]
public int miss;

//3.间隔特性 Space()
//让两个字段间出现间隔
//[Space()]
[Space()]
public int crit;

//4.修饰数值的滑条范围Range    **************有用**************
//[Range(最小值, 最大值)]
[Range(0,10)]
public float luck;

//5.多行显示字符串 默认不写参数显示3行
//写参数就是对应行
//[Multiline(4)]
[Multiline(5)]
public string tips;

//6.滚动条显示字符串 
//默认不写参数就是超过3行显示滚动条
//[TextArea(3, 4)]
//最少显示3行，最多4行，超过4行就显示滚动条
[TextArea(3,4)]
public string myLife;

//7.为变量添加快捷方法 ContextMenuItem    **************有用**************
//参数1 显示按钮名
//参数2 方法名 不能有参数
//[ContextMenuItem("显示按钮名", "方法名")]
[ContextMenuItem("重置钱", "Test")]
public int money;
private void Test()
{
    money = 99;
}

//8.为方法添加特性能够在Inspector中执行
//[ContextMenu("测试函数")]
[ContextMenu("哈哈哈哈")]
private void TestFun()
{
    print("测试方法");
}

```

### 注意
1. Inspector窗口中的变量关联的就是对象的成员变量，运行时改变他们就是在改变成员变量
2. 拖曳到GameObject对象后 再改变脚本中变量默认值 界面上不会改变
    - 要么老老实实的在Inspector窗口改默认值
    - 要么重新挂载脚本
3. 运行中修改的信息不会保存