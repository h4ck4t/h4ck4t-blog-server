2024-04-28 WEEK17 SUN 23-06-06 先简单把博客的框架梳理一下

- Django框架
  - Models
  - Views
  - Templates
- 数据库配置
  - SQLite, MySQL等等
- WSGI服务器
- 静态文件和媒体文件处理
- Docker配置
  - Dockerfile
  - docker-compose.yml
- 环境管理
  - 数据库密码及密钥 -> 环境变量
- 安全性考虑
- 日志和监控

2024-04-28 WEEK17 SUN 23-12-57 是否可以实现服务器通过获取github私有库来访问博客内容?

1. Personal Access Token
2. 在 Django 项目的设置文件中添加环境变量来存储 GitHub 访问令牌
3. Django 服务器可以通过 GitHub API 来访问仓库中的内容
4. 可以使用 Python 的 requests 库来发送 HTTP 请求，获取仓库中的文件列表、下载文件内容等
5. 可以设置一个定时任务（使用 Django 的 celery 库或 Python 的 schedule 库）

```
import requests

def get_github_content():
    url = "https://api.github.com/repos/用户名/仓库名/contents/路径"
    headers = {'Authorization': 'token 你的访问令牌'}
    response = requests.get(url, headers=headers)
    if response.status_code == 200:
        return response.json()  # 返回文件列表或内容
    else:
        return None

```