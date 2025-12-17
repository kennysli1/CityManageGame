# 文件迁移映射表

本文档记录了重构过程中的文件迁移情况。

## 已完成迁移

### 配置文件（保留在根目录）
这些是构建工具的标准配置文件，保留在根目录符合约定：

| 文件 | 位置 | 说明 |
|------|------|------|
| `vite.config.ts` | 根目录 | Vite 构建配置 |
| `tsconfig.json` | 根目录 | TypeScript 配置（主） |
| `tsconfig.node.json` | 根目录 | TypeScript 配置（Node） |
| `tailwind.config.js` | 根目录 | Tailwind CSS 配置 |
| `postcss.config.js` | 根目录 | PostCSS 配置 |
| `.eslintrc.cjs` | 根目录 | ESLint 配置 |

### src/ 目录重组

| 原路径 | 新路径 | 状态 |
|--------|--------|------|
| `src/config/` | `src/core/config/` | ✅ 已迁移 |
| `src/types/` | `src/core/types/` | ✅ 已迁移 |
| - | `src/core/constants/` | ✅ 已创建 |
| - | `src/core/managers/` | ✅ 已创建 |

### 新增目录结构

| 目录 | 说明 | 状态 |
|------|------|------|
| `docs/` | 项目文档 | ✅ 已创建 |
| `tests/unit/` | 单元测试 | ✅ 已创建 |
| `tests/integration/` | 集成测试 | ✅ 已创建 |
| `tests/e2e/` | 端到端测试 | ✅ 已创建 |
| `scripts/` | 脚本文件 | ✅ 已创建 |
| `public/assets/images/` | 图片资源 | ✅ 已创建 |
| `public/assets/audio/` | 音频资源 | ✅ 已创建 |
| `public/assets/icons/` | 图标资源 | ✅ 已创建 |

## 待实现文件

以下文件结构已创建，但具体实现待后续开发：

### 核心模块 (`src/core/`)
- [ ] `constants/game.ts` - 游戏常量
- [ ] `constants/roles.ts` - 角色常量
- [ ] `constants/metrics.ts` - 指标常量
- [ ] `types/game.ts` - 游戏类型
- [ ] `types/role.ts` - 角色类型
- [ ] `types/policy.ts` - 政策类型
- [ ] `types/metric.ts` - 指标类型
- [ ] `config/firebase.ts` - Firebase 配置
- [ ] `config/gameConfig.ts` - 游戏配置
- [ ] `managers/GameStateManager.ts` - 游戏状态管理器
- [ ] `managers/RoleManager.ts` - 角色管理器
- [ ] `managers/PolicyManager.ts` - 政策管理器
- [ ] `managers/MetricManager.ts` - 指标管理器

### 服务层 (`src/services/`)
- [ ] `firebase/auth.ts` - 认证服务
- [ ] `firebase/firestore.ts` - Firestore 服务
- [ ] `game/gameState.ts` - 游戏状态服务
- [ ] `game/roleService.ts` - 角色服务
- [ ] `game/policyService.ts` - 政策服务
- [ ] `game/metricService.ts` - 指标服务
- [ ] `game/turnService.ts` - 回合服务
- [ ] `satisfaction/satisfactionCalculator.ts` - 满意度计算

### Hooks (`src/hooks/`)
- [ ] `useAuth.ts` - 认证 Hook
- [ ] `useGameState.ts` - 游戏状态 Hook
- [ ] `useRoles.ts` - 角色管理 Hook
- [ ] `usePolicies.ts` - 政策管理 Hook
- [ ] `useMetrics.ts` - 指标管理 Hook

### 组件 (`src/components/`)
- [ ] `layout/Header.tsx` - 页面头部
- [ ] `layout/Container.tsx` - 布局容器
- [ ] `game/GameStatus.tsx` - 游戏状态显示
- [ ] `game/GameControls.tsx` - 游戏控制按钮
- [ ] `game/ElectionResult.tsx` - 竞选结果
- [ ] `metrics/MetricsDisplay.tsx` - 指标展示
- [ ] `roles/RoleList.tsx` - 角色列表
- [ ] `roles/RoleDisplay.tsx` - 角色显示
- [ ] `policies/PolicyForm.tsx` - 政策表单
- [ ] `policies/PolicyList.tsx` - 政策列表
- [ ] `policies/PolicyCard.tsx` - 政策卡片
- [ ] `ui/Modal.tsx` - 模态框
- [ ] `ui/Button.tsx` - 按钮
- [ ] `ui/Card.tsx` - 卡片

### 工具函数 (`src/utils/`)
- [ ] `formatters.ts` - 格式化工具
- [ ] `validators.ts` - 验证工具
- [ ] `helpers.ts` - 辅助函数

## 路径别名

已在 `tsconfig.json` 和 `vite.config.ts` 中配置路径别名：

- `@/*` → `./src/*`
- `@core/*` → `./src/core/*`
- `@components/*` → `./src/components/*`
- `@services/*` → `./src/services/*`
- `@hooks/*` → `./src/hooks/*`
- `@utils/*` → `./src/utils/*`

## 导出文件

所有模块都已创建 `index.ts` 导出文件，便于统一导入：

```typescript
// 示例：使用路径别名导入
import { GameState } from '@core/types'
import { useAuth } from '@hooks/useAuth'
import { Header } from '@components/layout'
```
