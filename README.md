# Use this action to deploy your service

## 使用前提

1. 在仓库的 **Settings → Secrets → Actions** 中添加以下 Secrets：
   - `DOCKERHUB_TOKEN`: 默认命名，含义： Docker Hub 的访问 Token
   - `GHCR_TOKEN`: 默认命名，含义：GitHub Container Registry 的访问 Token

2. 示例工作流文件：

```yaml
steps:
  - uses: your-username/vkube-deploy-action@v1
    with:
      vkube_config_file: './VKubefile.yaml' #这里根据自己的VKubefile.yaml的位置来填写
      
      dockerhub_token: 'MY_CUSTOM_DOCKER_TOKEN' # 如果自定义了 Secrets 名称，可覆盖默认值。在settings里设置了什么值这里就填什么值，下面的ghcr_token也是同理。
      ghcr_token: 'MY_CUSTOM_GHCR_TOKEN'

