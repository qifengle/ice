---
title: 迁移到 3.0 版本
order: 4
---

## 3.0 新特性

* CLI 使用链路：通过 CLI 方式启动本地 Web 工作台，开启全新研发体验；
* 产品结构升级：「项目管理」、「工程管理」、「物料市场」三大板块助力源码链路研发；
* 全新用户界面：多主题和多语言，满足开发者的个性化诉求；
* 可定制化工作台：任何前端项目，无论何种工程工具或项目规范，都可在 iceworks 中集成。

## 项目迁移方式

如果旧项目根目录不存在 `ice.config.js` 文件，则在 `package.json` 中增加如下配置:

```json
{
  "iceworks": {
    "adapter": "adapter-react-v0"
  }
}
```

如果旧项目根目录存在 `ice.config.js` 文件，且 `routerConfig.js` 中无路由分组 (所有路由平铺)，类似如下结构:

```javascript
const routerConfig = [
  {
    path: '/',
    component: 'pages/Dashboard/index.jsx',
    layout: 'layouts/BasicLayout',
    exact: true	
  }, {
    path: '/dashboard',
    component: 'pages/Dashboard/index.jsx',
    layout: 'layouts/BasicLayout',
  }, {
    component: 'components/NotFound/index.jsx',
    layout: 'layouts/BasicLayout',
  }
];
```

则在 `package.json` 中增加如下配置

```json
{
  "iceworks": {
    "adapter": "adapter-react-v1",
  }
}
```

如果项目根目录存在 `ice.config.js`文件，且 `routerConfig.js` 中有路由分组（路由有层级关系），类似如下结构

```javascript
const routerConfig = [
  {
    path: '/',
    component: BasicLayout,
    children: [
      {
        path: '/dashboard',
        component: Dashboard,
      },
      {
        path: '/',
        redirect: '/dashboard',
      },
      {
        component: NotFound,
      },
    ],
  },
];
```

则在`package.json`中增加如下配置

```json
{
  "iceworks": {
    "adapter": "adapter-react-v2"
  }
}
```

*注意：使用iceworks 3.0创建的新项目，adapter版本为`adapter-react-v3`*
