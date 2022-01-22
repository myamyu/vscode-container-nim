# vscode-container-nim

VSCodeのRemote Container開発用のテンプレート（nim）

## DBなどを立ち上げる場合

[vscode.docker-compose.yaml](./vscode.docker-compose.yaml) を編集する。

例: selenium-hubを追加する場合、servicesに以下を追加する

```yaml
  selenium-hub:
    image: selenium/hub:3.141.59-20210830
    container_name: selenium-hub
    ports:
    - 4444:4444
    environment:
    - GRID_MAX_SESSION=10

  chrome:
    image: selenium/node-chrome:3.141.59-20210830
    container_name: selenium-chrome
    shm_size: 2gb
    depends_on:
    - selenium-hub
    environment:
    - HUB_HOST=selenium-hub
    - HUB_PORT=4444
    - NODE_MAX_SESSION=5
```
