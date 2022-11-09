# 网页版幸运转盘

> 代码最后更新时间：2021/11/27
> Markdown最后更新时间：2022/11/04

该项目源于本人IT项目管理课程的作业，也是本人接触到的第一个网页开发项目。

该项目仅实现了在本地服务器上运行的网页版幸运转盘，用户可从文本文件、EXCEL或者数据库中自动获取数据，在线显示、编辑数据，根据自定义规则以幸运转盘的形式抽取合适数据，页面提供幸运转盘样式定制功能。

该项目后端使用 Python 的 Flask 框架，前端使用 Bootstrap 框架以及 Jquery 等JS库。

你可以通过本项目学习最基础的网页开发（本项目包含大量的中文注释，且结构十分简单），或者在此基础上进一步拓展完善与部署。

!['网页布局'](./doc/%E7%BD%91%E9%A1%B5%E7%89%88%E5%B9%B8%E8%BF%90%E8%BD%AC%E7%9B%98%E6%A0%B7%E5%9B%BE.png)

## 项目需求

1. 实现从数据集中随机选择某一条数据的功能，并显示在界面上

    1. 数据来源

        1. 可以从文本文件、EXCEL或者数据库中获取数据

    2. 数据格式

        1. 用户可以可以定义数据的格式，比如根据什么数据列来抽取，显示什么数据列内容，数据显示的字体和字体大小等

        2. 需要兼容直接从学校下载的教学班点名册

        3. 直接获取数据库中数据时，用户只需要提供表名称和字段就可以获取随机数据

    3. 随机选择规则

        1. 系统随机根据指定的数据列选择某一行数据并显示在转盘上

        2. 某一行数据被抽取后，则该行数据从候选数据列表中标记为已抽取的，后面的抽取动作不能再选择该行数据

        3. 根据指定条件抽取

            1. 用户指定数据选取条件，在满足条件的数据中抽取，如：抽取数据列 > 60 或者数据列 = '1' ，条件可以选择多个，用 && 或 || 来连接

            2. 用户指定数据选取条件，提高满足条件的数据被抽取的概率(如 10 倍概率)

            3. 用户指定数据选取条件，逐步提高满足条件的数据被抽取的概率

                (1) 第一次被抽取后，概率 \* 2
                (2) 第二次被抽取后，概率在第一次的基础上 \* 2
                (3) ......

    4. 随机抽取的方式

        1. 通过界面的按钮进行操作

        2. 通过语音识别的方式进行操作

2. 实现幸运转盘的显示方式

    1. 可以使用转盘的方式

    2. 可以使用将所有数据列出（轮盘）的方式

3. 实现幸运转盘的参数设置

    1. 设置转盘的显示图片

    2. 设置转盘转动时播放的音乐

    3. 设置转盘转动速度的快慢

4. 可自由添加更多功能

## 准备工作

为了运行该项目，你需要首先：

- 构建虚拟环境以及安装依赖

    ```shell
    # 创建虚拟环境
    python -m venv 虚拟环境

    # 激活虚拟环境
    ./虚拟环境/Scripts/activate

    # 安装依赖
    pip install flask
    ```

## 运行项目

- 你可以通过以下命令来运行该项目

    ```shell
    # 虚拟环境下终端：
    python main.py [port]

    # 浏览器输入地址：
    127.0.0.1:[port | 5000]
    ```

## 停止项目

- 你可以通过以下命令来停止该项目

    ```shell
    # 虚拟环境下终端：

    # ctrl + c 停止项目

    # 退出虚拟环境
    deactivate
    ```

## 其他说明

本项目原本是小组作业，但是所有开源的内容均由本人单独完成，另外两人仅负责IT项目文档的编写（而且还只是部分文档...）以及PPT展示，非本人负责内容并未放出，同时对一些敏感文件做了处理（比如点名册），其余不做改动（~~原汁原味的新手代码😆~~）。

注意！本项目并未达成所有项目需求（没时间写完就要答辩了，而且IT项目管理课程重点放在项目管理文档上），部分实现存在明显漏洞（没错就是最复杂的“指定条件抽取中”的“自定义条件”部分，本人只做了最简单的判断，~~这玩意往大了说tm是个编译器~~），同时由于是本人第一次写前端，HTML\CSS各种混搭，ES5\ES6也各种混搭（~~看着也别有一番风味😜~~）...

注意！由于本项目前端把CSS和JS的依赖下载下来固定死了（当时不会npm包管理，并且为了方便打包给老师减少老师操作所以采取这个方式），所有这些依赖不会自动更新（Bootstrap采用的是v4版本，现在v5都出了）！这种做法十分不推荐！切勿模仿！推荐使用NPM包管理或者CDN分发！

由于之前的git提交了过多涉及隐私的内容（之前是gitee上的私有仓库），所以重新初始化了git，可惜了以前的提交记录（见[git提交留念](./doc/git%E6%8F%90%E4%BA%A4%E7%95%99%E5%BF%B5.png))...

注意！本项目大概率**不再更新与维护**（~~除非有人请求我~~）！代码不适合生产环境部署！所有图片等素材来源网络！仅供新手学习参考！~~以及本人怀旧！~~
