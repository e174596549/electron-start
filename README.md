# Electron 使用方法

- 将你自己项目的入口 HTML 文件名称修改为 index.html
- 将本文件夹内的 main.js 与 package.json 两个文件复制到你项目的入口目录（与 index.html 在一个目录内）
- 打开 package.json 文件按照下面的介绍进行修改 未提及部分不要修改

```javascript
{
    "name": "Minesweeper",// 「name」中的 Minesweeper 替换为你自己的项目名称他是你程序的名字
    "version": "0.1.0",// 「version」是你程序的版本号 可以不用修改
    "main": "./main.js",// 「main」 入口地址 不要修改
    "scripts": {
        "start": "electron .",// 「start」 测试启动方式 不要修改
        "package": "electron-packager ./ Minesweeper --all --out ~/Desktop/Minesweeper --version 1.6.2 --overwrite --icon=./20170309040842376_easyicon_net_128.icns"
    },// 「package」中的 Minesweeper 修改为你的项目名称 「--all」是你要大包的平台 如果是 all 会打包为全平台 如果改为 「--Mac」则只打包为 mac 应用  --platform=win32 --arch=x64 打包win应用「~/Desktop/Minesweeper」是打包后文件的生成地址 默认是桌面 可自行修改 「C:\\Desktop\\Minesweeper」为 Windows 系统下的路径写法「--icon=」后面的部分是你打包应用的图标地址 自行替换
    "devDependencies": {
        "electron": "^1.6.2",
        "electron-packager": "^8.5.2",
        "electron-prebuilt": "^1.4.13"
    }
}
```
- 打开 main.js 文件按照下面的介绍进行修改 未提及部分不要修改
```javascript
    mainWindow = new BrowserWindow({
        width: 1200,// 应用宽度
        height: 800// 应用的高度
    })
```
```javascript
    // 注释后将不显示调试工具
    mainWindow.webContents.openDevTools()
```
## 在命令行工具中找的你的项目入口目录 执行相应命令
- 第一次需要运行 npm install electron -g 全局安装 electron
- 运行 npm install --save-dev electron-prebuilt 安装built工具
- 运行 npm install --save-dev electron-packager 安装打包工具
- 运行 npm start 进行调试
- 调试无问题后 执行 npm run-script package 进行打包 文件默认将生成在桌面
