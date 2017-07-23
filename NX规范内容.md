## NUX GUID
.namespace-unit.xmodifier

### 名词解释
1. 样式单元：指页面中有明显视觉边界的视觉单元或完整的功能模块(如:导航，布局结构等)。
2. 功能单元：指整站通用的单一功能性样式(如: `.nux-xhide { display:none; }` )

### 命名方式
1. 样式单元：命名空间-单元名称(如: `.nux-nav` )；
2. 后代元素：样式单元-后代元素类名(如: `.nux-nav-link`  或  `.nux-nav-linkico` )。
3. 功能单元：命名空间-x功能名称(如: `.nux-xhide` )

### 修饰符
1. 使用场景：当一个样式单元类某些小细节需要修改时，加修饰符来控制需要修改部份的样式；
2. 用法限制：修饰符不能单独使用，必须配合组件或组件后代元素一起使用；
3. 命名原则：修饰符统一以x字母开头，后面跟修饰符名；
4. "x"解析：避免与引入的其它样式库的类名冲突。

### 选择器
+ 禁止使用ID选择器；
+ 慎用标签选择器,除非能够保证其唯一性；
+ 慎用后代选择器，只有当存在修饰符时，或后代为唯一的标签选择器时，才允许使用后代选择器。

### 代码示例
```
/* 头部 */ 
.nux-header { height:60px; }
.nux-header-logo { padding-top:12px;  }
.nux-header-logotext { font-size:16px; }

/* 小头部:用修饰符更改细节 */ 
.nux-header.xsmall { height:45px; }
.nux-header.xsmall .nux-header-logo { padding-top:8px; }
.nux-header.xsmall .nux-header-logotext { font-size:14px; }

/* 小头部:直接在后代元素上更改细节 */
.nux-header-logo.xsmall { padding-top:8px;  }
.nux-header-logotext.xsmall { font-size:14px; }
```

### 错误示例

| 错误写法 | 正确写法 | 错误说明 |
| ------- | -------- | --- |
| `#nux-card` | `.nux-card` | 禁止使用ID选择器 |
| `.card` | `.nux-card` | 必须有命名空间前缀 |
| `.nux-card li` | `.nux-list > li` | 污染性大，不能确定后代li选择器的唯一性 |
| `.nux-card > .nux-card-header` | `.nux-card-header` | 无意义的父类限定 |
| `.nux-card-header-text` | `.nux-card-headertext` | 样式单元所有后代元素的类名的形式为:样式单元类名-后代类名 |
| `.xblue` | `.nux-card.xblue` | 修饰符不能单独使用 |
| `.nux-card.blue` | `.nux-card.xblue` | 修饰符必须以字母x开头 |
| `.nux-hide {display:none;}` | `.nux-xhide {display:none;}` | 功能单元必须以字母x开头 |
