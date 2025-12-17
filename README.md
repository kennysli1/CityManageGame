# 城市管理游戏

一个基于 React + TypeScript + Vite 的城市管理游戏项目。

## 技术栈

- **React 18** - UI 框架
- **TypeScript** - 类型安全
- **Vite** - 构建工具
- **Tailwind CSS** - 样式框架
- **Firebase** - 后端服务（认证和数据库）

## 项目结构

项目采用模块化、工程化的目录结构，参考 [anthropics/skills](https://github.com/anthropics/skills) 项目的组织方式。

```
CityManagementGame/
├── src/
│   ├── core/                   # 核心业务逻辑
│   │   ├── constants/          # 常量定义
│   │   ├── types/              # TypeScript 类型定义
│   │   ├── config/             # 应用配置
│   │   └── managers/           # 管理器类
│   ├── services/               # 服务层（Firebase、游戏服务）
│   ├── hooks/                  # React Hooks
│   ├── components/             # UI 组件（按功能模块组织）
│   ├── utils/                  # 工具函数
│   └── styles/                 # 样式文件
├── public/assets/              # 静态资源（图片、音频、图标）
├── docs/                       # 项目文档
├── tests/                      # 测试文件
└── config/                     # 工具配置文件
```

详细结构说明请查看 [docs/PROJECT_STRUCTURE.md](./docs/PROJECT_STRUCTURE.md)

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

## 下一步

按照计划文档，接下来将进行：
- 阶段2：类型定义和配置
- 阶段3：服务层拆分
- 阶段4：React Hooks封装
- 阶段5：UI组件拆分
- 阶段6：业务逻辑完善
