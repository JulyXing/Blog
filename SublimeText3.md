####SublimeText3 日常使用技巧
---
1 下载(download)
```
  http://www.sublimetext.com/3
```

2 包管理(package mange)
```
  import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```

3 插件(plug-in)
```
  格式：
  描述
    插件名
    插件链接

  3.1 文件和文件夹增强
    Side​Bar​Enhancements
    https://packagecontrol.io/packages/SideBarEnhancements

  3.2 Html
    Emmet (Zen Coding)
    https://packagecontrol.io/packages/Emmet

  3.3 文件名补全
    Autofilename
    https://packagecontrol.io/packages/AutoFileName

  3.4 代码注释
    Docblockr
    https://packagecontrol.io/packages/DocBlockr

  3.5 代码补全
    SublimeCodeIntel
    https://packagecontrol.io/packages/SublimeCodeIntel

  3.6 Markdown 编辑器 和 预览
    MarkdownEditing      编辑器
    https://packagecontrol.io/packages/MarkdownEditing

    OmniMarkupPreviewer  浏览器预览
    https://packagecontrol.io/packages/OmniMarkupPreviewer

  3.7 Material theme主题
    Material Theme
    https://packagecontrol.io/packages/Material%20Theme
```
4 配置
```
{
    "auto_complete": true,
    "auto_match_enabled": true,
    "color_scheme": "Packages/Material Theme/schemes/Material-Theme.tmTheme",
    "default_encoding": "UTF-8",      // 编码格式
    "default_line_ending": "unix",    // 行尾格式
    "font_face": "Dejavu Sans Mono",  // 字体
    "font_size": 12,          // 字体大小
    "ignored_packages":
    [
        "Markdown",
        "Vintage"
    ],
    "tab_size": 4,   // tab 长度
    "theme": "Material-Theme.sublime-theme",   // 主题
    "translate_tabs_to_spaces": true,   // tab 转换 spaces
    "word_wrap": "true",    // 自动换行
    "wrap_width": 120       // 行长度
}
```