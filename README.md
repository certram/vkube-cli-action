# Use this action to deploy your service

## 使用步骤

1. 在仓库的 **Settings → Secrets and variables→ Actions → New repository secret** 中添加以下 Secrets：
    - `DOCKERHUB_TOKEN`: 含义： Docker Hub 的访问 Token
    - `DOCKERHUB_USERNAME`: 含义： Docker Hub的用户名
    - `GHCR_TOKEN`: 含义：GitHub Container Registry 的访问 Token

2. 示例工作流文件：

```yaml
name: Deploy with vkube-cli

on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: your-username/vkube-deploy-action@v1
        with:
        vkube_config_file: './VKubefile.yaml' #这里根据自己的VKubefile.yaml的位置来填写
        env:
          DOCKERHUB_USERNAME: ${{ secrets.DOCKERHUB_USERNAME }}
          DOCKERHUB_TOKEN: ${{ secrets.DOCKERHUB_TOKEN }}
          GHCR_TOKEN: ${{ secrets.GHCR_TOKEN }}
```
