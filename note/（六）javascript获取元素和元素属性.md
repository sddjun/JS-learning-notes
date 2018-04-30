## 获取元素
##### （一）根据id来获取
- document.getElementById(id名字)

##### （二）根据标签获取元素
- document/元素.getElementsByTagName(标签名)

说明：通过getElementsByTagName获取的元素，是一个集合。

##### （三）根据css选择器来获取
- document/元素.querySelector(css选择器)
- document/元素.querySelectorAll(css选择器)

注意事项：
1. querySelector 当选择器匹配多个元素时，只能找到第一个；
2. querySelector 和 querySelectorAll； 是h5的新增方法，不支持IE8版本以下的浏览器；
3. 通过 querySelectorAll 获取到的是一个集合。


## 元素属性
事物所具有的不可缺少的性质，利用属性可以描述一个对象的特性和功能。

### 属性的操作
- 读操作：el.属性名
- 写操作（包括增加属性和改写属性）：el.属性名 = val
- 删除属性：delete el.属性名

### 操作属性的方式
- 点（.）——该方式操作的是元素的自身属性，使用场景为命名符合命名规则；
- 中括号（[]）——该方式的使用场景为属性名不符合命名规则或属性名存在变量中。

### 常用属性，详解和特殊属性注意事项
1. ``element.id``设置或返回元素的 id
2. ``element.innerHTML``设置或者返回元素的内容，可包含节点中的子标签以及内容
3. ``element.innerText``设置或者返回元素的内容，不包含节点中的子标签以及内容
4. ``element.className``设置或者返回元素的类名
5. ``element.style``设置或返回元素的样式属性。
- 注意：操作的是元素的行间样式，因此要获取某个样式需要将该样式定义到行间
- 使用方法：
style[样式名] = 值
```
element.style.background = "#fff";
```
- 特别说明 style 的 cssText 属性，node.style.cssText()， 设置元素的行间样式，它的作用是替换行间样式，而非新增行间样式

6. ``element.value``设置或返回表单控件的值
7. ``element.title``设置或返回元素的标题内容
8. ``element.classList``返回元素的类名集合的数组。使用方法：
- 增加class
    - 方法：node.classList.add(class1, class2, ...)
    - 描述：在元素中添加一个或多个类名，如果指定的类名已存在，则不会添加
- 删除 class
    - 方法：node.classList.remove(class1, class2, ...)
    - 描述：移除元素中一个或多个类名。移除不存在的类名，不会报错。
- 切换 class
    - 方法：node.classList.toggle(class, true|false)
    - 描述：在元素中切换类名。第一个参数为要在元素中移除的类名，并返回 false，如果该类名不存在则会在元素中添加类名，并返回 true。第二个是可选参数，是个布尔值用于设置元素是否强制添加或移除类，不管该类名是否存在。
    - 注意： Internet Explorer 或 Opera 12 及其更早版本不支持第二个参数。
- 判断 class
    - 方法：node.classList.contains(class)
    - 描述：返回布尔值，判断指定的类名是否存在。
- 索引 class
    - 方法：node.classList.item(index)
    - 描述：返回类名在元素中的索引值，索引值从 0 开始，如果索引值在区间范围外则返回 null。
9. ``element.src``设置或返回图像的 URL，该属性获取的是图片的绝对路径。
