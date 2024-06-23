
  <h1 align="center">PikPak自动邀请</h1>


## 目录

- [作者](#作者)
- [上手指南](#上手指南)
  - [本地运行](#本地运行)
  - [GitHub Actions运行（每日云端定时自动运行）](#GitHubActions运行)
- [文件目录说明](#文件目录说明)
- [说明](#说明)

### 作者

临渊

邮箱：<1577242215@qq.com>

### 上手指南

#### 本地运行

##### 使用前的配置

在使用本项目前请确保你具有以下环境

1. Python[推荐Python3.9~~别问为什么，我就是3.9，别的我不知道能不能运行~~]（如未安装请查看[Python安装教程](https://blog.csdn.net/maiya_yayaya/article/details/131828467?ops_request_misc=&request_id=&biz_id=102&utm_term=python如何安装&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-131828467.142^v100^pc_search_result_base7&spm=1018.2226.3001.4187)）
2. pip（如未安装请查看[pip安装及如何加速安装第三方组件](https://blog.csdn.net/figo0423/article/details/136146344?ops_request_misc=%7B%22request%5Fid%22%3A%22171784122216800226579490%22%2C%22scm%22%3A%2220140713.130102334..%22%7D&request_id=171784122216800226579490&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-7-136146344-null-null.142^v100^pc_search_result_base7&utm_term=pip如何安装&spm=1018.2226.3001.4187)）

##### **安装步骤**

1. 克隆项目到本地，如无法克隆也可以直接从右上角下载zip压缩包到本地解压

```shell
git clone https://github.com/LinYuanovo/pikpak_auto_invite.git
```

2. 进入到项目目录

```shell
cd pikpak_auto_invite
```

3. 安装项目所需依赖（如安装有问题自行换源）

```shell
pip install -r requirements.txt
```

##### 效果演示

在项目目录下用终端输入或利用`Pycharm`等工具直接运行`run.py`

```shell
python run.py
```

![效果演示](https://raw.hgithub.xyz/LinYuanovo/pic_bed/main/pikpak_auto_invite/7c010670-6d0c-41c0-8ad5-d6dab5e6bf02.png)

如果需要查看请求返回信息，请将主程序`run.py`的`DEBUG_MODE`参数设为True

如果多次出现IP问题可尝试将自己所用的魔法设置为代理，即主程序`run.py`的`PROXY`参数

如果觉得模型不够满意也可以查看我的另一个项目[Ddddocr 自训练今日校园、PikPak验证码模型](https://github.com/LinYuanovo/ddddocr_models)里面包含了几个版本的模型以及数据集，可以自己进行训练

#### GitHubActions运行

1. 点击项目右上角进行**fork**，也可以顺手点个**star**

    ![对项目进行fork](https://raw.hgithub.xyz/LinYuanovo/pic_bed/main/pikpak_auto_invite/f43174c1-1576-4ab0-b86f-31355b400887.png)

2. 然后点击你fork的项目中的**Settings**，找到**Secrets and variables**，选中**Actions**里的**New repository secret**添加一个环境变量，名称必须为**INVITE_CODE**，内容就填你的邀请码

    ![添加变量](https://raw.hgithub.xyz/LinYuanovo/pic_bed/main/pikpak_auto_invite/8ad57054-1c8b-4100-8e24-ab8d6ef51899.png)

    ![添加变量](https://raw.hgithub.xyz/LinYuanovo/pic_bed/main/pikpak_auto_invite/1a702216-0a12-44c4-8067-54eb8e34e7c5.png)

3. 点击你项目上方的**Actions**，第一次打开可能需要点击 `I understand...`，来启用actions

4. 提交修改来触发Actions，建议直接修改`run.py`，在空白的地方输入一次换行**commit**提交即可

    ![修改run.py](https://raw.hgithub.xyz/LinYuanovo/pic_bed/main/pikpak_auto_invite/44e7cf20-658a-4400-99a3-35babc2d5834.png)

    ![提交修改](https://raw.hgithub.xyz/LinYuanovo/pic_bed/main/pikpak_auto_invite/cca72584-36be-4b16-b0bb-141899eaa1b5.png)

5. 点开**Actions**查看运行日志

    ![查看日志](https://raw.hgithub.xyz/LinYuanovo/pic_bed/main/pikpak_auto_invite/3e58af4c-bf57-496c-9129-d237fd0aae7d.png)

    ![查看日志](https://raw.hgithub.xyz/LinYuanovo/pic_bed/main/pikpak_auto_invite/2cbadd33-bb64-4619-bc38-f86b3bd59ed8.png)

    至此操作完成，每天早十点、晚六点十分各定时执行一次（可以自己到`/.github/workflows/run.yml`中修改定时），可以以同样方式进入**Actions**查看日志

### 文件目录说明

```
pikpak_auto_invite 
├── /.github/
│  │──  /workflows/
│  │  │── run.yml       	Github Actions配置文件
├── README.md
├── /models/
│  │── pikpak3.0.onnx       图像识别模型
│  │── pikpak4.0.onnx       图像识别模型
│  │── charsets.json        配置
├── /temp/                  缓存验证图片
├── run.py                  程序主入口
├── image.py                处理图片
└── recognize.py            图像识别
```

### 说明

