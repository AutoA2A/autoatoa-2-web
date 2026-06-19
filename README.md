# 基于Web的中国古诗词浏览与解析系统

## 项目概述  
本项目是 **基于 Web 的中国古诗词浏览与解析系统**，旨在提供 80 首必备古诗词（当前 1‑20 首）的完整展示与深度解读。每首诗配有原文、注释、赏析、创作背景以及相关图片，支持关键词搜索，并可按 **朝代、作者、主题** 三大维度筛选，帮助用户快速定位并感受诗歌背后的情感与文化内涵。

## 各页面说明  

| 页面 | 功能 | 关键实现 |
|------|------|----------|
| 首页 | 轮播推荐、搜索框、筛选入口 | Vue + Element UI，调用后端 `/poems` 接口 |
| 诗词列表 | 按筛选条件分页展示诗词标题 | 表格组件 + 动态路由 |
| 诗词详情 | 原文、注释、赏析、背景、配图 | Markdown 渲染 + 图片懒加载 |
| 作者页 | 作者简介、作品列表 | 关联查询 `/authors/:id` |
| 朝代页 | 朝代概览、代表作品 | 结构化数据展示 |
| 主题页 | 主题分类、对应诗词 | 标签云交互 |
| 搜索结果 | 高亮显示匹配关键词 | 前端全文检索（ElasticSearch） |
| 关于/帮助 | 项目说明、使用指南 | 静态 Markdown 页面 |

已完成上述 **8 个页面**，实现基本交互与响应式布局。

## 协作过程  
1. **需求讨论**：每周一次线上会议，确定诗词范围、功能点与 UI 风格。  
2. **任务拆分**：在 GitHub Projects 中创建 Issue，分别指派前端、后端、数据维护三类任务。  
3. **代码审查**：Pull Request 必须通过两名成员审查，确保代码风格统一、单元测试覆盖率 ≥ 80%。  
4. **持续集成**：GitHub Actions 自动执行 lint、单元测试与 Docker 镜像构建。  
5. **文档同步**：README 与 Wiki 同步更新，记录接口文档、部署步骤与常见问题。  

## 如何在 GitHub 部署与运行  

1. **克隆仓库**  
   ```bash
   git clone https://github.com/yourorg/poem-browser.git
   cd poem-browser
   ```

2. **环境配置**  
   - 创建 `.env`（参考 `.env.example`）  
   - 设置数据库连接 `POSTGRES_URL`、搜索服务 `ES_URL` 等。  

3. **启动后端**（Docker Compose）  
   ```bash
   docker compose up -d backend db elasticsearch
   ```

4. **启动前端**  
   ```bash
   cd frontend
   npm install
   npm run serve   # 本地开发
   # 或者
   npm run build && npx serve -s dist   # 生产模式
   ```

5. **部署到服务器**（可选）  
   - 将 `docker-compose.yml` 推送至服务器，执行 `docker compose up -d`。  
   - 使用 Nginx 反向代理 `frontend` 与 `backend`，开启 HTTPS。  

6. **验证**  
   访问 `http://<your-domain>/`，检查首页、搜索、筛选等功能是否正常。  

> **备注**：项目采用 MIT 开源许可证，欢迎 Fork、Issue 与 Pull Request 共同完善古诗词资源库。

---
> 本项目由 AutoAtoA「AI 研究院」多个 AI 协作生成（共 8 个页面）。在线运行： https://AutoA2A.github.io/autoatoa-2-web/
