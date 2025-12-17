# 项目结构说明

参考 [anthropics/skills](https://github.com/anthropics/skills) 项目的模块化组织方式。

## 目录树结构

```
CityManagementGame/
├── .github/                      # GitHub 配置
│   └── workflows/                # CI/CD 工作流（待添加）
├── config/                       # 工具配置文件（可选）
│   └── (保留用于未来扩展配置)
├── docs/                         # 项目文档
│   ├── ARCHITECTURE.md          # 架构文档（待添加）
│   ├── API.md                   # API 文档（待添加）
│   ├── PROJECT_STRUCTURE.md     # 本文件
│   └── REFACTOR_PLAN.md         # 重构计划
├── public/                       # 静态资源
│   ├── assets/                  # 资源文件
│   │   ├── images/              # 图片资源
│   │   ├── audio/               # 音频资源
│   │   └── icons/                # 图标资源
│   └── favicon.ico              # 网站图标（待添加）
├── scripts/                      # 脚本文件
│   └── setup.sh                 # 项目设置脚本（待添加）
├── src/                          # 核心源代码
│   ├── main.tsx                 # 应用入口
│   ├── App.tsx                  # 根组件
│   ├── core/                    # 核心业务逻辑
│   │   ├── constants/           # 常量定义
│   │   │   ├── index.ts        # 导出入口
│   │   │   ├── game.ts         # 游戏常量（待实现）
│   │   │   ├── roles.ts        # 角色常量（待实现）
│   │   │   └── metrics.ts      # 指标常量（待实现）
│   │   ├── types/               # TypeScript 类型定义
│   │   │   ├── index.ts        # 导出入口
│   │   │   ├── game.ts         # 游戏类型（待实现）
│   │   │   ├── role.ts         # 角色类型（待实现）
│   │   │   ├── policy.ts       # 政策类型（待实现）
│   │   │   └── metric.ts       # 指标类型（待实现）
│   │   ├── config/              # 应用配置（运行时配置）
│   │   │   ├── index.ts        # 导出入口
│   │   │   ├── firebase.ts     # Firebase 配置（待实现）
│   │   │   └── gameConfig.ts   # 游戏配置（待实现）
│   │   └── managers/            # 管理器类（状态管理、业务逻辑）
│   │       ├── index.ts        # 导出入口
│   │       ├── GameStateManager.ts    # 游戏状态管理器（待实现）
│   │       ├── RoleManager.ts         # 角色管理器（待实现）
│   │       ├── PolicyManager.ts       # 政策管理器（待实现）
│   │       └── MetricManager.ts       # 指标管理器（待实现）
│   ├── services/                # 服务层（外部服务集成）
│   │   ├── index.ts            # 导出入口
│   │   ├── firebase/           # Firebase 服务
│   │   │   ├── index.ts        # 导出入口
│   │   │   ├── auth.ts         # 认证服务（待实现）
│   │   │   └── firestore.ts    # Firestore 数据库服务（待实现）
│   │   ├── game/               # 游戏服务
│   │   │   ├── index.ts        # 导出入口
│   │   │   ├── gameState.ts    # 游戏状态服务（待实现）
│   │   │   ├── roleService.ts  # 角色服务（待实现）
│   │   │   ├── policyService.ts # 政策服务（待实现）
│   │   │   ├── metricService.ts # 指标服务（待实现）
│   │   │   └── turnService.ts  # 回合服务（待实现）
│   │   └── satisfaction/       # 满意度计算服务
│   │       ├── index.ts        # 导出入口
│   │       └── satisfactionCalculator.ts # 满意度计算（待实现）
│   ├── hooks/                   # React Hooks
│   │   ├── index.ts            # 导出入口
│   │   ├── useAuth.ts          # 认证 Hook（待实现）
│   │   ├── useGameState.ts     # 游戏状态 Hook（待实现）
│   │   ├── useRoles.ts         # 角色管理 Hook（待实现）
│   │   ├── usePolicies.ts      # 政策管理 Hook（待实现）
│   │   └── useMetrics.ts       # 指标管理 Hook（待实现）
│   ├── components/             # UI 组件
│   │   ├── index.ts            # 导出入口
│   │   ├── layout/             # 布局组件
│   │   │   ├── index.ts        # 导出入口
│   │   │   ├── Header.tsx     # 页面头部（待实现）
│   │   │   └── Container.tsx   # 布局容器（待实现）
│   │   ├── game/               # 游戏相关组件
│   │   │   ├── index.ts        # 导出入口
│   │   │   ├── GameStatus.tsx  # 游戏状态显示（待实现）
│   │   │   ├── GameControls.tsx # 游戏控制按钮（待实现）
│   │   │   └── ElectionResult.tsx # 竞选结果（待实现）
│   │   ├── metrics/            # 指标相关组件
│   │   │   ├── index.ts        # 导出入口
│   │   │   └── MetricsDisplay.tsx # 指标展示（待实现）
│   │   ├── roles/              # 角色相关组件
│   │   │   ├── index.ts        # 导出入口
│   │   │   ├── RoleList.tsx    # 角色列表（待实现）
│   │   │   └── RoleDisplay.tsx # 角色显示（待实现）
│   │   ├── policies/           # 政策相关组件
│   │   │   ├── index.ts        # 导出入口
│   │   │   ├── PolicyForm.tsx # 政策表单（待实现）
│   │   │   ├── PolicyList.tsx # 政策列表（待实现）
│   │   │   └── PolicyCard.tsx # 政策卡片（待实现）
│   │   └── ui/                 # 通用 UI 组件
│   │       ├── index.ts        # 导出入口
│   │       ├── Modal.tsx      # 模态框（待实现）
│   │       ├── Button.tsx      # 按钮（待实现）
│   │       └── Card.tsx        # 卡片（待实现）
│   ├── utils/                  # 工具函数
│   │   ├── index.ts            # 导出入口
│   │   ├── formatters.ts       # 格式化工具（待实现）
│   │   ├── validators.ts       # 验证工具（待实现）
│   │   └── helpers.ts          # 辅助函数（待实现）
│   └── styles/                 # 样式文件
│       ├── index.css           # 全局样式
│       └── variables.css       # CSS 变量（待添加）
├── tests/                       # 测试文件
│   ├── unit/                   # 单元测试（待添加）
│   ├── integration/            # 集成测试（待添加）
│   └── e2e/                    # 端到端测试（待添加）
├── .eslintrc.cjs               # ESLint 配置
├── .gitignore                   # Git 忽略文件
├── index.html                   # HTML 入口
├── package.json                 # 项目依赖
├── postcss.config.js            # PostCSS 配置
├── README.md                    # 项目说明
├── tailwind.config.js           # Tailwind CSS 配置
├── tsconfig.json                # TypeScript 配置（主）
├── tsconfig.node.json           # TypeScript 配置（Node）
└── vite.config.ts               # Vite 构建配置
```

## 目录说明

### `/src/core/` - 核心业务逻辑
包含游戏的核心业务逻辑，不依赖外部框架（React 除外）。

- **constants/**: 常量定义，如游戏配置、角色映射、指标配置等
- **types/**: TypeScript 类型定义，确保类型安全
- **config/**: 运行时配置，如 Firebase 配置、游戏参数等
- **managers/**: 管理器类，负责状态管理和业务逻辑协调

### `/src/services/` - 服务层
负责与外部服务（Firebase）的集成和数据操作。

- **firebase/**: Firebase 相关服务（认证、数据库）
- **game/**: 游戏相关的数据服务
- **satisfaction/**: 满意度计算服务

### `/src/hooks/` - React Hooks
封装业务逻辑的 React Hooks，供组件使用。

### `/src/components/` - UI 组件
React 组件，按功能模块组织。

- **layout/**: 布局组件
- **game/**: 游戏相关组件
- **metrics/**: 指标展示组件
- **roles/**: 角色相关组件
- **policies/**: 政策相关组件
- **ui/**: 通用 UI 组件

### `/src/utils/` - 工具函数
纯函数工具，不依赖业务逻辑。

### `/public/assets/` - 静态资源
按类型分类的资源文件。

### `/docs/` - 项目文档
项目相关文档。

### `/tests/` - 测试文件
按测试类型分类。

## 路径别名配置

在 `tsconfig.json` 和 `vite.config.ts` 中配置了以下路径别名：

- `@/*` → `./src/*`
- `@core/*` → `./src/core/*`
- `@components/*` → `./src/components/*`
- `@services/*` → `./src/services/*`
- `@hooks/*` → `./src/hooks/*`
- `@utils/*` → `./src/utils/*`

使用示例：
```typescript
import { GameState } from '@core/types'
import { useAuth } from '@hooks/useAuth'
import { Header } from '@components/layout'
```

## 设计原则

1. **职责分离**: 每个目录有明确的职责
2. **模块化**: 功能模块独立，便于维护和测试
3. **可扩展性**: 新功能可以轻松添加到对应模块
4. **类型安全**: 类型定义集中管理
5. **统一导出**: 每个模块都有 index.ts 统一导出
