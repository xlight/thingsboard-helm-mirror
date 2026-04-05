# thingsboard-helm-mirror

用于镜像 [`thingsboard/thingsboard-ce-k8s`](https://github.com/thingsboard/thingsboard-ce-k8s) 中的 `helm/thingsboard` Helm Chart，并将其发布为可通过 `helm repo add` 使用的 Helm 仓库。

## 仓库目标

本仓库提供以下能力：

- 定时同步上游 `helm/thingsboard` Chart 源码
- 自动校验并打包 Chart
- 自动生成 Helm 仓库索引 `index.yaml`
- 通过 GitHub Pages 暴露为可消费的 Helm Repository

## Helm Repository 地址

启用 GitHub Pages 后，仓库地址应为：

- `https://xlight.github.io/thingsboard-helm-mirror`

## 使用方式

添加仓库：

- `helm repo add thingsboard-mirror https://xlight.github.io/thingsboard-helm-mirror`
- `helm repo update`

搜索 Chart：

- `helm search repo thingsboard-mirror`

安装 ThingsBoard：

- `helm install thingsboard thingsboard-mirror/thingsboard -n thingsboard --create-namespace`

查看 Values：

- `helm show values thingsboard-mirror/thingsboard`

## 仓库结构

- `charts/thingsboard/`：镜像后的 Chart 源码
- `docs/`：Helm 仓库发布目录，包含 `.tgz` 包和 `index.yaml`
- `.github/workflows/`：自动同步与发布工作流

## 发布说明

该仓库发布的是镜像版本，而非官方发布源。  
如果上游源码发生变化但未更新 `Chart.yaml` 中的 `version`，工作流会自动调整镜像版本，以避免同版本包内容漂移导致的 Helm 仓库缓存与索引问题。

## GitHub Pages 配置

需要在仓库设置中启用 GitHub Pages，并将发布目录指向默认分支下的 `docs/` 目录。

## 免责声明

本仓库仅做镜像与分发用途。  
ThingsBoard Helm Chart 的原始版权、实现与维护归属于上游项目：

- `https://github.com/thingsboard/thingsboard-ce-k8s`
