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
├── tsconfig.json               # TypeScript配置
├── vite.config.ts              # Vite构建配置
├── tailwind.config.js          # Tailwind CSS配置
├── index.html                  # 入口HTML
├── src/
│   ├── main.tsx                # 应用入口
│   ├── App.tsx                 # 根组件
│   ├── config/                 # 配置文件
│   ├── types/                  # 类型定义
│   ├── services/               # 服务层
│   ├── hooks/                  # React Hooks
│   ├── components/             # UI组件
│   ├── utils/                  # 工具函数
│   └── styles/                 # 样式文件
└── public/                     # 静态资源
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

## 下一步

按照计划文档，接下来将进行：
- 阶段2：类型定义和配置
- 阶段3：服务层拆分
- 阶段4：React Hooks封装
- 阶段5：UI组件拆分
- 阶段6：业务逻辑完善
