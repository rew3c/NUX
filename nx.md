## NX GUID
namespace-name.xmodifier guid

### 命名方式
1. 组件类名:项目(或公司)css命名空间前缀-组件名称
2. 组件后代元素：组件类名-后代元素类名(不存在后代的后代选择器命名方式，不管是一级后代元素还是二级后代元素，都按此方式命名)

### 修饰符
1. 使用场景:当页面中存在两个相似的视觉或功能模块，将其提取为组件后，加修饰符来修改具体细节
2. 用法限制:修饰符不能单独使用，必须配合类名或后代类名使用
3. 命名原则:修饰符统一以x字母开头，后面跟修饰符名
4. "x"解析:避免与引入的其它样式库的类名冲突,x开头的单词最少，且为中文修饰符的第一个字母

### 选择器
+ id选择器禁止使用
+ 能保证唯一性时慎用标签选择器，重置浏览器或其它样式库组件除外
+ 慎用后代选择器，只有当存在修饰符时，或后代为唯一的标签选择器时，才允许使用后代选择器

### 代码示例
```
/* 头部 */ 
.nx-header { height:60px; }
.nx-header-logo { padding-top:12px;  }
.nx-header-logotext { font-size:16px; }

/* 小头部:用修饰符更改细节 */ 
.nx-header.xsmall { height:45px; }
.nx-header.xsmall .nx-header-logo { padding-top:8px; }
.nx-header.xsmall .nx-header-logotext { font-size:14px; }

/* 小头部:直接在后代元素上更改细节 */
.nx-header-logo.xsmall { padding-top:8px;  }
.nx-header-logotext.xsmall { font-size:14px; }
```

### 错误示例

| 错误写法 | 正确写法 | 错误说明 |
| ------- | -------- | --- |
| #nx-card | .nx-card | id选择器禁止使用 |
| .card | .nx-card | 必须有类命名空间前缀 |
| .nx-card li | .nx-list > li | 污染性太大，不能确定后代li选择器的唯一性 |
| .nx-card .nx-card-header | .nx-card-header | 无意义的父类限定 |
| .nx-card-header-text | .nx-card-hdtext | 不存在后代的后代元素类名 |
| .xblue | .nx-card.xblue | 修饰符不能单独使用 |
| .nx-card.blue | .nx-card.xblue | 修饰符必须以字母x开头 |
