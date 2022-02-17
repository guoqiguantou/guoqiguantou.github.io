# 图表属性

模版上选中组件后右侧就会展示对应的图表属性，图表属性用来扩展组件对组件进行配置。如图：

<img src="/img/iShot2022-02-08 13.35.25.png"  width="500"   />

1、为组件绑定图表属性组件：组件添加静态方法getEditProps返回数组，数组的第一项固定是数据源组件，后面还可以加多个属性组件，pType可以填组件名字符串或组件。

<img src="/img/iShot2022-02-08 14.09.24.png"  width="350"   /><img src="/img/iShot2022-02-08 11.38.53.png"  width="350"   />

2、属性组件可以放在公共props目录下（pType填组件字符串），也可以写在项目内部（pType填组件）

<img src="/img/iShot2022-02-08 14.58.10.png"  width="350"   /><img src="/img/iShot2022-02-08 14.58.48.png"  width="380"   />

下面代码可以看到如果pType填字符串，就会去公共props目录下去匹配

```
Inspector.js
... 
// 判断属性组件
const { pType } = item;
const PropElement = typeof pType === 'string' ? compProps[pType] : pType;
if (!PropElement) {
  throw "找不到属性组件" + item.pType;
}
...
```

3、属性组件内部可以获取组件数据和修改组件数据的方法

```
const { data, update } = props;
update(Object.assign({}, data, value));
```

4、组件内部可以获取组件数据和修改组件数据的方法

```
const { editComponentProps, _id, data } = this.props;
editComponentProps(_id, ['cmpHideProps'], currentConfig);
```





