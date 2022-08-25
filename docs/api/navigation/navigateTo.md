---
layout: default
title: to
nav_order: 1
parent: 导航
grand_parent: API

---

# to
## 说明
跳转到指定页面/副屏页

## 使用
```javascript
TinyAPI.navigation.to(uri, options)
```

## 示例
```javascript
// 跳转新页面（所有选项）,uri需根据路由表生成填写，该模版只做参考
TinyAPI.navigation.to(
    "assets://cart.js",
    {
        params: {
            a: 1,
            b: "aaaaaa",
        },
        closeSelf: false,
        callback: function (res) {
            console.log(res);
        },
    }
);

// 跳转新页面（只填路径）
TinyAPI.navigation.to("assets://com.sunmi.demo/pages/storage.js");
```

## 参数

| 属性     | 类型     | 默认值 | 必填  | 说明                                                                                           | 最低版本支持 |
|:-------|:-------|:------|:----|:---------------------------------------------------------------------------------------------|:-----------|
| uri    | string | - | 是   | 路由跳转地址（schema + js路径地址）例如：schema：跳转类型（assets, file, http, https, sub, lsub）,具体schema值参照生成路由表 | v0.3.0 |
| option | object | - | 否   | 路由跳转信息                                                                                       | v0.3.0 |

### option参数

| 属性 | 类型                                  | 默认值 | 必填 | 说明                                                                                            | 最低版本支持 |
|:----|:------------------------------------|:------|:-----|:----------------------------------------------------------------------------------------------|:-----------|
| params | string / integer / boolean / object | - | 否 | 跳转页面传递过去的参数，类型支持String，Integer，Boolean, Object(Object只支持基础类型，不支持Function类型)                   | v0.3.0 |
| closeSelf | boolean                             | false | 否 | 打开新页面是否关闭自身页面(跳转副屏页时不可用🚫)                                                                    | v0.3.0 |
| callback | function                            | - | 否 | 当前页面关闭时，在上一页面回调方法（如果调用[@navigateBack](navigateBack)方法时有传递params，则会在此回调中将params回传；跳转副屏页时不可用🚫） | v0.3.0 |

### schema参数

| 属性     | 类型     | 默认值 | 必填  | 说明                                       | 最低版本支持 |
|:-------|:-------|:----|:----|:-----------------------------------------|:-----------|
| assets | string | -   | -   | 跳转主屏页面                                   | v0.3.0 |
| sub    | string | -   | -   | 跳转副屏页面（与主页生命周期绑定，且只能在主屏页面&非lsub副屏页面进行跳转） | v0.3.0 |
| lsub   | string | -   | -   | 跳转副屏页面（生命周期独立，且只能在主屏页面和非sub副屏页面进行跳转）     | v0.3.0 |

