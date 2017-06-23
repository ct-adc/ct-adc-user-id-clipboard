
# ct-adc-user-id-textarea

将从 Excel 表格中复制的用户 ID，格式化成逗号分隔的字符串（textarea）

## Table of contents

- [项目运行](#项目运行)
- [在线 demo](#在线-demo)
- [目录结构](#目录结构)
- [使用说明](#使用说明)
- [参数说明](#参数说明)
- [JavaScript 部分](#javascript-部分)
- [HTML 部分](#html-部分)
- [Bugs and feature requests](#bugs-and-feature-requests)
- [Thought](#thought)
- [License](#license)

## 项目运行

``` bash
# install dependencies
npm install
or
cnpm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For detailed explanation on how things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

## 在线 demo

Just click there: [Live Demo](http://htmlpreview.github.io/?https://github.com/ct-adc/ct-adc-user-id-textarea/blob/master/view/demo.html).

![demo.gif](./src/img/demo.gif)

## 目录结构

Within the download you'll find the following directories and files, logically grouping common assets and providing both compiled and minified variations. You'll see something like this:

```
ct-adc-pattern-input/
├── ...
├── src/
│   ├── /component
│   │   └── ct-adc-user-id-textarea.vue
│   └── /js
│      └── ... demo ...
└── /view
    └── demo.html
```

## 使用说明

#### 参数说明

```javascript
/**
 * Component Settings
 * @param  {String} separator    用户 ID 之间的分隔符
 * @param  {String} userId       用户 ID
 */
```

#### JavaScript 部分

组件配置项

```javascript
setting: {
  separator: ', ', // 逗号加空格
  userId: '123,223' // 初始值
}
```

#### HTML 部分

组件使用

```html
<user-id-textarea class="form-control"
                  :placeholder="'批量输入用户ID请用英文逗号隔开，最多 ' + max + ' 个用户'" rows="18"
                  :separator="setting.separator"
                  :userId="setting.userId"
                  @change="updateUserId"></user-id-textarea>
```

> 可以想原生组件一样使用 class、rows 等等

## Bugs and feature requests

Have a bug or a feature request? If your problem or idea is not addressed yet, [please open a new issue](https://github.com/ct-adc/ct-adc-user-id-textarea/issues/new).

## Thought

第一版先这样吧

## License

Code released under the [MIT License](https://github.com/ct-adc/ct-adc-user-id-textarea/blob/master/LICENSE).