###   Unity  api讲解

**1.Time.deltaTime:**

Update执行了1次，`transform.Translate(0, 0, 1/60 \* 10)`执行一次，物体移动了1/6米

Update1秒内执行了60次，就是`transform.Translate(0, 0, Time.deltaTime \* 10)`乘以60次
相当于 =（每帧时间1/60 \* 速度 \* 60）=10米

Update1秒内执行了N次，就是`transform.Translate(0, 0, Time.deltaTime \* 10)`乘以N次
相当于 =（每帧时间1/N \* 速度 \* N）=10米

```c#
    void Update()
    {
        transform.Translate(0, 0, Time.deltaTime * 10); //物体沿着自身Z轴方向，每秒移                                                          动物体10米运动
    }
```

**2.Input.GetAxis**

```c#
    void FixedUpdate ()
    {
       // vector3.clampMagnitude(vector,maxlength)
       //返回原向量vector的拷贝，并且它的模长最大不超过maxlength的长度
       Cube.position =  Vector3.ClampMagnitude(Cube.position, 5);

       float x= Input.GetAxis("Horizontal");//对应键盘上的A键和D键 或←键和→键
       float z = Input.GetAxis("Vertical"); //对应键盘上的W键和S键 或↑键和↓键
       float h = Input.GetAxis("Mouse X"); //对应X方向上鼠标的移动，在移动设备上也可以这样
       float v = Input.GetAxis("Mouse Y"); //对应Y方向上鼠标的移动，在移动设备上也可以这样
       float m = Input.GetAxis("Fire1");  //对应鼠标左键或left+Ctrl
       float n = Input.GetAxis("Fire2");  //对应鼠标右键或left+Alt
       float k = Input.GetAxis("Fire3");  //对应鼠标中键或left+shift
        float m1 = Input.GetAxisRaw("Fire1");
        //input.getAxis()和input.getAxisRaw()的区别
        //input.getAxis()的返回值m从0渐变为1或者-1
        //input.getAxisRaw()的返回值从0变成1或者-1，没有渐变
        // transform.Translate(x,0,z);
        // transform.Translate(h,0,v);
         transform.Translate(0,0,m1);
    }
```

**3.Vector3 属性**

**forward** Vector3(0, 0, 1)的简码,       也就是向z轴。 
**right** Vector3(1, 0, 0)的简码,             也就是向x轴。 
**up** Vector3(0, 1, 0)的简码,                 也就是向y轴。 
**zero** Vector3(0, 0, 0)的简码。 
**one** 是 Vector3(1, 1, 1)的简码。 
**Vector3.sqrMagnitude** 长度平方（只读的）



**4.Transform 属性**   (Transform是一个类，用来管理该对象的位置，旋转，缩放的基础属性
                                      transform是一个Transform类的实例，直接指向这个对象的transform组件)

**一.成员变量:**

**position：**在世界空间坐标transform的位置。
**localPosition：**相对于父级的变换的位置。如果该变换没有父级，那么等同于Transform.position。
**eulerAngles：**世界坐标系中的旋转（欧拉角）。
**localEulerAngles：**相对于父级的变换旋转角度。
**right：**世界坐标系中的右方向。（世界空间坐标变换的红色轴。也就是x轴。）
**up：**世界坐标系中的上方向。（在世界空间坐标变换的绿色轴。也就是y轴。）
**forward：**世界坐标系中的前方向。（在世界空间坐标变换的蓝色轴。也就是z轴。）
**rotation：**世界坐标系中的旋转（四元数）。
**localRotation：**相对于父级的变换旋转角度。
**localScale：**相对于父级的缩放比例。
**parent：**父对象Transform组件。
**worldToLocalMatrix：**矩阵变换的点从世界坐标转为自身坐标（只读）。
**localToWorldMatrix：**矩阵变换的点从自身坐标转为世界坐标（只读）。
**root：**对象层级关系中的根对象的Transform组件。
**childCount：**子对象数量。
**lossyScale：**全局缩放比例（只读）。

**二.函数**

**Translate:**  用来移动物体的函数，非常常用的一个函数。

```c#
public void Translate (translation : Vector3, relativeTo : Space = Space.Self) : void
```

  把物体向translation方向移动，距离为translation.magnitude。 relativeTo表示这个移动的参考坐标系。



**Rotate: ** 用来旋转物体的函数，非常常用，在知道需要旋转的角度的情况下。如果要让物体旋转到指定位置，需要搭配Quaternion来使用。

```c#
public void Rotate (eulerAngles : Vector3, relativeTo : Space = Space.Self) : void
```

旋转eulerAngles度（3个轴向分别旋转），以relativeTo为参考坐标系



**RotateAround:**  让物体以某一点为轴心成圆周运动。

```c#
public void RotateAround (point : Vector3, axis : Vector3, angle : float) : void
```

让物体以point为中心，绕axis为轴向旋转angle度。保持原来与point的距离。

 

**LookAt:**  让物体的z轴看向目标物体

```c#
public void LookAt (target : Transform, worldUp : Vector3 = Vector3.up) : void
```

让物体的z轴看向target的位置,并以worldUp为y轴指向方向。

```c#
public void LookAt (worldPosition : Vector3, worldUp : Vector3 = Vector3.up) : void
```

让物体看向worldPosition

 

**TransformDirection:**

```c#
public Vector3 TransformDirection (direction : Vector3) : Vector3
```

返回以物体自身为坐标轴的向量direction在世界坐标中的朝向向量。

```c#
public Vector3** TransformDirection (x : float, y : float, z : float) : Vector3
```

同上

 

**InverseTransformDirection**

```c#
public Vector3 InverseTransformDirectionTransformDirection (direction : Vector3) : Vector3

public Vector3 InverseTransformDirection**TransformDirection (x : float, y : float, z : float) : Vector3
```

与TransformDirection相反，从世界坐标转换到自身相对坐标。

 

**TransformPoint**

```c#
public Vector3 TransformPoint (position : Vector3) : Vector3

public Vector3** TransformPoint (x : float, y : float, z : float) : Vector3
```

把一个点从自身相对坐标转换到世界坐标

 

**InverseTransformPoint**

``` c#
public Vector3 InverseTransformPoint (position : Vector3) : Vector3

public Vector3** InverseTransformPoint (x : float, y : float, z : float) : Vector3
```

把一个点从时间坐标转换到自身坐标的位置。

 

**DetachChildren**

```c#
public void DetachChildren () : void
```

把自身所有的子物体的父物体都设成世界，也就是跟自己的所有子物体接触父子关系。

 

**Find**

```c#
public Transform** Find (name : string) : Transform
```

找到一个名字是name的物体并返回

如果没有找到则返回null。如果字符串被/隔离，函数则会像文件路径一样逐级下查。

```c#
// The magical rotating finger
function Update() {
aFinger = transform.Find("LeftShoulder/Arm/Hand/Finger");
aFinger.Rotate(Time.deltaTime\*20, 0, 0);
}
```

