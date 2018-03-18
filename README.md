# vw
如何在Vue项目中使用vw实现移动端适配，结合

依赖：

NodeJs
NPM
Webpack
Vue-cli
postcss-import
postcss-url
postcss-aspect-ratio-mini
postcss-cssnext
autoprefixer
postcss-px-to-viewport
postcss-write-svg
cssnano
postcss-viewport-units
Viewport Units Buggyfill
著作权归作者所有。
商业转载请联系作者获得授权,非商业转载请注明出处。
原文: https://www.w3cplus.com/mobile/vw-layout-in-vue.html © w3cplus.com

$ npm install -g vue-cli

vue init webpack vw-layout

cd vw-layout
然后执行:

npm run dev

npm i postcss-aspect-ratio-mini postcss-px-to-viewport postcss-write-svg postcss-cssnext postcss-viewport-units cssnano  

module.exports = { "plugins": { "postcss-import": {}, "postcss-url": {}, "postcss-aspect-ratio-mini": {}, "postcss-write-svg": { utf8: false }, "postcss-cssnext": {}, "postcss-px-to-viewport": { viewportWidth: 750, // (Number) The width of the viewport. viewportHeight: 1334, // (Number) The height of the viewport. unitPrecision: 3, // (Number) The decimal numbers to allow the REM units to grow to. viewportUnit: 'vw', // (String) Expected units. selectorBlackList: ['.ignore', '.hairlines'], // (Array) The selectors to ignore and leave as px. minPixelValue: 1, // (Number) Set the minimum pixel value to replace. mediaQuery: false // (Boolean) Allow px to be converted in media queries. }, "postcss-viewport-units":{}, "cssnano": { preset: "advanced", autoprefixer: false, "postcss-zindex": false } } }

npm i cssnano-preset-advanced --save-dev

 "postcss-px-to-viewport": { viewportWidth: 750, // 视窗的宽度，对应的是我们设计稿的宽度，一般是750 viewportHeight: 1334, // 视窗的高度，根据750设备的宽度来指定，一般指定1334，也可以不配置 unitPrecision: 3, // 指定`px`转换为视窗单位值的小数位数（很多时候无法整除） viewportUnit: 'vw', // 指定需要转换成的视窗单位，建议使用vw selectorBlackList: ['.ignore', '.hairlines'], // 指定不转换为视窗单位的类，可以自定义，可以无限添加,建议定义一至两个通用的类名 minPixelValue: 1, // 小于或等于`1px`不转换为视窗单位，你也可以设置为你想要的值 mediaQuery: false // 允许在媒体查询中转换`px` }
 
 <script src="//g.alicdn.com/fdilab/lib3rd/viewport-units-buggyfill/0.6.2/??viewport-units-buggyfill.hacks.min.js,viewport-units-buggyfill.min.js"></script>
 
 <script> window.onload = function () { window.viewportUnitsBuggyfill.init({ hacks: window.viewportUnitsBuggyfillHacks }); } </script>
