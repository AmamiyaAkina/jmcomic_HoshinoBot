## jmcomic_HoshinoBot （原项目由[SlightDust](https://github.com/SlightDust)开发，为二次修改）

原项目地址：[jmcomic_HoshinoBot](https://github.com/SlightDust/jmcomic_HoshinoBot)

功能：下载并加密指定jmid的漫画并上传到群文件。基于[hect0x7/JMComic-Crawler-Python](https://github.com/hect0x7/JMComic-Crawler-Python)，适用于[HoshinoBot](https://github.com/Ice9Coffee/HoshinoBot)。  
需要Python3.9+

## 安装方法
1. 在module目录下克隆本仓库 `git clone https://github.com/AmamiyaAkina/jmcomic_HoshinoBot.git`
2. 下载依赖 `pip install jmcomic PyPDF2 img2pdf pyzipper`
3. 前往`jm_config.yml`配置你的JMComic账号密码（如需要）
4. 前往`jmcomic_HoshinoBot.py`配置你的HTTP HTTPS代理（如需让主机走梯下本的话，默认为关）
5. 在`__bot__.py`的`module`中添加`jmcomic_HoshinoBot`
6. 在群内发送`enable jmcomic`以启用本插件

## 注意事项
本项目是为应对无API接口的下载情况而生，所以如果你没有代理，或者不需要代理，就无需动相关有关代理配置的代码（大概能跑吧）
`jm_config.yml`的`base_dir`是下载的全部图片文件的路径，`pdf_dir`是输出pdf的路径，如果是Windows用的话要改成Windows的路径格式(反斜杠太不优雅了)。这个配置文件的其他设置可以参考[jmcomic配置文件指南](https://jmcomic.readthedocs.io/zh-cn/latest/option_file_syntax/#)。  
加密PDF、压缩包均会保存至`pdf_dir`

默认情况下，仅允许`SUPERUSER`权限的用户开启本插件，可以按需求修改`manage_priv`。    
默认情况下，文件密码是jmid的倒序，可以改`enctypt_pdf`和`encrypt_zip`的password传参设置别的密码。  


## 遗留问题
- 下载的文件会全部积攒在硬盘中，没有做自动清理。
- 如果是体积太大的本子会传不上去 ~~（这好像是NapCat的问题）~~

## 更新日志
2025.05.06 可用  
2025.05.08 加密PDF文件的输出路径读取`jmcomic_config.yml`by[@NekoYSure](https://github.com/NekoYSure)；本地存在目标jmid文件时直接上传。增加依赖`pyyaml`。  
2025.05.09 可选上传1.未加密pdf、2.加密pdf、3.加密zip+未加密pdf、4.加密zip+加密pdf。增加依赖`pyzipper`。  
2025.05.10 增加了一个记录正在下载的列表，尝试下载已经在下载中的本子时发提示并return。优化提示。  

2026.02.09 增加了代理配置，增加了下载时读取漫画名


## 杂谈
群友看本需求激增，变相推动一波技术革新吧，此前走的是API下本，但貌似上游的API炸了，遂考虑让项目走代理，一劳永逸，顺便小改了一下核心代码以外的部分。
且用且珍惜，HoshinoBot也是半死不活的，更别说配套的插件了，很多都年久失修，但好在是曾经辉煌过
