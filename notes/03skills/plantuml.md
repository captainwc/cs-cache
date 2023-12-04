

# PlantUML & Mermaid

## plantUML

### 1 类图

> [类图的语法和功能 (plantuml.com)](https://plantuml.com/zh/class-diagram)

#### 声明元素

类、结构体、枚举、抽象类、接口等

<table style="border:none;text-align:center">
<tr>
    <td>
    	<p style="text-align:left">
            @startuml<br>
            class<br>
            struct<br>
            enum<br>
            abstract<br>
            annotation<br>
            entity<br>
            interface <br>
            protocol<br>
            circle<br>
            ()<br>
            diamond<br>
            <><br>
            @enduml<br>
        </p>
    </td>
        <td>
            <p style="text-align:left">
            <br>
            class<br>
            struct<br>
            enum<br>
            abstract<br>
            annotation<br>
            entity<br>
            interface<br>
            protocol<br>
            circle<br>
            circle2<br>
            diamond<br>
            diamond2<br>
            <br>
            </p>
    </td>
    <td style="width:70%">
    <img src = "https://shuaikai-bucket0001.oss-cn-shanghai.aliyuncs.com/blog_img/plantuml对象.png"></td>
</tr>
</table>

#### 类内风云

- `+` public  `-` private  `#` protected（mermaid中`()*`表示虚函数，`$`表示静态）
- 通过检查`()`来确定是属性还是方法，也可以用`{field}`来指定属性，`{method}`来指定方法
- `{static}`指定静态（下划线），`{abstract}`指定虚函数（斜体）
- 可以自定义类体内的分隔情况，如`--  ==  ..`或者`--xxx--  ==xxx==  ..xxxxx`
- `interface fly <<interface>>`,

#### 注释

- 可以使用`note left of` , `note right of` , `note top of` , `note bottom of`这些关键字来添加备注

- 还可以在类的声明末尾使用`note left`, `note right`,`note top`, `note bottom`来添加
- 单独用`note`这个关键字也是可以的，使用 `..` 符号可以作出一条连接它与其它对象的虚线
- 注释内部可以使用html标签，如
  - `<b>`, `<u>`, `<i>`
  - `<s>`, `<del>`, `<strike>`
  - `<font color="#AAAAAA">` or `<font color="colorName">`
  - `<color:#AAAAAA>` or `<color:colorName>`
  - `<size:nn>` to change font size
  - `<img src="file">` or `<img:file>`: the file must be accessible by the filesystem

#### 类之间关系

关联、依赖、组合、聚合、泛化、实现...

<table style="border:none;text-align:center"><tr><td style="width:55%"><img src = "https://shuaikai-bucket0001.oss-cn-shanghai.aliyuncs.com/blog_img/image-20230606205910714.png"></td><td style="width:45%"><img src = "https://shuaikai-bucket0001.oss-cn-shanghai.aliyuncs.com/blog_img/image-20230606210114046.png"></td></tr></table>

**补充：**棒棒糖接口用`A ()-- B`，即用圆括号表示圆圈⭕

### 2 用例图

> [用例图语法和功能 (plantuml.com)](https://plantuml.com/zh/use-case-diagram)

**省流：**`:user:`或`actor user1 as u1`创建用户，`(case1)`或`usecase case2`创建用例，`rectangle`画方框。线跟别的一样，`note`也跟别的一样。

```bash
@startuml usercase
# 选择布局方向，也可以是 top to down direction
left to right direction
# 可以用 :: 也可以用 actor 来创建用户
:user: ..> (case)
actor usr2 as u2
# 选择包或者方框
package Library {
    rectangle lib {
    # 可以用 () 也可以用 usecase 来表示用例
        # 起别名，方便后续划线
        (图书) as ts
        usecase "管 理员" as gly
        # 这里同样可以使用分割线
        usecase "可以用--分==割..线.."
    }
}
# 线都是通用的
u2 -left-> ts 
u2 --> gly
# 创建注释文本框
note "This note is connected\nto several objects." as N2
# 创建一个有指明方向的注释
note left of u2
hello note
endnote
@enduml
```

## Mermaid

> [小书匠语法说明之mermaid ](http://soft.xiaoshujiang.com/docs/grammar/feature/mermaid/#e7b1bbe59bbe_36)

图形种类

```
classDiagram	   类图
sequenceDiagram    序列图，即几列一放，你对我说啥我对你说啥
stateDiagram-v2	   状态图，即多了个起点和终点的流程图
graph			  流程图，即方框箭头方框箭头
pie				  饼图
journey			  用户行程图
gantt		      甘特图
```

#### 类图

- 注释：`%% xxxx`
- 布局方向：`direction LR RL TB BT`  
- 注解：使用 《》框住，如《interface》
- 返回类型：直接跟在括号后面即可（比plantUML智能），如`getName() string`
- 虚函数：括号后面加`*`，变为斜体，如`fly()* void`
- 静态：`$`



