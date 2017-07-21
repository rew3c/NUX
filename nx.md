## NX GUID
namespace-classname.xmodifier guid

### 基本选择器
id选择器:不使用  
class选择器:推荐使用  
标签选择器:不单独使用，能保证唯一性时慎用,统一重置浏览器样式或其它css框架样式除外

### 命名方式
1. 组件类名:项目(或公司)css命名前缀-类名
2. 组件细节有修改:组件类名.x修饰符
3. 组件后代元素：组件类名-后代元素类名

### 代码示例

```
.rx-header { height:60px; }
.rx-header-logo { ... }
.rx-header-logotext { ... }

/* 以下选择器错误，在NX规范中，不存在后代的后代元素类名 */
.rx-header-logo-text { ... }
```
