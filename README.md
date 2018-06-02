# packages
Extra packages for OpenWRT or LEDE

## 使用方法

假定你已知晓如何编译 OpenWrt 或 LEDE 的固件

#### 编辑`feeds.conf`文件，加入下面一行

```
src-git joole https://github.com/joole/private-pkgs.git
```

#### 运行下面的命令

```bash
./scripts/feeds update -a
./scripts/feeds install -a
```

## 目录结构介绍
 + lang : 编程语言需要的额外包
 + libs ：通用系统类库包（c/c++）
 + luci : luci-app-主要存放这里
 + net ： 网络相关模块存放
 + util ：通用模块存放
