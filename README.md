# Kawaii-gcc 让GCC变得可爱
让你的GCC编译器变得可爱！

本项目通过修改GCC的输出信息的本地化文件的方式让GCC变得可爱。

欢迎贡献更多有趣的内容。

## 依赖
- GNU GCC
- GNU Gettext

## 如何使用？
### ArchLinux

- 编辑`/etc/locale.gen`, 将`zh_CN.UTF-8 UTF-8`取消注释
    ```bash
    sudo nano /etc/locale.gen

    # 取消zh_CN.UTF-8 UTF-8的注释

    #zh_CN.GB18030 GB18030
    #zh_CN.GBK GBK
    zh_CN.UTF-8 UTF-8
    #zh_CN GB2312
    #zh_HK.UTF-8 UTF-8
    #zh_HK BIG5-HKSCS
    #zh_SG.UTF-8 UTF-8
    #zh_SG.GBK GBK
    ```
- 执行`locale-gen`

    ```bash
    sudo locale-gen
    ```

- 编辑`/etc/locale.conf`, 设定 LANG 变量`LANG=zh_CN.UTF-8`

    ```bash
    sudo nano /etc/locale.conf
    LANG=zh_CN.UTF-8
    ```

- 安装任意中文字体包 (如果没有安装)

    ```bash
    sudo pacman -S wqy-zenhei
    ```

- 安装 `gcc`.

    ```bash
    sudo pacman -S gcc
    ```

- 找到你的语言文件的路径。默认会在 `/usr/share/locale/zh_CN/LC_MESSAGES/gcc.mo`. 如果已有相关文件，备份之。 (eg. `sudo mv gcc.mo gcc.mo.bak`) 如果没有相关文件，无需担心，什么都不需要做。

- 通过以下命令克隆该仓库并编译仓库中的`po` 文件然后将其复制到刚才的路径去。

    ```bash
    git clone https://github.com/Bill-Haku/kawaii-gcc
    cd kawaii-gcc
    msgfmt gcc-zh.po -o gcc.mo && sudo cp gcc.mo /usr/share/locale/zh_CN/LC_MESSAGES/gcc.mo
    ```

- 修改环境变量以将终端语言改为中文：

    ```bash
    vim ~/.bashrc
    
    # Add the following lines
    export LANG="zh_CN.UTF-8"
    export LANGUAGE="zh_CN.UTF-8"
    # Save it in Vim

    source ~/.bashrc
    ```

- 现在你的GCC已经变得可爱了。

    你可以使用附带的 `test.cc` 来试试效果。

    ```bash
    gcc test.cc -Wall
    # -Wall 表示让GCC输出所有警告信息
    ```

### macOS & Windows

暂未实现。欢迎贡献。

## 特别鸣谢

本项目的灵感来自[`gcc-hentai`](https://github.com/Mosklia/gcc-hentai)项目。为了将其推广到日语区，我创建了本仓库、制作了日语版并修改完善了使用说明的诸多细节，最后制作了完全日语的宣传视频发布在YouTube，不料却在Bilibili获得了关注。十分感谢原作者的分享和开源精神。
