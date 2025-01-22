## 前言

今天给大家分享一款非常实用的微信聊天机器人——`chatgpt-on-wechat`，由@zhayujie大佬开发。该项目支持多种大模型（国内外），并且可以部署在个人微信、公众号和企业微信上。它不仅能处理文本、语音、图片，还支持联网功能、绘图功能以及知识库功能。

废话不多说，直接进入正题。

👉 [WildCard | 一分钟注册，轻松订阅海外线上服务](https://bit.ly/bewildcard)

---

## 一、准备工作

1. **服务器**：需要一台服务器（国内外均可），或者选择本地部署。
2. **远程连接工具**：如果是本地部署则不需要，推荐使用可视化的 BT 面板。
3. **ChatGPT 账号**：需要一个 ChatGPT 账号，用于生成 API KEY。
4. **微信小号**：建议使用微信小号以防万一。

---

## 二、部署方式

### 1. Docker 部署

#### 下载 `docker-compose.yml` 文件

bash
wget https://open-1317903499.cos.ap-guangzhou.myqcloud.com/docker-compose.yml


将文件复制到服务器上，等待下载完成后打开配置文件。

#### 修改配置

下载完成后，打开 `docker-compose.yml` 文件，重点修改以下三个变量：

- **`OPEN_AI_API_KEY`**：从 [OpenAI 官网](https://bit.ly/bewildcard) 生成的 API KEY。
- **`PROXY`**：如果是海外服务器无需填写；本地部署需要填写（如 `127.0.0.1:xxxx`，其中 `xxxx` 是代理端口号）。
- **`OPEN_AI_API_BASE`**：代理地址。如果是国内服务器，可以通过填写代理地址进行反代。

其他变量请参考 [ReadMe.md](https://bit.ly/bewildcard) 进行配置。

#### 启动服务

bash
sudo docker compose up -d


#### 查看日志

运行以下命令查看运行日志：

bash
sudo docker logs -f chatgpt-on-wechat


日志中会生成一个二维码，使用微信小号扫描即可。

---

### 2. 本地部署

#### 代码拉取

bash
git clone https://github.com/zhayujie/chatgpt-on-wechat


如果不熟悉 Git，可以直接下载 ZIP 包。

#### 运行环境

建议 Python 版本在 3.7.1~3.9.X 之间，推荐使用 3.8 版本。3.10 及以上版本在 MacOS 上可用，但其他系统可能存在兼容性问题。

#### 安装依赖

在项目目录下运行以下命令安装依赖：

bash
pip3 install -r requirements.txt


扩展依赖（可选，建议安装）：

bash
pip3 install -r requirements-optional.txt


#### 配置文件

项目根目录下有一个 `config-template.json` 文件，复制该模板并重命名为 `config.json` 文件。然后按照 Docker 部署教程修改以下变量：

- **`OPEN_AI_API_KEY`**
- **`PROXY`**
- **`OPEN_AI_API_BASE`**

#### 启动项目

bash
python3 app.py


终端输出二维码后，使用微信扫描。当输出 “Start auto replying” 时，表示自动回复程序已成功运行。

---

## 三、演示

以下是项目的部分功能演示，包括对话功能和 GPT-4-Turbo 的 Dalle-3 绘图功能：

![演示图片](https://i-blog.csdnimg.cn/blog_migrate/58f9683235105d482cf9e7ec45bcfade.jpeg)

---

## 四、总结

该项目功能强大，支持多种扩展功能。虽然目前集成了 MJ，但需要使用 LinkAI 的接口，性价比不高。希望后续能新增 `midjourney-proxy` 项目代码，进一步提升用户体验。

👉 [WildCard | 一分钟注册，轻松订阅海外线上服务](https://bit.ly/bewildcard)