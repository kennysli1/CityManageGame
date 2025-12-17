# 城市管理游戏

一个基于 React + TypeScript + Vite 的城市管理游戏项目。

## 技术栈

- **React 18** - UI 框架
- **TypeScript** - 类型安全
- **Vite** - 构建工具
- **Tailwind CSS** - 样式框架
- **Firebase** - 后端服务（认证和数据库）

## 项目结构

```
CityManagementGame/
├── package.json                 # 项目依赖配置
├── tsconfig.json               # TypeScript配置（引用 config/tsconfig.json）
├── index.html                  # 入口HTML
├── src/
│   ├── main.tsx                # 应用入口
│   ├── App.tsx                 # 根组件
│   ├── config/
│   │   ├── firebase.ts         # Firebase配置和初始化
│   │   ├── gameConfig.ts       # 游戏配置（指标、角色、回合等）
│   │   └── constants.ts        # 常量定义
│   ├── types/
│   │   ├── game.ts             # 游戏相关类型定义
│   │   ├── role.ts              # 角色类型定义
│   │   ├── policy.ts           # 政策类型定义
│   │   └── metric.ts           # 指标类型定义
│   ├── services/
│   │   ├── firebase/
│   │   │   ├── auth.ts         # 认证服务
│   │   │   └── firestore.ts    # Firestore数据库操作
│   │   ├── game/
│   │   │   ├── gameState.ts    # 游戏状态管理服务
│   │   │   ├── roleService.ts  # 角色分配和管理服务
│   │   │   ├── policyService.ts # 政策提案和审批服务
│   │   │   ├── metricService.ts # 指标计算和管理服务
│   │   │   └── turnService.ts  # 回合结算服务
│   │   └── satisfaction/
│   │       └── satisfactionCalculator.ts # 满意度计算逻辑
│   ├── hooks/
│   │   ├── useAuth.ts          # 认证状态Hook
│   │   ├── useGameState.ts     # 游戏状态Hook
│   │   ├── useRoles.ts         # 角色管理Hook
│   │   ├── usePolicies.ts      # 政策管理Hook
│   │   └── useMetrics.ts       # 指标管理Hook
│   ├── components/
│   │   ├── layout/
│   │   │   ├── Header.tsx      # 页面头部（连接状态、用户ID）
│   │   │   └── Container.tsx   # 布局容器
│   │   ├── game/
│   │   │   ├── GameStatus.tsx  # 游戏状态显示（回合数、竞选回合）
│   │   │   ├── GameControls.tsx # 游戏控制按钮（开始、下一回合）
│   │   │   └── ElectionResult.tsx # 竞选结果展示
│   │   ├── metrics/
│   │   │   └── MetricsDisplay.tsx # 城市指标展示组件
│   │   ├── roles/
│   │   │   ├── RoleList.tsx    # 角色列表展示
│   │   │   └── RoleDisplay.tsx # 当前角色显示
│   │   ├── policies/
│   │   │   ├── PolicyForm.tsx  # 政策提案表单
│   │   │   ├── PolicyList.tsx  # 待审批政策列表
│   │   │   └── PolicyCard.tsx  # 政策卡片组件
│   │   └── ui/
│   │       ├── Modal.tsx       # 通用模态框组件
│   │       └── Button.tsx      # 通用按钮组件
│   ├── utils/
│   │   ├── formatters.ts       # 格式化工具函数
│   │   └── validators.ts       # 验证工具函数
│   └── styles/
│       └── index.css           # 全局样式
├── config/                     # 工具配置文件
│   ├── vite.config.ts         # Vite构建配置
│   ├── tsconfig.json          # TypeScript配置
│   ├── tsconfig.node.json     # TypeScript Node配置
│   ├── tailwind.config.js     # Tailwind CSS配置
│   ├── postcss.config.js      # PostCSS配置
│   └── .eslintrc.cjs          # ESLint配置
├── public/                     # 静态资源
│   └── assets/                 # 资源文件分类
│       ├── images/            # 图片资源
│       ├── audio/              # 音频资源
│       └── icons/              # 图标资源
└── docs/                       # 项目文档
    └── (文档文件)
```

## 安装依赖

```bash
npm install
```

## 开发模式

```bash
npm run dev
```

项目将在 `http://localhost:5173` 启动。

## 构建生产版本

```bash
npm run build
```

## 预览生产版本

```bash
npm run preview
```

## 拆分步骤

### 阶段1：项目基础设置 ✅

1. ✅ 初始化React + TypeScript + Vite项目
2. ✅ 配置Tailwind CSS
3. ✅ 安装Firebase SDK依赖
4. ✅ 设置基础项目结构

### 阶段2：类型定义和配置

1. 创建类型定义文件（game.ts, role.ts, policy.ts, metric.ts）
2. 提取游戏配置到config/gameConfig.ts
3. 创建Firebase配置文件

### 阶段3：服务层拆分

1. **Firebase服务**：
   - `auth.ts`: 处理认证逻辑
   - `firestore.ts`: 封装Firestore操作（游戏状态、政策集合）

2. **游戏服务**：
   - `gameState.ts`: 游戏状态CRUD操作
   - `roleService.ts`: 角色分配、角色验证
   - `policyService.ts`: 政策提案、审批、执行
   - `metricService.ts`: 指标计算、更新
   - `turnService.ts`: 回合结算逻辑

3. **满意度服务**：
   - `satisfactionCalculator.ts`: 根据各指标计算满意度

### 阶段4：React Hooks封装

1. `useAuth`: 封装认证状态和操作
2. `useGameState`: 封装游戏状态监听和更新
3. `useRoles`: 封装角色相关操作
4. `usePolicies`: 封装政策相关操作
5. `useMetrics`: 封装指标相关操作

### 阶段5：UI组件拆分

1. **布局组件**：Header, Container
2. **游戏组件**：GameStatus, GameControls, ElectionResult
3. **指标组件**：MetricsDisplay（展示所有城市指标）
4. **角色组件**：RoleList, RoleDisplay
5. **政策组件**：PolicyForm, PolicyList, PolicyCard
6. **UI组件**：Modal, Button等通用组件

### 阶段6：业务逻辑完善

1. 实现满意度计算公式（参考AGENTS.md中各角色的满意度权重）
2. 实现回合结算的完整逻辑
3. 实现角色权限验证
4. 实现政策效果计算

## 关键文件说明

### config/gameConfig.ts

包含：
- `METRIC_CONFIG`: 指标配置（名称、颜色、变化范围、影响权重）
- `ROLES_MAP`: 角色映射
- `ELECTION_TURN`: 竞选回合数
- `INITIAL_METRICS`: 初始指标值
- `POLICY_COST_RANGE`: 政策预算范围

### types/game.ts

定义核心类型：

```typescript
interface GameState {
  metrics: Metrics;
  roles: Record<string, Role>;
  currentTurn: number;
  electionTurn: number;
  lastReset: number;
}
```

### services/game/turnService.ts

包含回合结算的核心逻辑：
- 执行已批准政策
- 计算指标变化
- 计算满意度变化
- 计算财政收入
- 更新游戏状态

### services/satisfaction/satisfactionCalculator.ts

实现满意度计算，根据AGENTS.md中各角色的满意度权重计算总满意度

## 后续扩展点

1. **角色系统扩展**：根据AGENTS.md添加更多角色（教育、卫生、环保等）
2. **政策系统扩展**：支持更复杂的政策效果和相互影响
3. **指标系统扩展**：添加更多城市指标（房价、就业率等）
4. **交流系统**：添加玩家间的实时聊天功能
5. **历史记录**：记录政策执行历史和指标变化历史
6. **数据可视化**：添加图表展示指标趋势

## 注意事项

1. 保持Firebase配置的安全性（使用环境变量）
2. 确保实时数据同步的正确性
3. 处理并发更新冲突
4. 优化性能（避免不必要的重渲染）
5. 添加错误处理和加载状态
6. 保持代码的可测试性

## 详细文档

- [项目结构说明](./docs/PROJECT_STRUCTURE.md)
- [文件迁移记录](./docs/FILE_MIGRATION.md)
- [重构计划](./REFACTOR_PLAN.md)
