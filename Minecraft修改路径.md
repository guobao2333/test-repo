# 说明
果宝手把手教你使用`mt管理器`修改`Minecraft基岩版`的存储路径
- 将内部存储路径`Android/data/com.mojang.minecraftpe`
- 修改为`games/com.mojang`

> **本教程建议使用支持`markdown`文档格式的软件或网站查看，来获得更好的阅读体验**

## 目录
1. [准备工作](#第一步-准备工作)
2. [打开安装包](#第二步-打开安装包)
3. [打开dex文件](#第三步-打开dex文件)
4. [定位代码](#第四步-定位代码)
5. [修改代码](#第五步-修改代码)
6. [保存并签名](#第六步-保存并签名)

### 第一步 准备工作
- 获取`Minecraft基岩版`安装包
- 准备`mt管理器`或者`np管理器`

### 第二步 打开安装包
- 使用mt/np管理器打开安装包
> **教程使用mt管理器**
  1. 点击安装包
  2. 点击`查看`

### 第三步 打开dex文件
- 使用Dex++编辑器打开dex文件
  1. 点击`classes.dex`
  2. 点击Dex++编辑器
  3. 弹出Multidex窗口，只需要用到第一个dex，不需要全选

### 第四步 定位代码
- 搜索并确认代码位置
  1. 打开后点击第三个`新搜索`
  2. 点击`发起新搜索`
  3. 查找内容填`com.mojang.minecraftpe.MainActivity`
  > **`搜索子目录`一定要勾选！搜索类型选择`类名`**
  4. 点击搜索结果第一个`MainActivity`
  5. 进入后点击右上角三个点，再点击`搜索`
  6. 然后填写以下代码，并点击`搜索`
  ```smali copy
  invoke-virtual {p0, v0}, Lcom/mojang/minecraftpe/MainActivity;->getExternalFilesDir(Ljava/lang/String;)Ljava/io/File;
  ```
### 第五步 修改代码
- 指定代码的删除和修改
  1. 将搜索的代码替换为以下代码
  ```samli copy
  invoke-static {}, Landroid/os/Environment;->getExternalStorageDirectory()Ljava/io/File;
  ```
  2. 删除这行上面代码`const/4 v0, 0x0`

### 第六步 保存并签名
- 保存并退出，然后勾选自动签名，你可以更换签名文件。

- 好了现在你可以重新安装Minecraft并体验外部存储路径了。
