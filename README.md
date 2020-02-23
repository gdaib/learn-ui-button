# 学习 B 站 vueTypeScript 代码
视频链接: https://www.bilibili.com/video/av83946465/?spm_id_from=333.788.videocard.2

## 技术栈
1. vue
2. typeScript
3. less


## 技巧梳理

## style 中定义的变量可以在 css 中用 var 关键字 访问

```html
style = '--color-tint: $color';

background: var(--color-tint);
```

## less 中使用 mixins
```css
.className(@size) {
    font-size: @size;
}

.a {
    .className(14px);
}
```


## vscode 中的 settings/files.exclude 
这个是用来隐藏项目中不必要的文件的，免得显得眼花缭乱

```json
{
    "files.exclude": {
        "**/.git": true,
        "**/.svn": true,
        "**/.hg": true,
        "**/CVS": true,
        "**/.DS_Store": true,
        "**/node_modules": true,
        "**/.eslintrc.js": true,
        "**/.gitignore": true,
        "**/.browserslistrc": true,
        "**/tsconfig.json": true, 
        "**/babel.config.js": true,
    }
}
```