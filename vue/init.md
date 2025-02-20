# 未完待续
### 项目基本信息
-  nodejs 版本： 20.0
-  vue版本：3.5.13
-  yarn： 1.22.19
-  vite: 6.1.0

## 1. 初始化项目
```bash
# 使用 Yarn 创建 Vue 项目并使用 Vite 模板
yarn create vite 

# 进入项目目录
cd admin

# 安装依赖
yarn
# 启动
yarn dev
```
## 2. 安装所需的库 
vue Router 用于路由管理、Vuex 用于状态管理、Axios 用于 API 请求； 使用命令yarn add xxx
```bash
yarn add vue-router@4 vuex@4 axios
```
- numeral库: 用于格式化数字（如货币、百分比等）。
-  object-to-formdata库：用于将 JavaScript 对象转换为 FormData，可以用于发送表单数据。
-   js-cookie库：用于操作浏览器中的 Cookies（获取、设置和删除 cookies）
```bash
yarn add numeral object-to-formdata js-cookie
```

## 3. 配置 Vue Router
创建 router 文件夹并设置路由。定义基础路由
src/router/index.ts：
```typescript
import { createRouter, createWebHistory, RouteRecordRaw } from 'vue-router';
import Login from '../views/Login.vue';
import Dashboard from '../views/Dashboard.vue';
import Products from '../views/Products.vue';

// 定义路由记录
const routes: RouteRecordRaw[] = [
  {
    path: '/',
    name: 'Login',
    component: Login,
  },
  {
    path: '/dashboard',
    name: 'Dashboard',
    component: Dashboard,
  },
  {
    path: '/products',
    name: 'Products',
    component: Products,
  },
];

// 创建并导出路由实例
const router = createRouter({
  history: createWebHistory(import.meta.env.BASE_URL),
  routes,
});

export default router;
```
## 4. 配置 Vuex (状态管理)
创建 store 文件夹并添加商品或者用户登陆信息初始化
src/store/index.js：
```vue
import { createStore } from 'vuex'

export default createStore({
  state: {
    user: null,
    products: []
  },
  mutations: {
    setUser(state, user) {
      state.user = user
    },
    setProducts(state, products) {
      state.products = products
    },
  },
  actions: {
    fetchProducts({ commit }) {
      // 用 Axios 从后端获取商品列表
      axios.get('/api/products')
        .then(response => {
          commit('setProducts', response.data)
        })
    },
    login({ commit }, user) {
      // 用 Axios 进行登录请求
      axios.post('/api/login', user)
        .then(response => {
          commit('setUser', response.data)
        })
    }
  },
  getters: {
    isAuthenticated: state => !!state.user,
  },
})
```
## 5. 创建基础视图组件
使用Ant Design Vue 构建试图页面
```bash
yarn add ant-design-vue @ant-design/icons-vue
```

创建 views 文件夹并添加登陆等页面组件
- Login.vue：用于登录页面。
- Dashboard.vue：用于展示后台管理系统的仪表盘。
- Products.vue：用于商品的增删改查操作。

### Login.vue
src/views/Login.vue：




