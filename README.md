# ng-antd-admin
[![CodeFactor](https://www.codefactor.io/repository/github/huajian123/ng-antd-admin/badge)](https://www.codefactor.io/repository/github/huajian123/ng-antd-admin)
![License](https://img.shields.io/badge/License-MIT-blue.svg)
[![Angular](https://img.shields.io/badge/Build%20with-Angular%20CLI-red?logo=angular)](https://www.github.com/angular/angular)

## ✨特性
- 支持最新angular版本
- Support the latest angular version
- 所有组件onPush,性能卓越
- All components onPush, excellent performance
- 代码示例丰富，有完整服务端后台，前后端分离示例
- Rich code examples, complete server background, front-end and back-end separation examples
- 常用工具类，服务， 指令，管道，封装了表格，抽屉，对话框等常用功能
- Common tools, services, instructions, pipelines。Encapsulates common functions such as tables, drawers, and dialog boxes
- <font color=red size=6>全部组件均为独立组件，文件量减少（如果需要module版本，请看[这里](https://github.com/huajian123/ng-antd-admin/releases/tag/v15.0)）</font>
- <font color=red size=6>Standalone Components（module style is [here](https://github.com/huajian123/ng-antd-admin/releases/tag/v15.0)）</font>


# 路由的key(routing key)
key需要设置成路由地址最后一个'/'后的字符串，并且要唯一<br>
The key needs to be set to the string after the last '/' of the routing address, and it must be unique<br>
```typescript
const routes: Routes = [
  {path: '', data: {key: 'login', shouldDetach: 'no'}, component: LoginFormComponent}
];
```
# 栅格系统监听(grid system monitoring) 
```angular2html
enum EquipmentWidth {
  xs,  // (max-width: 575.98px)
  sm,  // (min-width: 576px) and (max-width: 767.98px)
  md,  // (min-width: 768px) and (max-width: 991.98px)
  lg,  // (min-width: 992px) and (max-width: 1199.98px)
  xl,  // (min-width: 1200px) and (max-width: 1599.98px)
  xxl  // (min-width: 1600px)
}
```
使用方式(How to use)
```
  constructor(private windowsWidthService: WindowsWidthService) {
  }
  
  this.windowsWidthService.getWindowWidthStore().pipe(takeUntil(this.destory$)).subscribe(res => {
    this.currentEquipmentWidth = res;
    this.cdr.markForCheck();
  })
```


# 模块不需要预加载(Modules do not need to be preloaded)

```typescript
export const routes: Routes = [
  {
    path: 'contact',
    loadChildren: import(() => './contact/contact.module').then(m => m.ContactModule),
    data: {
      preload: false
    }
  }
];
```


# 模块不需要保存状态(Modules don't need to save state)

```typescript
const routes: Routes = [
  {path: '', data: {key: 'login', shouldDetach: 'no'}, component: LoginFormComponent}
];
```

# 模块中打开新tab页来展示详情，必须设置参数如下(Open a new tab page in the module to display the details, and the parameters must be set as follows)
在data中设置(newTab Set newTab in data)
```typescript
const routes: Routes = [
  {path: '', component: TabsComponent, data: {title: '标签页操作', key: 'tabs'}},
  {path: 'example-detail', component: DetailComponent, data: {newTab:'true', title: '演示详情', key: 'example-detail'}}
];
```

# 缓存页面中指定容器的滚动条(The scroll bar of the specified container in the cache page)
在data中设置scrollContain 为元素选择器 (Set scrollContain as element selector in data)
```typescript
  {path: '', component: KeepScrollPageComponent, data: {title: '缓存滚动条', key: 'keep-scroll-page',scrollContain:['#div-scroll1','#div-scroll2']}}

```

# 路由复用下切换tab调用的临时声明周期如下(The temporary statement cycle of switching tab calls is as follows)

```typescript
_onReuseInit: () => void;
_onReuseDestroy: () => void;

```
直接在目标组件中写出方法名为_onReuseInit或者_onReuseDestroy的方法即可实现<br>
It can be realized by directly writing the method named _onReuseInit or _onReuseDestroy in the target component<br>

### 🏴授权协议License

MIT 
