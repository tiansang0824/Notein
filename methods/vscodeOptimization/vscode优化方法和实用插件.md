# vscode优化方法和实用插件

部分设置json文件：

```json
{
  "files.autoSave": "afterDelay",  // 文件修改后自动保存
  "files.autoGuessEncoding": true,  // 自动推断文件编码格式
  "workbench.list.smoothScrolling": true,  // 接下来四个都是平滑设置，用于优化视觉体验
  "editor.cursorSmoothCaretAnimation": "on",
  "editor.smoothScrolling": true,
  "editor.cursorBlinking": "smooth",
  "editor.mouseWheelZoom": true, // 鼠标滚轮设置字体大小
  "editor.formatOnPaste": true,  // 接下来的三项设置和格式化文件有关，配合格式化插件，可以实现高效的格式化
  "editor.formatOnType": true,
  "editor.formatOnSave": true,
  "editor.wordWrap": "on",  // 自动折行
  "editor.guides.bracketPairs": true,  // 接下来是两个括号对的设置，第二个可以废弃
  //"editor.bracketPairColorization.enabled": true, (此设置vscode在较新版本已默认开启)
  "editor.suggest.snippetsPreventQuickSuggestions": false,  // 接下来三项是代码自动补全的功能
  "editor.acceptSuggestionOnEnter": "smart",
  "editor.suggestSelection": "recentlyUsed",
  "window.dialogStyle": "custom", // 用于优化窗口央视
  "debug.showBreakpointsInOverviewRuler": true,  // 断点样式，可以让断点以红色的形式在行号栏显示
}
```

## 插件

基础插件

-   error lens：用于将错误提醒显示在对应行的右侧，而不是在输出窗口中；
-   Path Intellisense：用于输入路径时自动补全功能；
-   `image preview`：可以预览引入的图像；

功能插件

-   codesnap：代码截图
-   `Prettier - Code formatter`"：代码格式化插件，支持很多语言，结合json中设置的保存时格式化代码，可以在保存文件的时候自动格式化代码；
-   `GBK to UTF8 for vscode`：实现编码格式转换；
-   `Doxygen Documentation Generator`：文档生成器；
-   `Remote - SSH`：远程ssh链接服务器；
-   