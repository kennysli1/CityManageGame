# CityManageGame 项目重构计划

参考 [anthropics/skills](https://github.com/anthropics/skills) 项目的模块化结构，重构项目目录。

## 目标结构

```
CityManagementGame/
├── .github/                      # GitHub 配置
│   └── workflows/                # CI/CD 工作流
├── config/                       # 构建和工具配置（根级别）
│   ├── vite.config.ts
│   ├── tsconfig.json
│   ├── tsconfig.node.json
│   ├── tailwind.config.js
│   ├── postcss.config.js
│   └── .eslintrc.cjs
├── docs/                         # 项目文档
│   ├── ARCHITECTURE.md          # 架构文档
│   ├── API.md                   # API 文档
│   └── REFACTOR_PLAN.md         # 重构计划（本文件）
├── public/                       # 静态资源
│   ├── assets/                  # 资源文件
│   │   ├── images/              # 图片
│   │   ├── audio/               # 音频
│   │   └── icons/               # 图标
│   └── favicon.ico
├── src/                          # 核心源代码
│   ├── main.tsx                 # 应用入口
│   ├── App.tsx                  # 根组件
│   ├── core/                    # 核心业务逻辑
│   │   ├── constants/          # 常量定义
│   │   │   ├── index.ts
│   │   │   ├── game.ts          # 游戏常量
│   │   │   ├── roles.ts         # 角色常量
│   │   │   └── metrics.ts       # 指标常量
│   │   ├── types/               # TypeScript 类型定义
│   │   │   ├── index.ts
│   │   │   ├── game.ts          # 游戏类型
│   │   │   ├── role.ts          # 角色类型
│   │   │   ├── policy.ts        # 政策类型
│   │   │   └── metric.ts        # 指标类型
│   │   ├── config/              # 应用配置（运行时配置）
│   │   │   ├── index.ts
│   │   │   ├── firebase.ts      # Firebase 配置
│   │   │   └── gameConfig.ts    # 游戏配置
│   │   └── managers/            # 管理器类（状态管理、业务逻辑）
│   │       ├── index.ts
│   │       ├── GameStateManager.ts
│   │       ├── RoleManager.ts
│   │       ├── PolicyManager.ts
│   │       └── MetricManager.ts
│   ├── services/                # 服务层（外部服务集成）
│   │   ├── index.ts
│   │   ├── firebase/            # Firebase 服务
│   │   │   ├── index.ts
│   │   │   ├── auth.ts          # 认证服务
│   │   │   └── firestore.ts     # Firestore 数据库服务
│   │   ├── game/                # 游戏服务
│   │   │   ├── index.ts
│   │   │   ├── gameState.ts     # 游戏状态服务
│   │   │   ├── roleService.ts   # 角色服务
│   │   │   ├── policyService.ts # 政策服务
│   │   │   ├── metricService.ts # 指标服务
│   │   │   └── turnService.ts   # 回合服务
│   │   └── satisfaction/        # 满意度计算服务
│   │       ├── index.ts
│   │       └── satisfactionCalculator.ts
│   ├── hooks/                   # React Hooks
│   │   ├── index.ts
│   │   ├── useAuth.ts           # 认证 Hook
│   │   ├── useGameState.ts      # 游戏状态 Hook
│   │   ├── useRoles.ts          # 角色管理 Hook
│   │   ├── usePolicies.ts       # 政策管理 Hook
│   │   └── useMetrics.ts        # 指标管理 Hook
│   ├── components/              # UI 组件
│   │   ├── index.ts             # 组件导出
│   │   ├── layout/              # 布局组件
│   │   │   ├── index.ts
│   │   │   ├── Header.tsx       # 页面头部
│   │   │   └── Container.tsx    # 布局容器
│   │   ├── game/                # 游戏相关组件
│   │   │   ├── index.ts
│   │   │   ├── GameStatus.tsx   # 游戏状态显示
│   │   │   ├── GameControls.tsx # 游戏控制按钮
│   │   │   └── ElectionResult.tsx # 竞选结果
│   │   ├── metrics/             # 指标相关组件
│   │   │   ├── index.ts
│   │   │   └── MetricsDisplay.tsx
│   │   ├── roles/               # 角色相关组件
│   │   │   ├── index.ts
│   │   │   ├── RoleList.tsx
│   │   │   └── RoleDisplay.tsx
│   │   ├── policies/            # 政策相关组件
│   │   │   ├── index.ts
│   │   │   ├── PolicyForm.tsx
│   │   │   ├── PolicyList.tsx
│   │   │   └── PolicyCard.tsx
│   │   └── ui/                  # 通用 UI 组件
│   │       ├── index.ts
│   │       ├── Modal.tsx
│   │       ├── Button.tsx
│   │       └── Card.tsx
│   ├── utils/                   # 工具函数
│   │   ├── index.ts
│   │   ├── formatters.ts        # 格式化工具
│   │   ├── validators.ts        # 验证工具
│   │   └── helpers.ts           # 辅助函数
│   └── styles/                  # 样式文件
│       ├── index.css            # 全局样式
│       └── variables.css        # CSS 变量
├── tests/                        # 测试文件
│   ├── unit/                    # 单元测试
│   ├── integration/             # 集成测试
│   └── e2e/                     # 端到端测试
├── scripts/                     # 脚本文件
│   └── setup.sh                 # 项目设置脚本
├── .gitignore
├── index.html                   # HTML 入口
├── package.json                 # 项目依赖
├── README.md                    # 项目说明
└── tsconfig.json                # TypeScript 配置（根级别，引用 config/）

```

## 文件迁移映射表

### 根目录配置文件 → config/
| 原路径 | 新路径 | 说明 |
|--------|--------|------|
| `vite.config.ts` | `config/vite.config.ts` | Vite 构建配置 |
| `tsconfig.json` | `config/tsconfig.json` | TypeScript 配置（主） |
| `tsconfig.node.json` | `config/tsconfig.node.json` | TypeScript 配置（Node） |
| `tailwind.config.js` | `config/tailwind.config.js` | Tailwind 配置 |
| `postcss.config.js` | `config/postcss.config.js` | PostCSS 配置 |
| `.eslintrc.cjs` | `config/.eslintrc.cjs` | ESLint 配置 |

### src/ 目录重组
| 原路径 | 新路径 | 说明 |
|--------|--------|------|
| `src/config/` | `src/core/config/` | 运行时配置（Firebase、游戏配置） |
| `src/types/` | `src/core/types/` | TypeScript 类型定义 |
| `src/services/` | `src/services/` | 保持不变，但添加 index.ts |
| `src/hooks/` | `src/hooks/` | 保持不变，但添加 index.ts |
| `src/components/` | `src/components/` | 保持不变，但添加各模块 index.ts |
| `src/utils/` | `src/utils/` | 保持不变，但添加 index.ts |
| `src/styles/` | `src/styles/` | 保持不变 |

### 新增目录
- `src/core/constants/` - 常量定义
- `src/core/managers/` - 管理器类
- `docs/` - 项目文档
- `tests/` - 测试文件
- `scripts/` - 脚本文件
- `public/assets/` - 资源文件分类

## 重构步骤

1. **创建新目录结构**
2. **移动配置文件到 config/**
3. **重组 src/core/ 目录**
4. **更新所有导入路径**
5. **更新配置文件引用**
6. **添加 index.ts 导出文件**
7. **更新文档**

## 优势

1. **清晰的职责分离**：配置、核心逻辑、服务、UI 分离
2. **更好的可维护性**：模块化组织，易于查找和修改
3. **符合工程化标准**：参考成熟项目的组织方式
4. **便于扩展**：新功能可以轻松添加到对应模块
5. **类型安全**：类型定义集中管理
