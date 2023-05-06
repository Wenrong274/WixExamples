# Wix Examples

主要是用來打包程式輸出成 `.msi` 檔（[Windows Installer][wiki]）。

建議先看完 「[30天 | C# WixToolset + WPF 帥到不行的安裝包 系列][30d]」，能夠把 80% 以上的問題解決。

## 輸出 Wix 文件方法

先到 [WiX Toolset Release][wix3] 安裝需要的工具。

需要開啟 [CMD][cmd] 且必須要用`工作管理員權限`打開，之後 cd 到 WiX Toolset 的安裝資料夾。

```text
C:\Program Files (x86)\WiX Toolset v3.11\bin
```

![img_1]

### heat.exe

可以掃描目錄中的所有文件和子目錄，並生成 WiX 文件中所需的 Component、Directory、File 和其他元素的定義。

使用下面的參數可以拿到 `myKeyIn.wxs`。需要把 [MyDemo] 替換成正確的路徑，可以參考我的 `Product.wxs`。

```text
heat.exe dir "[PUT_YOUR_PATH]" -dr INSTALLFOLDER -cg ProductComponents -gg -gl -sf -srd -var "[MyDemo]" -out "[PUT_YOUR_OUTPUT_PATH]\myKeyIn.wxs"
````

| 參數名稱               | 解釋                   |
| :--------------------- | :--------------------- |
| [PUT_YOUR_PATH]        | 需要打包的路徑資料夾   |
| [MyDemo]               | WiX 文件中要使用的變數 |
| [PUT_YOUR_OUTPUT_PATH] | WiX 文件的路徑         |

![img_2]

## Wix Code


## 參考文章

[用 WiX 制作安装包：创建一个简单的 msi 安装包][wixblog]

[30天 | C# WixToolset + WPF 帥到不行的安裝包 系列][30d]

[Create an Uninstall Shortcut][wix1]

[Create a Shortcut on the Start Menu][wix2]

[Removing files when uninstalling WiX][Cleanup]

________________________________________________________________________________

[30d]:https://ithelp.ithome.com.tw/users/20139206/ironman/3901
[wix1]:https://wixtoolset.org/docs/v3/howtos/files_and_registry/create_uninstall_shortcut/
[wix2]:https://wixtoolset.org/docs/v3/howtos/files_and_registry/create_start_menu_shortcut/
[Cleanup]:https://stackoverflow.com/a/17513551
[wix3]:https://github.com/wixtoolset/wix3/releases
[wixblog]:https://blog.walterlv.com/post/getting-started-with-wix-toolset-msi-hello-world
[cmd]:https://zh.wikipedia.org/zh-tw/cmd.exe
[wiki]:https://zh.wikipedia.org/zh-tw/Windows_Installer
[img_1]:https://i.imgur.com/ovuJCka.png
[img_2]:https://i.imgur.com/SbjBwmv.png
