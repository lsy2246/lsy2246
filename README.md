![Dusai's GitHub stats](https://github-readme-stats.vercel.app/api?username=stacklens&show_icons=true&theme=radical)
# 访问 https://github.com/lowlighter/metrics#-documentation 获取完整的参考文档
name: 统计信息
on:
  # 定时更新（每小时一次）
  schedule: [{cron: "0 * * * *"}]
  # 下面的行允许你手动运行工作流和在每次提交时运行
  workflow_dispatch:
  push: {branches: ["master", "main"]}
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # 你的GitHub令牌
          # 需要以下权限：
          #  - public_access（默认权限）
          # 还可能需要以下附加权限：
          #  - read:org      （用于组织相关的统计数据）
          #  - read:user     （用于用户相关数据）
          #  - read:packages （用于某些包相关的数据）
          #  - repo          （可选，如果你想包括私有仓库）
          token: ${{ secrets.METRICS_TOKEN }}

          # 选项
          user: lsy2246
          template: classic
          base: header, activity, community, repositories, metadata
          config_timezone: Asia/Shanghai
          plugin_introduction: yes
          plugin_introduction_title: yes
