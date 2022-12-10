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
    "cart",
    {
        params: {
            a: 1,
            b: "aaaaaa",
        },
        closeSelf: false,
        clear: true,
        callback: function (res) {
            console.log(res);
        },
    }
);

// 跳转新页面（只填路径）
TinyAPI.navigation.to("cart");

// 跳转副屏
TinyAPI.navigation.to("sub://banner")
```

## 参数

| 属性     | 类型     | 默认值 | 必填  | 说明                       | 取值范围 |
|:-------|:-------|:------|:----|:-------------------------|:-----|
| uri    | string | - | 是   | 路由跳转地址（跳转副屏时需添加schema参数） |      |
| option | object | - | 否   | 路由跳转信息                   |      |

### option参数

| 属性        | 类型                                  | 默认值 | 必填 | 说明                                                                                            | 取值范围   |
|:----------|:------------------------------------|:------|:-----|:----------------------------------------------------------------------------------------------|:-------|
| params    | string / integer / boolean / object | - | 否 | 跳转页面传递过去的参数，类型支持String，Integer，Boolean, Object(Object只支持基础类型，不支持Function类型)                   |  |
| closeSelf | boolean                             | false | 否 | 打开新页面是否关闭自身页面(跳转副屏页时不可用🚫)                                                                    |  |
| clear     | boolean                             | false | 否 | 打开新页面是否关闭所有之前页面(跳转副屏页时不可用🚫)                                                                  |  |
| callback  | function                            | - | 否 | 当前页面关闭时，在上一页面回调方法（如果调用[@navigateBack](navigateBack)方法时有传递params，则会在此回调中将params回传；跳转副屏页时不可用🚫） |  |

### schema参数

| 属性     | 类型     | 默认值 | 必填  | 说明                                     | 取值范围   |
|:-------|:-------|:----|:----|:---------------------------------------|:-------|
| sub    | string | -   | -   | 跳转副屏页面（与主页生命周期绑定，且只能在主屏页面和sub副屏页面进行跳转） |  |
| lsub   | string | -   | -   | 跳转副屏页面（生命周期独立，且只能在主屏页面和lsub副屏页面进行跳转）   |  |

