来源：[用 DEVONthink 批量翻译外文 RSS 标题](https://utgd.net/article/8406)

对于DT pro版本：

1. 下载applescript翻译[脚本](https://github.com/malnlda/tools/blob/main/DEVONthink/批量翻译RSS英文标题/dt%20RSS%20Translate%20Pro.scpt)
2. 在 DEVONthink 设置的“Data”标签页中增加一个 custom meta data，可以起名为“translation”，勾选启用新建好的项目，就可以看到订阅列表中多了翻译列。
3. 安装shortcuts[动作](https://www.icloud.com/shortcuts/5b3d389046444b46afd5f54c8edc83be)， 并将脚本中的 Translate Text 相应调整为 Translate Text 1，以便调用新的 Shortcuts 动作。其余操作均与直接翻译标题无异（具体以你实际下载的 Shortcuts 动作名为准，Shortcuts 一旦分享就不能修改，我不能像管理代码那样轻松管理它们）。

```
tell application id &quot;DNtp&quot;
    repeat with r in selected records
        set iName to name of r
        set the clipboard to iName
        try
            set fName to do shell script &quot;shortcuts run &#039;Translate Text&#039;&quot;
            add custom meta data fName for &quot;Translation&quot; to r
        end try
    end repeat
end tell
```

4. 点击文件标题，选择菜单 - 脚本 - 新建的翻译脚本项目。