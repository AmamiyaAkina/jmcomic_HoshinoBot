## jmcomic_HoshinoBot （原项目由[SlightDust](https://github.com/SlightDust)开发，为二次修改）

原项目地址：[jmcomic_HoshinoBot](https://github.com/SlightDust/jmcomic_HoshinoBot)

功能：下载并加密指定jmid的漫画并上传到群文件。基于[hect0x7/JMComic-Crawler-Python](https://github.com/hect0x7/JMComic-Crawler-Python)，适用于[HoshinoBot](https://github.com/Ice9Coffee/HoshinoBot)。  
需要Python3.9+

## 安装方法
1. 在module目录下克隆本仓库 `git clone https://github.com/AmamiyaAkina/jmcomic_HoshinoBot.git`
2. 下载依赖 `pip install jmcomic PyPDF2 img2pdf pyzipper`
3. 前往`jm_config.yml`配置你的`base_dir`与`pdf_dir`路径（这个直接决定本子与打包好的PDF会下在哪）
4. 前往`jmcomic_HoshinoBot.py`配置你的HTTP HTTPS代理（如需让主机走梯下本的话，默认为关）
5. 在`__bot__.py`的`module`中添加`jmcomic_HoshinoBot`
6. 在群内发送`enable jmcomic`以启用本插件

## 注意事项
本项目是为应对无API接口的下载情况而生，所以如果你没有代理，或者不需要代理，就无需动代码任何部分，开箱配好路径即用
`jm_config.yml`的`base_dir`是下载的全部图片文件的路径，`pdf_dir`是输出pdf的路径，如果是Windows用的话要改成Windows的路径格式(反斜杠太不优雅了)。加密PDF、压缩包均会保存至`pdf_dir`
这个配置文件的其他设置可以参考[jmcomic配置文件指南](https://jmcomic.readthedocs.io/zh-cn/latest/option_file_syntax/#)。  

默认情况下，仅允许`SUPERUSER`权限的用户开启本插件，可以按需求修改`manage_priv`。    
默认情况下，文件密码是jmid的倒序，可以改`enctypt_pdf`和`encrypt_zip`的password传参设置别的密码。  


## 遗留问题
- 下载的文件会全部积攒在硬盘中，没有做自动清理。
- 如果是体积太大的本子会传不上去 ~~（这好像是NapCat的问题，但Lagrange会报错直接传不上去）~~
- **如是走html代理，则无法下载登录状态才可见的本子（即便是使用`jmcomic`库自带的自动登录插件也是必定会`403`）**

## 更新日志
2025.05.06 可用  
2025.05.08 加密PDF文件的输出路径读取`jmcomic_config.yml`by[@NekoYSure](https://github.com/NekoYSure)；本地存在目标jmid文件时直接上传。增加依赖`pyyaml`。  
2025.05.09 可选上传1.未加密pdf、2.加密pdf、3.加密zip+未加密pdf、4.加密zip+加密pdf。增加依赖`pyzipper`。  
2025.05.10 增加了一个记录正在下载的列表，尝试下载已经在下载中的本子时发提示并return。优化提示。  

2026.02.09 增加了代理配置，增加了下载时读取漫画名
2026.03.12 回滚代码方案，手动更新了一波API domain，但注释保留了终端全局代理方案（万一以后能解决cookies或者登录的问题了呢？）


## 杂谈
原本为了应对上游API炸了，所以写了代理支持，用了两三个月吧，结果自动登录插件会403了，cookies的自动抓取，也抓不到登录状态的cookies，改了半天有点无从下手，所以在功能层面不得不回滚了API方案，凑巧也看见有新的API地址了，然后就，回滚解决了？
我承认我此前说话有点大声了点，在这里先给项目原作者和API维护者磕头了，但如果能实现稳定登录了，那通过本地配置代理的方式，在长远与稳定的角度来看，或许会是更好的选择。但还是那句话，且用且珍惜吧。

<img width="755" height="944" alt="图片" src="https://github.com/user-attachments/assets/2f8545ff-e2e2-496e-9aba-64263386ce88" />
