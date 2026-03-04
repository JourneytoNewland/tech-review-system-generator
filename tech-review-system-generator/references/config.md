# 配置指南

## 内容粒度配置

```javascript
const CONTENT_GRADE = {
  concise: { minItems: 5, maxItems: 8 },      // 精简版：5-8 项/模块
  standard: { minItems: 10, maxItems: 15 },    // 标准版：10-15 项/模块
  detailed: { minItems: 20, maxItems: 30 }     // 详细版：20-30 项/模块
};
```

## 界面风格配置

### modern（现代专业）- 默认
- 圆角设计（rounded-lg）
- 柔和阴影（shadow-sm）
- 丰富动画（fade-in, slide-in）
- 渐变色强调

### clean（简洁清爽）
- 扁平化设计
- 极简阴影
- 轻量动画
- 纯色强调

### technical（技术风格）
- 代码风格边框
- 单色系配色
- 终端风格字体
- 矩形硬朗

## 系统配色方案

6 个模块使用不同颜色，确保视觉区分：

```javascript
const MODULE_COLORS = [
  '#1976D2',  // 蓝色 - 架构/基础
  '#2E7D32',  // 绿色 - 数据/存储
  '#ED6C02',  // 橙色 - 专项/特性
  '#9C27B0',  // 紫色 - 交互/流程
  '#F57C00',  // 深橙 - 性能/优化
  '#D32F2F'   // 红色 - 运维/监控
];
```

## 图标映射

| 模块类型 | FontAwesome 图标 |
|----------|------------------|
| 架构设计 | fa-sitemap |
| 数据建模 | fa-database |
| 流程设计 | fa-cogs |
| 性能优化 | fa-bolt |
| 运维监控 | fa-chart-line |
| 交互流程 | fa-comments |

## 输出配置

| 配置项 | 说明 |
|--------|------|
| 输出路径 | 默认：`./index.html` |
| 文件编码 | UTF-8 |
| HTML 压缩 | 可选（默认不压缩） |
| CDN 版本 | React 18, Chart.js 4.4.0, Tailwind 最新 |
| 备用字体 | Segoe UI, Roboto, Helvetica Neue |

## 高级配置

### 模块数量范围
- 最小：3 个模块
- 推荐：4-8 个模块
- 最大：12 个模块

### 检查项数量范围
- 最小：3 项/评审项
- 推荐：4-6 项/评审项
- 最大：10 项/评审项

### 图表配置

```javascript
const CHART_CONFIG = {
  overallProgress: {
    type: 'doughnut',
    cutout: '70%',
    colors: ['#2E7D32', '#E0E0E0', '#D32F2F']
  },
  issueDistribution: {
    type: 'pie',
    colors: ['#D32F2F', '#ED6C02', '#1976D2']
  },
  moduleProgress: {
    type: 'bar',
    maxHeight: 250
  }
};
```
