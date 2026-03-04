# 模块映射规则

技术方案文档章节到评审模块的映射规则。

## 映射规则

### 架构设计类

**关键词**：`architecture, design, schema, structure, 架构, 设计, 结构`

```javascript
{
  name: '架构设计',
  icon: 'fa-sitemap',
  color: '#1976D2',
  checklist: [
    '设计完整性：核心组件/模块定义完整',
    '设计合理性：技术选型有充分依据',
    '扩展性：支持未来功能扩展',
    '一致性：与其他模块协调一致'
  ]
}
```

### 数据建模类

**关键词**：`data, model, entity, database, 数据, 模型, 实体, 数据库`

```javascript
{
  name: '数据建模',
  icon: 'fa-database',
  color: '#2E7D32',
  checklist: [
    '模型定义：节点/表结构定义完整',
    '关系设计：关联关系定义准确',
    '索引优化：索引配置合理',
    '查询性能：查询路径优化'
  ]
}
```

### 流程设计类

**关键词**：`process, workflow, pipeline, ingestion, flow, 流程, 工作流, 管道, 入库`

```javascript
{
  name: '流程设计',
  icon: 'fa-cogs',
  color: '#ED6C02',
  checklist: [
    '步骤完整性：流程步骤无遗漏',
    '异常处理：异常场景有处理方案',
    '性能指标：有明确的性能目标',
    '可监控性：关键节点可监控'
  ]
}
```

### 性能优化类

**关键词**：`performance, optimization, cache, 性能, 优化, 缓存`

```javascript
{
  name: '性能优化',
  icon: 'fa-bolt',
  color: '#F57C00',
  checklist: [
    '响应时间：满足性能要求（<X ms）',
    '吞吐量：支持并发要求',
    '资源使用：CPU/内存使用合理',
    '缓存策略：缓存配置有效'
  ]
}
```

### 运维监控类

**关键词**：`monitoring, ops, operation, deploy, 运维, 监控, 部署`

```javascript
{
  name: '运维监控',
  icon: 'fa-chart-line',
  color: '#D32F2F',
  checklist: [
    '监控指标：关键指标有监控',
    '告警规则：告警阈值配置合理',
    '故障检测：异常自动检测',
    '恢复机制：故障自动恢复'
  ]
}
```

### 交互流程类

**关键词**：`interaction, ui, ux, user, 交互, 界面, 用户体验`

```javascript
{
  name: '交互流程',
  icon: 'fa-comments',
  color: '#9C27B0',
  checklist: [
    '交互完整性：交互流程无遗漏',
    '用户体验：操作流畅自然',
    '反馈及时：操作反馈及时',
    '错误处理：错误提示清晰'
  ]
}
```

## 映射优先级

当章节匹配多个类别时，按以下优先级选择：

1. **架构设计** > 数据建模 > 流程设计
2. **性能优化** > 其他（单独考虑）
3. **运维监控** > 其他（单独考虑）
4. **交互流程** > 其他（如果有用户界面相关）

## 自定义映射

如果默认映射不适用，可以根据文档特点自定义：

```javascript
// 示例：微服务架构文档
const CUSTOM_MAPPING = {
  '服务拆分': '架构设计',
  'API网关': '架构设计',
  '服务发现': '架构设计',
  '配置管理': '架构设计',
  '数据库设计': '数据建模',
  '缓存策略': '性能优化',
  '部署流程': '流程设计',
  '日志监控': '运维监控'
};
```
