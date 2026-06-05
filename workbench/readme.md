# 微信工作台搭建计划

> 会话时间：2026-06-04
> 状态：计划阶段，待实施

## 需求

将 `https://13yan.github.io/weekly-reports/` 的周报内容做成**微信工作台**，用于查看每周重点市场资讯和核心关注内容。

## 核心设计

- 在 `weekly-repos/workbench/` 下创建 SPA
- 修改 `gen_report_v3.js` 输出 JSON 数据
- 修改发布脚本维护 manifest 索引
- 响应式设计，适配桌面端和手机端
- 页脚：`数据来源：引力引擎（数据截止时间XXXX年XX月XX日）`

## 关键修改文件

| 文件 | 操作 |
|------|------|
| `C:\temp\gen_report_v3.js` | 添加 JSON 数据输出 |
| `C:\Users\Administrator\weekly-reports\workbench\index.html` | 新建 SPA |
| `C:\Users\Administrator\.claude\scripts\publish-weekly-report.sh` | 添加 data.json 复制 + manifest 维护 |

## 数据流

```
gen_report_v3.js → report-data.json → publish → GitHub Pages → workbench/
```

## 视图结构

- **Master 主视图**：报告卡片时间线（最新在前），显示 highlight + 关键指标
- **Detail 详情视图**：指标条 + 标签栏（摘要/畅销榜/模拟经营/飙升/政策/趋势）+ 内容面板

## 实施顺序

1. 修改 `gen_report_v3.js` — 提取政策变量 + JSON 输出
2. 测试 JSON 输出
3. 创建 `workbench/index.html` — 完整 SPA
4. 修改发布脚本
5. 本地测试 → 部署验证
