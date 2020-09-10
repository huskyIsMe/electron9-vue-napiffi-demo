# electron-napi-ffi-demo
electron v9 + napi-ffi v3 + cli4 开发的demo，方便快速构建，避免N多大坑
electron调用dll 真的是一个大坑。这里用了一个可用的，且相对版本较新的。
希望方便大家使用

测试使用的Node版本是 12, Electron 版本 8.4.0
npm包为 ffi-napi@3.0.1

## 构建之前，需要保证相关软件（非windows系统）环境都是32或者都是64位位 切记！！！！
## 下面为各个组件判断环境的方法
nodejs   判断环境 https://newsn.net/say/node-arch.html
python   判断环境 在python官网下载，下载2.7版本
electron 

## electron 由于需要tizi，在install的时候会有无法下载的情况，因此有两种方法。推荐方法2
## 下载安装 electron 8.4.0 切记选择对应的版本 32位
## 方法1
electron-v8.4.0-win32-ia32.zip
https://zhuanlan.zhihu.com/p/110448415

## 方法2
## 将electron包下载地址注册位淘宝的镜像:
npm config set ELECTRON_MIRROR https://npm.taobao.org/mirrors/electron/

## 设置npm淘宝源
npm config set registry https://registry.npm.taobao.org/

## 启动项目  注意。项目路径中不能含有中文，否则有可能会报错
npm i <!-- 如果提示c++版本 可以尝试 npm install --msvs_version 2015 -->
npm run electron:serve

## npm的时候，有时候会报vs 2015的错误。我安装的是 vs2017 community版本。直接官网下载即可

## 打包命令 打包时候需要从外网下载包，这里还需要进行额外设置，因为我有环境，所以没有深入研究了
npm run electron:build

## 请注意 dllPath 这个参数需要根据运行环境切换，因为是demo，就不做设置了

```bash