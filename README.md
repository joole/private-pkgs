# packages
packages for OpenWRT or LEDE

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
