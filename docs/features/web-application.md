---
layout: doc
title: Web应用
description: 尝试解决前后端在实际中的应用
---

# Web 应用

## 概述

Web 应用是现代互联网应用的主流形式。我们致力于帮助开发者理解和掌握前后端在实际生产环境中的最佳实践。

## 核心方向

### 前端开发

- **现代框架**：掌握 Vue、React、Angular 等主流框架
- **性能优化**：深入理解代码分割、懒加载、缓存策略
- **用户体验**：构建高效、响应式的用户界面
- **跨浏览器兼容**：确保应用在各种浏览器中的稳定性

### 后端开发

- **API 设计**：学习 RESTful、GraphQL 等现代 API 设计模式
- **数据库优化**：掌握数据库设计、查询优化、事务处理
- **服务器架构**：理解微服务、分布式系统设计
- **安全防护**：实现认证、授权、加密等安全机制

### 全栈整合

- **前后端协作**：学习如何高效地进行前后端集成
- **DevOps 实践**：掌握 CI/CD、容器化部署
- **监控和日志**：建立完整的应用监控体系
- **性能调优**：从整体角度提升应用性能

## 前端基础技术深入详解

### HTML5 完全指南

HTML（HyperText Markup Language）是网页的结构骨架。HTML5 是最新的标准，引入了许多新的语义化标签和 API，使网页开发更加高效和标准化。

#### HTML5 基础结构

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <!-- 字符编码：声明页面的字符集为 UTF-8 -->
  <meta charset="UTF-8">
  <!-- 视口配置：使页面在移动设备上正确显示 -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <!-- 页面标题：显示在浏览器标签页中 -->
  <title>我的网站 - 欢迎来到首页</title>
  <!-- SEO 描述：搜索引擎用此描述来显示页面摘要 -->
  <meta name="description" content="这是一个现代化的 Web 应用示例">
  <!-- SEO 关键词：帮助搜索引擎理解页面内容 -->
  <meta name="keywords" content="Web, 应用, 开发">
  <!-- 引入样式表 -->
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <!-- 页头：网站的顶部，通常包含 logo 和导航菜单 -->
  <header>
    <nav>
      <ul>
        <li><a href="/">首页</a></li>
        <li><a href="/about">关于</a></li>
        <li><a href="/contact">联系</a></li>
      </ul>
    </nav>
  </header>

  <!-- 主内容区域：页面的核心内容 -->
  <main>
    <!-- 文章部分：包含文章标题、发布时间和内容 -->
    <article>
      <h1>欢迎来到我的博客</h1>
      <time datetime="2024-01-15">2024 年 1 月 15 日</time>
      <p>这是文章的主要内容。在这里可以写任何你想分享的信息。</p>
    </article>

    <!-- 侧边栏：通常用于放置辅助信息 -->
    <aside>
      <h3>相关链接</h3>
      <ul>
        <li><a href="#">链接 1</a></li>
        <li><a href="#">链接 2</a></li>
      </ul>
    </aside>
  </main>

  <!-- 页脚：网站的底部，通常包含版权信息和链接 -->
  <footer>
    <p>&copy; 2024 我的网站。保留所有权利。</p>
  </footer>

  <!-- 引入 JavaScript 文件，应该放在 body 末尾 -->
  <script src="main.js"></script>
</body>
</html>
```

这个 HTML5 结构展示了语义化标签的使用。`<header>`、`<main>`、`<article>`、`<aside>` 和 `<footer>` 这些标签不仅提高了代码的可读性，还帮助搜索引擎和屏幕阅读器更好地理解页面内容。

#### 表单和输入元素

```html
<!-- 表单是网页与用户交互的重要方式，用于收集用户信息 -->
<form action="/api/submit" method="POST" enctype="multipart/form-data">
  <!-- 文本输入：最基础的输入字段 -->
  <div class="form-group">
    <label for="username">用户名：</label>
    <input type="text" id="username" name="username" 
           placeholder="请输入用户名" required>
  </div>

  <!-- 邮箱输入：带有内置验证的邮箱字段 -->
  <div class="form-group">
    <label for="email">邮箱：</label>
    <input type="email" id="email" name="email" 
           placeholder="example@example.com" required>
  </div>

  <!-- 密码输入：输入内容会被隐藏 -->
  <div class="form-group">
    <label for="password">密码：</label>
    <input type="password" id="password" name="password" required>
  </div>

  <!-- 数字输入：只能输入数字，带有增减按钮 -->
  <div class="form-group">
    <label for="age">年龄：</label>
    <input type="number" id="age" name="age" min="0" max="150">
  </div>

  <!-- 日期输入：提供日期选择器 -->
  <div class="form-group">
    <label for="birthdate">出生日期：</label>
    <input type="date" id="birthdate" name="birthdate">
  </div>

  <!-- 单选按钮：从多个选项中选择一个 -->
  <div class="form-group">
    <label>性别：</label>
    <input type="radio" id="male" name="gender" value="male">
    <label for="male">男性</label>
    
    <input type="radio" id="female" name="gender" value="female">
    <label for="female">女性</label>
    
    <input type="radio" id="other" name="gender" value="other">
    <label for="other">其他</label>
  </div>

  <!-- 复选框：可以选择多个选项 -->
  <div class="form-group">
    <label>兴趣：</label>
    <input type="checkbox" id="reading" name="interests" value="reading">
    <label for="reading">阅读</label>
    
    <input type="checkbox" id="coding" name="interests" value="coding">
    <label for="coding">编程</label>
    
    <input type="checkbox" id="gaming" name="interests" value="gaming">
    <label for="gaming">游戏</label>
  </div>

  <!-- 下拉选择框：从列表中选择一个选项 -->
  <div class="form-group">
    <label for="country">国家/地区：</label>
    <select id="country" name="country" required>
      <option value="">-- 请选择 --</option>
      <option value="cn">中国</option>
      <option value="us">美国</option>
      <option value="uk">英国</option>
      <option value="jp">日本</option>
    </select>
  </div>

  <!-- 文本区域：用于输入多行文本 -->
  <div class="form-group">
    <label for="message">消息：</label>
    <textarea id="message" name="message" rows="5" cols="40" 
              placeholder="请输入您的消息"></textarea>
  </div>

  <!-- 文件上传：允许用户选择文件上传 -->
  <div class="form-group">
    <label for="file">上传文件：</label>
    <input type="file" id="file" name="file" accept=".jpg,.png,.pdf">
  </div>

  <!-- 提交按钮：提交表单 -->
  <button type="submit">提交表单</button>
  
  <!-- 重置按钮：清空表单所有输入 -->
  <button type="reset">清空表单</button>
</form>
```

HTML5 表单提供了丰富的输入类型和验证功能。使用正确的输入类型不仅提高了用户体验（例如，在移动设备上会显示对应的虚拟键盘），还能进行客户端验证，减少服务器的验证负担。

#### HTML5 多媒体元素

```html
<!-- 音频播放器：支持多种格式的音频文件 -->
<audio controls>
  <!-- source 标签提供多个格式，浏览器会选择支持的格式 -->
  <source src="audio.mp3" type="audio/mpeg">
  <source src="audio.ogg" type="audio/ogg">
  您的浏览器不支持音频播放。
</audio>

<!-- 视频播放器：支持多种格式的视频文件 -->
<video width="640" height="480" controls>
  <source src="video.mp4" type="video/mp4">
  <source src="video.webm" type="video/webm">
  您的浏览器不支持视频播放。
</video>

<!-- Canvas：用于绘制图形的 HTML5 元素 -->
<canvas id="myCanvas" width="400" height="300" style="border:1px solid #ccc;"></canvas>

<!-- SVG：可伸缩矢量图形，适合绘制复杂的图形 -->
<svg width="200" height="200">
  <!-- 矩形 -->
  <rect width="100" height="100" fill="blue"></rect>
  <!-- 圆形 -->
  <circle cx="150" cy="75" r="50" fill="red"></circle>
  <!-- 文本 -->
  <text x="10" y="50" font-size="20" fill="black">SVG 图形</text>
</svg>
```

### CSS3 深度教程

CSS（Cascading Style Sheets）用于控制网页的样式和布局。CSS3 引入了许多强大的新特性，如 Flexbox、Grid、动画和变换等。

#### CSS 基础选择器和样式

```css
/* 元素选择器：选择所有该类型的 HTML 元素 */
p {
  font-size: 16px;
  line-height: 1.6;
  color: #333;
}

/* 类选择器：选择具有特定类名的元素 */
.button {
  background-color: #007bff;
  color: white;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
  text-decoration: none;
  display: inline-block;
}

/* ID 选择器：选择具有特定 ID 的元素，应谨慎使用，因为 ID 应该唯一 */
#main {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

/* 属性选择器：根据元素属性进行选择 */
input[type="text"] {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

/* 伪类选择器：选择元素的特定状态 */
a:hover {
  color: #0056b3;
  text-decoration: underline;
}

button:active {
  transform: scale(0.98);
}

/* 伪元素：在元素前后插入内容 */
p::before {
  content: ">>> ";
  font-weight: bold;
}

/* 后代选择器：选择特定元素内的后代元素 */
nav ul li {
  list-style: none;
  display: inline-block;
}

/* 兄弟选择器：选择相邻的兄弟元素 */
h2 + p {
  margin-top: 0;
}
```

#### Flexbox 布局系统

```css
/* Flexbox 是现代 CSS 中最重要的布局工具，用于创建灵活的、响应式的布局 */

/* 容器设置 */
.flex-container {
  display: flex;
  /* 主轴方向：row 为水平，column 为垂直 */
  flex-direction: row;
  /* 主轴对齐方式：flex-start、center、flex-end、space-between、space-around */
  justify-content: center;
  /* 交叉轴对齐方式：flex-start、center、flex-end、stretch */
  align-items: center;
  /* 换行方式：nowrap、wrap、wrap-reverse */
  flex-wrap: wrap;
  /* 行之间的间距 */
  gap: 15px;
  /* 容器高度 */
  height: 300px;
  background-color: #f5f5f5;
}

/* 子元素设置 */
.flex-item {
  /* 放大因子：当容器有多余空间时，按比例分配 */
  flex-grow: 1;
  /* 缩小因子：当容器空间不足时，按比例缩小 */
  flex-shrink: 1;
  /* 基础宽度 */
  flex-basis: 200px;
  /* 简写：flex: grow shrink basis */
  /* flex: 1; */
  background-color: #007bff;
  color: white;
  padding: 20px;
  text-align: center;
  border-radius: 4px;
}

/* 导航栏示例：使用 Flexbox 创建响应式导航栏 */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #333;
  padding: 0 20px;
  height: 60px;
}

.navbar-brand {
  color: white;
  font-size: 20px;
  font-weight: bold;
}

.navbar-links {
  display: flex;
  gap: 30px;
  list-style: none;
  margin: 0;
  padding: 0;
}

.navbar-links a {
  color: white;
  text-decoration: none;
  transition: color 0.3s;
}

.navbar-links a:hover {
  color: #ffc107;
}
```

#### CSS Grid 布局

```css
/* CSS Grid 是另一个强大的布局系统，特别适合创建二维布局 */

.grid-container {
  display: grid;
  /* 定义列数和宽度：三列，每列平均分布 */
  grid-template-columns: repeat(3, 1fr);
  /* 定义行数和高度 */
  grid-template-rows: auto auto;
  /* 列之间的间距 */
  column-gap: 20px;
  /* 行之间的间距 */
  row-gap: 20px;
  /* 简写：gap: 20px; */
  gap: 20px;
  margin: 20px 0;
}

.grid-item {
  background-color: #007bff;
  color: white;
  padding: 40px;
  text-align: center;
  border-radius: 4px;
  /* 项目跨越多个列 */
  /* grid-column: span 2; */
  /* 项目跨越多个行 */
  /* grid-row: span 2; */
}

/* 响应式 Grid 布局 */
@media (max-width: 768px) {
  .grid-container {
    /* 在小屏幕上改为两列 */
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 480px) {
  .grid-container {
    /* 在更小的屏幕上改为单列 */
    grid-template-columns: 1fr;
  }
}

/* 复杂的 Grid 布局示例 */
.dashboard-grid {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr;
  grid-template-rows: auto 1fr auto;
  gap: 15px;
  height: 100vh;
}

.header {
  grid-column: 1 / -1;  /* 跨越所有列 */
  background-color: #333;
  color: white;
  padding: 20px;
}

.sidebar {
  grid-row: 2;
  background-color: #f8f9fa;
  padding: 20px;
}

.main-content {
  grid-column: 2;
  grid-row: 2;
  background-color: white;
  padding: 20px;
  overflow-y: auto;
}

.footer {
  grid-column: 1 / -1;
  background-color: #333;
  color: white;
  padding: 20px;
}
```

#### CSS 动画和变换

```css
/* 变换：改变元素的大小、位置和形状，但不影响文档流 */

/* 平移变换：沿 X、Y 轴移动元素 */
.translate-example {
  transform: translate(50px, 100px);
  /* 或者使用 3D 变换 */
  /* transform: translate3d(50px, 100px, 0); */
}

/* 旋转变换：旋转元素 */
.rotate-example {
  transform: rotate(45deg);
  /* 3D 旋转 */
  /* transform: rotateX(45deg) rotateY(45deg) rotateZ(45deg); */
}

/* 缩放变换：改变元素大小 */
.scale-example {
  transform: scale(1.5);
  /* 分别缩放 X 和 Y 轴 */
  /* transform: scaleX(1.5) scaleY(0.8); */
}

/* 倾斜变换：改变元素角度 */
.skew-example {
  transform: skew(20deg, 10deg);
}

/* 变换原点：指定变换的中心点 */
.transform-origin-example {
  transform-origin: top left;
  transform: rotate(45deg);
}

/* 过渡：平滑地在两个状态之间变化 */
.button-with-transition {
  background-color: #007bff;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  /* 指定要过渡的属性、持续时间、缓动函数和延迟 */
  transition: background-color 0.3s ease, transform 0.2s ease;
}

.button-with-transition:hover {
  background-color: #0056b3;
  transform: scale(1.1);
}

/* 关键帧动画：定义更复杂的动画序列 */
@keyframes slideIn {
  /* 动画的起始状态 */
  from {
    opacity: 0;
    transform: translateX(-100px);
  }
  /* 动画的结束状态 */
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

/* 应用动画 */
.animated-element {
  /* 动画名称、持续时间、缓动函数、延迟、循环次数、方向 */
  animation: slideIn 1s ease-out 0.5s 1 normal;
}

/* 更复杂的动画：多个关键帧 */
@keyframes bounce {
  0%, 100% {
    transform: translateY(0);
  }
  25% {
    transform: translateY(-20px);
  }
  50% {
    transform: translateY(0);
  }
  75% {
    transform: translateY(-10px);
  }
}

.bouncing-ball {
  animation: bounce 1s ease-in-out infinite;
}
```

#### 响应式设计和媒体查询

```css
/* 响应式设计是现代 Web 开发的必须，确保网站在各种设备上都能正常显示 */

/* 基础样式：手机优先的方法 */
body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f5f5f5;
}

.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 15px;
}

.grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 20px;
}

/* 小屏幕：手机设备 (320px - 480px) */
@media (min-width: 480px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* 中等屏幕：平板设备 (768px - 1024px) */
@media (min-width: 768px) {
  .grid {
    grid-template-columns: repeat(3, 1fr);
  }
  
  .sidebar {
    display: block;
    width: 250px;
    float: left;
    margin-right: 20px;
  }
  
  .main-content {
    overflow: hidden;
  }
}

/* 大屏幕：桌面设备 (1025px+) */
@media (min-width: 1024px) {
  .grid {
    grid-template-columns: repeat(4, 1fr);
  }
  
  .container {
    padding: 0 30px;
  }
}

/* 超大屏幕：大型显示器 */
@media (min-width: 1440px) {
  .container {
    max-width: 1400px;
  }
}

/* 针对特定设备的媒体查询 */
/* 只在横屏模式下应用 */
@media (orientation: landscape) {
  .mobile-menu {
    display: none;
  }
}

/* 高分辨率屏幕（视网膜屏）*/
@media (min-resolution: 2dppx) {
  .logo {
    background-image: url('logo@2x.png');
    background-size: 50%;
  }
}

/* 暗黑模式支持 */
@media (prefers-color-scheme: dark) {
  body {
    background-color: #1a1a1a;
    color: #e0e0e0;
  }
}
```

### JavaScript 核心概念详解

JavaScript 是 Web 开发的编程语言，提供了与 DOM 交互、处理事件、异步操作等功能。

#### ES6+ 基本语法

```javascript
// 变量声明：const 优先，其次 let，避免使用 var
const PI = 3.14159;  // 常量，不能重新赋值
let count = 0;       // 块级作用域，可以重新赋值
var old = 'old';     // 函数作用域，避免使用（容易产生bug）

// 模板字符串：用反引号包含，支持插值和多行
const name = '张三';
const age = 25;
const message = `我叫${name}，今年${age}岁。
这是多行文本。`;

// 解构赋值：快速提取对象或数组的值
const user = { username: 'john', email: 'john@example.com', role: 'admin' };
const { username, email } = user;  // 提取特定属性
const { role = 'user' } = user;    // 提供默认值

const arr = [1, 2, 3, 4, 5];
const [first, second, ...rest] = arr;  // 第一个、第二个、其余元素

// 剩余参数和扩展操作符
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}
console.log(sum(1, 2, 3, 4, 5));  // 输出：15

const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combined = [...arr1, ...arr2];  // 合并数组

// 箭头函数：简洁的函数语法，自动绑定 this
const add = (a, b) => a + b;
const greet = name => `Hello, ${name}!`;
const multiply = () => 2 * 3;

// 回调函数：将函数作为参数传递给另一个函数
function fetchData(callback) {
  setTimeout(() => {
    const data = { id: 1, name: 'User' };
    callback(data);
  }, 1000);
}

fetchData((data) => {
  console.log('Received:', data);
});
```

#### 异步编程

```javascript
// Promise：处理异步操作的标准方式
function fetchUserData(userId) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (userId > 0) {
        resolve({ id: userId, name: `User ${userId}` });
      } else {
        reject(new Error('Invalid user ID'));
      }
    }, 1000);
  });
}

// 使用 Promise
fetchUserData(1)
  .then(user => {
    console.log('User found:', user);
    return fetchUserData(2);  // 链式调用
  })
  .then(user => {
    console.log('Second user:', user);
  })
  .catch(error => {
    console.error('Error:', error.message);
  })
  .finally(() => {
    console.log('Operation complete');
  });

// async/await：更简洁的异步语法，基于 Promise
async function getUserData() {
  try {
    // await 暂停执行，直到 Promise 解决
    const user1 = await fetchUserData(1);
    console.log('First user:', user1);
    
    const user2 = await fetchUserData(2);
    console.log('Second user:', user2);
    
    // 并行执行多个 Promise
    const [user3, user4] = await Promise.all([
      fetchUserData(3),
      fetchUserData(4)
    ]);
    console.log('Users 3 and 4:', user3, user4);
  } catch (error) {
    console.error('Error:', error.message);
  }
}

getUserData();

// Fetch API：获取远程资源
async function getPostsFromAPI() {
  try {
    // GET 请求
    const response = await fetch('https://jsonplaceholder.typicode.com/posts');
    
    // 检查响应状态
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    
    // 解析 JSON
    const posts = await response.json();
    console.log('Posts:', posts);
    return posts;
  } catch (error) {
    console.error('Failed to fetch posts:', error);
  }
}

// POST 请求
async function createPost(title, content) {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/posts', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({ title, content, userId: 1 })
    });
    
    const newPost = await response.json();
    console.log('Created post:', newPost);
    return newPost;
  } catch (error) {
    console.error('Failed to create post:', error);
  }
}
```

#### DOM 操作和事件处理

```javascript
// DOM 选择和修改
// 选择元素
const element = document.getElementById('my-id');  // 按 ID
const elements = document.getElementsByClassName('my-class');  // 按类名
const elements2 = document.querySelectorAll('.item');  // CSS 选择器（推荐）

// 修改内容
element.textContent = 'New text';  // 设置纯文本
element.innerHTML = '<strong>Bold text</strong>';  // 设置 HTML（要谨慎）

// 修改属性
element.setAttribute('data-id', '123');
element.id = 'new-id';
element.className = 'new-class';
element.classList.add('active');     // 添加类
element.classList.remove('active');  // 移除类
element.classList.toggle('active');  // 切换类

// 修改样式
element.style.color = 'red';
element.style.backgroundColor = '#f0f0f0';
element.style.display = 'none';

// 创建和删除元素
const newDiv = document.createElement('div');
newDiv.textContent = 'New element';
document.body.appendChild(newDiv);  // 追加到末尾

const parent = document.getElementById('container');
parent.removeChild(element);  // 移除子元素
element.remove();  // 直接移除

// 事件处理：响应用户交互
const button = document.getElementById('my-button');

// 方法 1：在 HTML 中添加事件处理器（不推荐，混合了 HTML 和 JavaScript）
// <button onclick="handleClick()">Click me</button>

// 方法 2：使用 addEventListener（推荐）
button.addEventListener('click', () => {
  console.log('Button clicked!');
});

// 移除事件监听
function handleClick() {
  console.log('Clicked!');
}
button.addEventListener('click', handleClick);
button.removeEventListener('click', handleClick);

// 常见事件类型
document.addEventListener('DOMContentLoaded', () => {
  console.log('DOM 已加载完成');
});

window.addEventListener('resize', () => {
  console.log('窗口已调整大小');
});

const input = document.getElementById('search-input');
input.addEventListener('input', (event) => {
  console.log('Input value:', event.target.value);
});

input.addEventListener('change', (event) => {
  console.log('Final value:', event.target.value);
});

// 阻止事件的默认行为
const link = document.querySelector('a');
link.addEventListener('click', (event) => {
  event.preventDefault();  // 阻止默认的链接跳转
  console.log('Link clicked, but navigation prevented');
});

// 事件委托：在父元素上处理子元素的事件，提高性能
const list = document.getElementById('item-list');
list.addEventListener('click', (event) => {
  if (event.target.tagName === 'LI') {
    console.log('Clicked item:', event.target.textContent);
  }
});
```

### TypeScript 详解

TypeScript 是 JavaScript 的超集，添加了静态类型和其他高级特性，使代码更健壮和易维护。

#### 基础类型

```typescript
// 基本类型
let string: string = 'Hello';
let number: number = 42;
let boolean: boolean = true;
let any_type: any = 'anything';  // 避免使用 any，会失去类型检查的优势
let unknown_type: unknown = 'unknown';  // 比 any 更安全

// 数组类型
let numbers: number[] = [1, 2, 3];
let strings: Array<string> = ['a', 'b', 'c'];
let mixed: (string | number)[] = [1, 'two', 3];

// 元组：固定长度和类型的数组
let tuple: [string, number] = ['hello', 42];
let tuple2: [string, number, boolean] = ['hello', 42, true];

// 枚举：定义一组命名的常量
enum Color {
  Red,
  Green,
  Blue
}
let color: Color = Color.Red;

enum Status {
  Active = 'ACTIVE',
  Inactive = 'INACTIVE',
  Pending = 'PENDING'
}
let status: Status = Status.Active;

// 联合类型：值可以是多个类型中的一个
let id: string | number;
id = 'ID123';
id = 123;

// 字面量类型：限制值为特定的字面量
let direction: 'up' | 'down' | 'left' | 'right';
direction = 'up';  // 正确
// direction = 'diagonal';  // 错误

// 类型别名：为类型创建一个新名称
type Point = { x: number; y: number };
let point: Point = { x: 10, y: 20 };

// 接口：定义对象的形状和契约
interface User {
  id: number;
  username: string;
  email: string;
  age?: number;  // 可选属性
  readonly role: string;  // 只读属性
  greet(): string;  // 方法
}

const user: User = {
  id: 1,
  username: 'john',
  email: 'john@example.com',
  role: 'admin',
  greet() {
    return `Hello, I'm ${this.username}`;
  }
};
```

#### 函数和类

```typescript
// 函数类型注解
function add(a: number, b: number): number {
  return a + b;
}

// 可选参数和默认参数
function greet(name: string, greeting: string = 'Hello'): string {
  return `${greeting}, ${name}!`;
}

// 剩余参数
function sum(...numbers: number[]): number {
  return numbers.reduce((total, num) => total + num, 0);
}

// 函数类型
type MathOperation = (a: number, b: number) => number;
const multiply: MathOperation = (a, b) => a * b;

// 重载：同一个函数名，多个签名
function process(value: string): string;
function process(value: number): number;
function process(value: string | number): string | number {
  if (typeof value === 'string') {
    return value.toUpperCase();
  }
  return value * 2;
}

// 类：对象的模板
class Animal {
  // 属性
  name: string;
  age: number;
  
  // 访问修饰符
  protected species: string;  // 只能在类和子类中访问
  private energy: number;     // 只能在类中访问
  public sound: string;       // 公开，默认是 public
  
  // 构造函数
  constructor(name: string, age: number, species: string) {
    this.name = name;
    this.age = age;
    this.species = species;
    this.energy = 100;
    this.sound = 'sound';
  }
  
  // 方法
  speak(): void {
    console.log(`${this.name} makes a sound`);
  }
  
  // 只读属性和方法
  readonly birthYear: number = new Date().getFullYear();
  
  // Getter 和 Setter
  get exhausted(): boolean {
    return this.energy < 10;
  }
  
  set rest(hours: number) {
    this.energy = Math.min(100, this.energy + hours * 10);
  }
  
  // 静态方法和属性
  static count: number = 0;
  static create(name: string): Animal {
    Animal.count++;
    return new Animal(name, 0, 'unknown');
  }
}

// 继承
class Dog extends Animal {
  breed: string;
  
  constructor(name: string, age: number, breed: string) {
    super(name, age, 'Dog');  // 调用父类构造函数
    this.breed = breed;
  }
  
  // 重写父类方法
  speak(): void {
    console.log(`${this.name} barks`);
  }
}

// 接口实现
interface Flyable {
  fly(): void;
}

class Bird extends Animal implements Flyable {
  fly(): void {
    console.log(`${this.name} is flying`);
  }
}

// 抽象类：不能直接实例化，用于被继承
abstract class Vehicle {
  abstract start(): void;
  
  stop(): void {
    console.log('Vehicle stopped');
  }
}

class Car extends Vehicle {
  start(): void {
    console.log('Car started');
  }
}

// 泛型：创建可重用的类和函数
function identity<T>(arg: T): T {
  return arg;
}

const stringValue = identity<string>('hello');
const numberValue = identity<number>(42);

// 泛型类
class Box<T> {
  private content: T;
  
  constructor(content: T) {
    this.content = content;
  }
  
  getContent(): T {
    return this.content;
  }
}

const stringBox = new Box<string>('Hello');
const numberBox = new Box<number>(42);

// 泛型约束
interface HasLength {
  length: number;
}

function getLength<T extends HasLength>(arg: T): number {
  return arg.length;
}

console.log(getLength('hello'));      // 5
console.log(getLength([1, 2, 3]));    // 3
```

## 学习路线

1. **基础阶段**：学习 HTML、CSS、JavaScript 基础和后端语言基础
2. **框架阶段**：深入学习前端框架和后端框架
3. **进阶阶段**：学习数据库、API 设计、认证授权
4. **项目实战**：通过完整项目实战应用所学知识
5. **生产部署**：学习如何将应用部署到生产环境

## 最佳实践

- 遵循代码规范和设计模式
- 编写可测试的代码
- 重视文档和注释
- 持续学习和优化
- 关注安全和性能

## 资源推荐

### 前端

- Vue.js 官方文档
- React 官方文档
- MDN Web 文档
- Web 性能工作组文档

### 后端

- Node.js 官方文档
- Spring Boot 官方文档
- Django 官方文档
- 数据库文档（MySQL、PostgreSQL）

### 工具和框架

- Vite - 下一代前端构建工具
- Webpack - 模块打包器
- Docker - 容器化技术
- Kubernetes - 容器编排平台

## 深入前端开发

### Vue 3 完全指南

Vue 3 是一个渐进式的 JavaScript 框架，使用 Composition API，提供了更灵活和强大的方式来组织组件逻辑。相比 Vue 2，Vue 3 性能提升了 1.3-1.6 倍，并且使用了 TypeScript 编写，提供了更好的类型支持。

#### Vue 3 核心概念

```javascript
// Vue 3 Composition API：是一套 API，允许以函数的方式组织组件逻辑
// 相比 Options API（分散在 data、methods、computed 等选项中），
// Composition API 更灵活，代码组织更清晰

import { ref, reactive, computed, watch, onMounted, onUnmounted } from 'vue'

// 1. ref：创建响应式的基本类型值
// 使用 ref 包装基本类型（string、number、boolean 等）
const count = ref(0)

// 访问和修改 ref 值需要使用 .value 属性
console.log(count.value)  // 0
count.value++              // 修改值

// 2. reactive：创建响应式对象
// 用于包装对象和数组，自动追踪嵌套属性
const user = reactive({
  username: 'john',
  email: 'john@example.com',
  profile: {
    age: 25,
    location: 'Beijing'
  }
})

// 可以直接修改属性
user.username = 'jane'
user.profile.age = 26

// 3. computed：创建计算属性
// computed 返回一个 ref，可以缓存计算结果，只在依赖改变时重新计算
const userInfo = computed(() => {
  return `${user.username} (${user.profile.age})`
})

// 4. watch：监听响应式数据的变化
// 监听单个 ref
watch(count, (newValue, oldValue) => {
  console.log(`Count changed from ${oldValue} to ${newValue}`)
})

// 监听对象属性
watch(
  () => user.username,
  (newName, oldName) => {
    console.log(`Username changed from ${oldName} to ${newName}`)
  }
)

// 监听多个源
watch([count, () => user.username], ([newCount, newName]) => {
  console.log(`Count: ${newCount}, Username: ${newName}`)
})

// 深度监听
watch(
  () => user.profile,
  (newProfile) => {
    console.log('Profile changed:', newProfile)
  },
  { deep: true }  // 启用深度监听
)

// 5. 生命周期钩子：在组件的特定阶段执行代码
onMounted(() => {
  console.log('Component mounted')
  // 此时 DOM 已经挂载，可以进行 DOM 操作或发起 API 请求
})

onUnmounted(() => {
  console.log('Component unmounted')
  // 清理工作：移除事件监听、取消 API 请求等
})
```

#### Vue 3 完整组件示例

```vue
<!-- 这是一个 Vue 3 单文件组件 (.vue 文件) -->
<template>
  <!-- 模板部分：定义组件的 HTML 结构 -->
  <div class="todo-app">
    <!-- 标题 -->
    <h1>{{ title }}</h1>
    
    <!-- 输入框和添加按钮 -->
    <div class="input-group">
      <input 
        v-model="newTodoText"
        placeholder="添加新的待办事项..."
        @keyup.enter="addTodo"
        class="input-field"
      />
      <button @click="addTodo" class="btn btn-primary">
        添加
      </button>
    </div>
    
    <!-- 过滤器按钮 -->
    <div class="filter-buttons">
      <button 
        v-for="filter in filters" 
        :key="filter"
        @click="currentFilter = filter"
        :class="{ active: currentFilter === filter }"
        class="btn"
      >
        {{ filterLabel[filter] }}
      </button>
    </div>
    
    <!-- 待办事项列表 -->
    <div v-if="filteredTodos.length > 0" class="todo-list">
      <!-- v-for 遍历列表 -->
      <div 
        v-for="todo in filteredTodos" 
        :key="todo.id"
        class="todo-item"
        :class="{ completed: todo.completed }"
      >
        <!-- 复选框：用于标记完成状态 -->
        <input 
          type="checkbox" 
          v-model="todo.completed"
          class="checkbox"
        />
        <!-- 待办事项文本 -->
        <span class="todo-text">{{ todo.text }}</span>
        <!-- 优先级标签 -->
        <span class="priority-badge" :class="`priority-${todo.priority}`">
          {{ priorityLabel[todo.priority] }}
        </span>
        <!-- 删除按钮 -->
        <button @click="deleteTodo(todo.id)" class="btn btn-delete">
          删除
        </button>
      </div>
    </div>
    
    <!-- 空列表提示 -->
    <div v-else class="empty-state">
      <p>没有待办事项</p>
    </div>
    
    <!-- 统计信息 -->
    <div class="stats">
      <p>总数: {{ totalTodos }}</p>
      <p>已完成: {{ completedCount }}</p>
      <p>进度: {{ progressPercentage }}%</p>
    </div>
    
    <!-- 清空已完成按钮 -->
    <button v-if="completedCount > 0" @click="clearCompleted" class="btn btn-danger">
      清空已完成
    </button>
  </div>
</template>

<script setup>
// setup 是 Composition API 的入口点
import { ref, computed } from 'vue'

// 定义响应式数据
const title = ref('我的待办事项')
const newTodoText = ref('')
const currentFilter = ref('all')
const todos = ref([
  { id: 1, text: '学习 Vue 3', completed: false, priority: 'high' },
  { id: 2, text: '完成项目', completed: false, priority: 'medium' },
  { id: 3, text: '阅读文档', completed: true, priority: 'low' }
])

// 过滤器选项和标签
const filters = ['all', 'active', 'completed']
const filterLabel = {
  all: '全部',
  active: '进行中',
  completed: '已完成'
}

const priorityLabel = {
  high: '高',
  medium: '中',
  low: '低'
}

// 计算属性：根据过滤器返回不同的待办事项列表
const filteredTodos = computed(() => {
  switch (currentFilter.value) {
    case 'active':
      return todos.value.filter(todo => !todo.completed)
    case 'completed':
      return todos.value.filter(todo => todo.completed)
    default:
      return todos.value
  }
})

// 计算属性：总数
const totalTodos = computed(() => todos.value.length)

// 计算属性：已完成的数量
const completedCount = computed(() => {
  return todos.value.filter(todo => todo.completed).length
})

// 计算属性：完成进度百分比
const progressPercentage = computed(() => {
  if (totalTodos.value === 0) return 0
  return Math.round((completedCount.value / totalTodos.value) * 100)
})

// 方法：添加待办事项
function addTodo() {
  if (newTodoText.value.trim()) {
    todos.value.push({
      id: Math.max(...todos.value.map(t => t.id), 0) + 1,
      text: newTodoText.value,
      completed: false,
      priority: 'medium'
    })
    newTodoText.value = ''  // 清空输入框
  }
}

// 方法：删除待办事项
function deleteTodo(id) {
  const index = todos.value.findIndex(todo => todo.id === id)
  if (index !== -1) {
    todos.value.splice(index, 1)
  }
}

// 方法：清空已完成的待办事项
function clearCompleted() {
  todos.value = todos.value.filter(todo => !todo.completed)
}
</script>

<style scoped>
/* scoped 使样式仅应用于当前组件 */

.todo-app {
  max-width: 600px;
  margin: 20px auto;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

h1 {
  color: #333;
  margin-bottom: 20px;
  text-align: center;
}

.input-group {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.input-field {
  flex: 1;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 14px;
  transition: border-color 0.3s;
}

.input-field:focus {
  outline: none;
  border-color: #007bff;
}

.btn {
  padding: 10px 15px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 14px;
  transition: background-color 0.3s;
}

.btn-primary {
  background-color: #007bff;
  color: white;
}

.btn-primary:hover {
  background-color: #0056b3;
}

.btn-delete {
  background-color: #dc3545;
  color: white;
  padding: 5px 10px;
  font-size: 12px;
}

.btn-delete:hover {
  background-color: #c82333;
}

.btn-danger {
  background-color: #dc3545;
  color: white;
  width: 100%;
  margin-top: 20px;
}

.filter-buttons {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
  justify-content: center;
}

.btn.active {
  background-color: #007bff;
  color: white;
}

.todo-list {
  margin-bottom: 20px;
}

.todo-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 12px;
  background-color: white;
  border-left: 3px solid #007bff;
  margin-bottom: 10px;
  border-radius: 4px;
  transition: opacity 0.3s;
}

.todo-item.completed {
  opacity: 0.6;
}

.todo-item.completed .todo-text {
  text-decoration: line-through;
  color: #999;
}

.checkbox {
  width: 18px;
  height: 18px;
  cursor: pointer;
}

.todo-text {
  flex: 1;
  color: #333;
}

.priority-badge {
  padding: 4px 8px;
  border-radius: 12px;
  font-size: 12px;
  font-weight: bold;
  color: white;
}

.priority-high {
  background-color: #dc3545;
}

.priority-medium {
  background-color: #ffc107;
  color: #333;
}

.priority-low {
  background-color: #28a745;
}

.empty-state {
  text-align: center;
  padding: 40px;
  color: #999;
  font-size: 16px;
}

.stats {
  padding: 15px;
  background-color: white;
  border-radius: 4px;
  margin-bottom: 20px;
}

.stats p {
  margin: 5px 0;
  color: #666;
}
</style>
```

#### Vue Router：路由管理

```javascript
// router/index.js - Vue Router 用于管理应用的不同页面和路由

import { createRouter, createWebHistory } from 'vue-router'
import Home from '@/pages/Home.vue'
import About from '@/pages/About.vue'
import ArticleList from '@/pages/ArticleList.vue'
import ArticleDetail from '@/pages/ArticleDetail.vue'
import NotFound from '@/pages/NotFound.vue'

// 定义路由表：每个路由对应一个路径和组件
const routes = [
  {
    path: '/',
    name: 'Home',
    component: Home,
    meta: { title: '首页' }  // 元数据，可用于设置页面标题等
  },
  {
    path: '/about',
    name: 'About',
    component: About,
    meta: { title: '关于' }
  },
  {
    path: '/articles',
    name: 'ArticleList',
    component: ArticleList,
    meta: { title: '文章列表' }
  },
  {
    // 动态路由参数：:id 是动态参数，用于获取具体的文章
    path: '/articles/:id',
    name: 'ArticleDetail',
    component: ArticleDetail,
    meta: { title: '文章详情' }
  },
  {
    // 404 页面：捕获所有未定义的路由
    path: '/:pathMatch(.*)*',
    name: 'NotFound',
    component: NotFound
  }
]

// 创建路由实例
const router = createRouter({
  // 使用 HTML5 History 模式，URL 看起来更清洁
  history: createWebHistory(import.meta.env.BASE_URL),
  routes
})

// 路由守卫：在路由切换前执行
router.beforeEach((to, from, next) => {
  // 在页面切换前做一些处理（例如检查权限）
  console.log(`从 ${from.path} 跳转到 ${to.path}`)
  next()  // 继续导航
})

// 路由守卫：在导航完成后执行
router.afterEach((to) => {
  // 设置页面标题
  document.title = to.meta.title || '我的网站'
})

export default router
```

### React 18 完全指南

React 是由 Facebook 开发的声明式 UI 库，通过 JSX 语法和组件化思想，使 UI 开发更加高效。React 18 引入了 Concurrent Rendering 等新特性，性能和用户体验都有显著提升。

#### React 基础概念

```javascript
// React 使用 JSX：一种在 JavaScript 中编写类似 HTML 的语法
// JSX 会被编译成 React.createElement() 调用

import React, { useState, useEffect, useCallback } from 'react'

// 函数组件：React 推荐的组件编写方式
function Counter() {
  // useState Hook：用于在函数组件中添加状态
  // 返回 [状态值, 更新函数]
  const [count, setCount] = useState(0)
  const [name, setName] = useState('User')
  
  // 处理计数增加
  const handleIncrement = () => {
    setCount(count + 1)
  }
  
  // 处理计数减少
  const handleDecrement = () => {
    setCount(prevCount => prevCount - 1)
  }
  
  // JSX：看起来像 HTML，但实际上是 JavaScript
  return (
    <div className="counter">
      <h2>计数器: {count}</h2>
      <p>你好，{name}!</p>
      <button onClick={handleIncrement}>增加</button>
      <button onClick={handleDecrement}>减少</button>
      <input 
        value={name} 
        onChange={(e) => setName(e.target.value)}
        placeholder="输入你的名字"
      />
    </div>
  )
}

// useEffect Hook：处理副作用（API 请求、订阅、定时器等）
function UserProfile({ userId }) {
  const [user, setUser] = useState(null)
  const [loading, setLoading] = useState(true)
  const [error, setError] = useState(null)
  
  useEffect(() => {
    // 副作用函数：在组件挂载后和 userId 改变时执行
    let isMounted = true  // 标志位，防止内存泄漏
    
    const fetchUser = async () => {
      try {
        setLoading(true)
        const response = await fetch(`/api/users/${userId}`)
        if (!response.ok) throw new Error('Failed to fetch')
        const data = await response.json()
        
        if (isMounted) {
          setUser(data)
          setError(null)
        }
      } catch (err) {
        if (isMounted) {
          setError(err.message)
        }
      } finally {
        if (isMounted) {
          setLoading(false)
        }
      }
    }
    
    fetchUser()
    
    // 清理函数：组件卸载时执行
    return () => {
      isMounted = false
    }
  }, [userId])  // 依赖数组：只在 userId 改变时重新执行
  
  if (loading) return <div>加载中...</div>
  if (error) return <div>错误: {error}</div>
  if (!user) return <div>未找到用户</div>
  
  return (
    <div className="user-profile">
      <h3>{user.username}</h3>
      <p>Email: {user.email}</p>
    </div>
  )
}

// useCallback Hook：缓存函数，防止不必要的重新创建
function ParentComponent() {
  const [count, setCount] = useState(0)
  
  // 即使父组件重新渲染，callback 函数也不会重新创建
  // 除非 count 改变
  const memoizedCallback = useCallback(() => {
    console.log('Callback called with count:', count)
  }, [count])
  
  return (
    <div>
      <Child callback={memoizedCallback} />
      <button onClick={() => setCount(count + 1)}>增加</button>
    </div>
  )
}

function Child({ callback }) {
  // 由于 callback 被记忆，这个组件不会不必要地重新渲染
  return <button onClick={callback}>调用回调</button>
}

export default Counter
```

#### React 上下文和状态管理

```javascript
// React Context：用于跨组件传递数据，避免 prop drilling

import React, { createContext, useState } from 'react'

// 创建一个上下文
const ThemeContext = createContext()

// 提供者组件：在组件树的顶部使用，为所有子组件提供状态
export function ThemeProvider({ children }) {
  const [theme, setTheme] = useState('light')
  
  const toggleTheme = () => {
    setTheme(prev => prev === 'light' ? 'dark' : 'light')
  }
  
  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  )
}

// 自定义 Hook：使用上下文
export function useTheme() {
  const context = React.useContext(ThemeContext)
  if (!context) {
    throw new Error('useTheme must be used within ThemeProvider')
  }
  return context
}

// 使用上下文的组件
function Header() {
  const { theme, toggleTheme } = useTheme()
  
  return (
    <header className={`header ${theme}`}>
      <h1>我的应用</h1>
      <button onClick={toggleTheme}>
        切换到 {theme === 'light' ? '深色' : '浅色'} 模式
      </button>
    </header>
  )
}

// Redux：用于复杂的全局状态管理
import { createSlice, configureStore } from '@reduxjs/toolkit'
import { Provider, useDispatch, useSelector } from 'react-redux'

// 创建 slice：包含 reducer 和 actions
const counterSlice = createSlice({
  name: 'counter',
  initialState: { value: 0 },
  reducers: {
    increment: state => {
      state.value += 1
    },
    decrement: state => {
      state.value -= 1
    },
    incrementByAmount: (state, action) => {
      state.value += action.payload
    }
  }
})

export const { increment, decrement, incrementByAmount } = counterSlice.actions

// 创建 store：所有 reducer 的集合
const store = configureStore({
  reducer: {
    counter: counterSlice.reducer
  }
})

// 使用 Redux 的组件
function Counter() {
  const dispatch = useDispatch()
  const count = useSelector(state => state.counter.value)
  
  return (
    <div>
      <p>计数: {count}</p>
      <button onClick={() => dispatch(increment())}>增加</button>
      <button onClick={() => dispatch(decrement())}>减少</button>
      <button onClick={() => dispatch(incrementByAmount(5))}>增加 5</button>
    </div>
  )
}

// 应用入口：使用 Provider 包装应用
export default function App() {
  return (
    <Provider store={store}>
      <ThemeProvider>
        <Header />
        <Counter />
      </ThemeProvider>
    </Provider>
  )
}
```

#### 自定义 React Hooks

```javascript
// 自定义 Hooks：将组件逻辑提取为可复用的函数

import { useState, useEffect, useRef, useCallback } from 'react'

// Hook 1: useFetch - 用于数据获取
export function useFetch(url) {
  const [data, setData] = useState(null)
  const [loading, setLoading] = useState(true)
  const [error, setError] = useState(null)
  
  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch(url)
        if (!response.ok) throw new Error('API 错误')
        const result = await response.json()
        setData(result)
      } catch (err) {
        setError(err.message)
      } finally {
        setLoading(false)
      }
    }
    
    fetchData()
  }, [url])
  
  return { data, loading, error }
}

// 使用 useFetch
function PostsList() {
  const { data: posts, loading, error } = useFetch('/api/posts')
  
  if (loading) return <div>加载中...</div>
  if (error) return <div>错误: {error}</div>
  
  return (
    <ul>
      {posts?.map(post => (
        <li key={post.id}>{post.title}</li>
      ))}
    </ul>
  )
}

// Hook 2: useLocalStorage - 与 localStorage 同步
export function useLocalStorage(key, initialValue) {
  const [value, setValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(key)
      return item ? JSON.parse(item) : initialValue
    } catch (error) {
      console.error(error)
      return initialValue
    }
  })
  
  const setStoredValue = useCallback((value) => {
    try {
      const valueToStore = value instanceof Function ? value(value) : value
      setValue(valueToStore)
      window.localStorage.setItem(key, JSON.stringify(valueToStore))
    } catch (error) {
      console.error(error)
    }
  }, [key])
  
  return [value, setStoredValue]
}

// 使用 useLocalStorage
function UserPreferences() {
  const [theme, setTheme] = useLocalStorage('theme', 'light')
  const [language, setLanguage] = useLocalStorage('language', 'zh')
  
  return (
    <div>
      <select value={theme} onChange={(e) => setTheme(e.target.value)}>
        <option value="light">浅色</option>
        <option value="dark">深色</option>
      </select>
      <select value={language} onChange={(e) => setLanguage(e.target.value)}>
        <option value="zh">中文</option>
        <option value="en">English</option>
      </select>
    </div>
  )
}

// Hook 3: useAsync - 用于异步操作管理
export function useAsync(asyncFunction, immediate = true) {
  const [status, setStatus] = useState('idle')
  const [data, setData] = useState(null)
  const [error, setError] = useState(null)
  
  const execute = useCallback(async () => {
    setStatus('pending')
    setData(null)
    setError(null)
    
    try {
      const result = await asyncFunction()
      setData(result)
      setStatus('success')
      return result
    } catch (err) {
      setError(err)
      setStatus('error')
      throw err
    }
  }, [asyncFunction])
  
  useEffect(() => {
    if (immediate) {
      execute()
    }
  }, [execute, immediate])
  
  return { status, data, error, execute }
}

// Hook 4: useDebounce - 防抖 Hook
export function useDebounce(value, delay) {
  const [debouncedValue, setDebouncedValue] = useState(value)
  
  useEffect(() => {
    // 延迟 delay 毫秒后执行
    const handler = setTimeout(() => {
      setDebouncedValue(value)
    }, delay)
    
    // 清理：如果 value 在 delay 时间内改变，取消上一次的执行
    return () => clearTimeout(handler)
  }, [value, delay])
  
  return debouncedValue
}

// 使用 useDebounce 实现搜索
function SearchUsers() {
  const [searchTerm, setSearchTerm] = useState('')
  const debouncedSearchTerm = useDebounce(searchTerm, 500)
  const { data: results } = useFetch(
    debouncedSearchTerm ? `/api/search?q=${debouncedSearchTerm}` : ''
  )
  
  return (
    <div>
      <input
        value={searchTerm}
        onChange={(e) => setSearchTerm(e.target.value)}
        placeholder="搜索用户..."
      />
      <ul>
        {results?.map(result => (
          <li key={result.id}>{result.name}</li>
        ))}
      </ul>
    </div>
  )
}
```

#### React 性能优化

```javascript
// React.memo：防止不必要的重新渲染
import React, { memo, useMemo } from 'react'

const UserCard = memo(({ user, onDelete }) => {
  console.log('UserCard rendered for:', user.id)
  return (
    <div className="user-card">
      <h3>{user.name}</h3>
      <p>{user.email}</p>
      <button onClick={() => onDelete(user.id)}>删除</button>
    </div>
  )
})

// useMemo：缓存计算结果
function ExpensiveList({ users, filter }) {
  // 只有当 users 或 filter 改变时，才重新计算
  const filteredUsers = useMemo(() => {
    console.log('Filtering users...')
    return users.filter(user => user.name.includes(filter))
  }, [users, filter])
  
  return (
    <div>
      {filteredUsers.map(user => (
        <div key={user.id}>{user.name}</div>
      ))}
    </div>
  )
}

// 代码分割：使用 React.lazy 和 Suspense
const HeavyComponent = React.lazy(() => import('./HeavyComponent'))

function App() {
  return (
    <React.Suspense fallback={<div>加载中...</div>}>
      <HeavyComponent />
    </React.Suspense>
  )
}
```

## 学习路线

1. **基础阶段**：学习 HTML、CSS、JavaScript 基础和后端语言基础
2. **框架阶段**：深入学习前端框架和后端框架
3. **进阶阶段**：学习数据库、API 设计、认证授权
4. **项目实战**：通过完整项目实战应用所学知识
5. **生产部署**：学习如何将应用部署到生产环境

## Pinia 状态管理详解

```javascript
// Pinia 是 Vue 3 的官方状态管理库，比 Vuex 更简洁更高效

import { defineStore } from 'pinia'
import { ref, computed } from 'vue'

// 定义一个 store：使用组合式 API
export const useUserStore = defineStore('user', () => {
  // 状态：定义应用的数据
  const user = ref(null)
  const isAuthenticated = ref(false)
  const loading = ref(false)

  // 计算属性：派生状态
  const userGreeting = computed(() => {
    return user.value ? `欢迎，${user.value.username}!` : '未登录'
  })

  // 操作：修改状态的方法
  const login = async (username, password) => {
    loading.value = true
    try {
      // 调用 API 进行登录
      const response = await fetch('/api/auth/login', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ username, password })
      })

      if (!response.ok) throw new Error('登录失败')

      const data = await response.json()
      user.value = data.user
      isAuthenticated.value = true
      localStorage.setItem('token', data.token)
    } finally {
      loading.value = false
    }
  }

  const logout = () => {
    user.value = null
    isAuthenticated.value = false
    localStorage.removeItem('token')
  }

  const updateProfile = async (newData) => {
    try {
      const response = await fetch('/api/user/profile', {
        method: 'PUT',
        headers: {
          'Content-Type': 'application/json',
          'Authorization': `Bearer ${localStorage.getItem('token')}`
        },
        body: JSON.stringify(newData)
      })

      if (!response.ok) throw new Error('更新失败')

      const updated = await response.json()
      user.value = updated
    } catch (error) {
      console.error(error)
      throw error
    }
  }

  return {
    user,
    isAuthenticated,
    loading,
    userGreeting,
    login,
    logout,
    updateProfile
  }
})

// 在组件中使用 store
import { useUserStore } from '@/stores/user'

export default {
  setup() {
    const userStore = useUserStore()

    const handleLogin = async () => {
      await userStore.login('username', 'password')
    }

    return {
      userStore,
      handleLogin
    }
  }
}
```

## 深入后端开发

### Node.js 与 Express

Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行时，使用 Express 可以快速构建 Web 服务器。

#### 基础服务器

```javascript
const express = require('express')
const app = express()

app.use(express.json())

// 中间件
app.use((req, res, next) => {
  console.log(`${req.method} ${req.path}`)
  next()
})

// 路由
app.get('/api/users', (req, res) => {
  res.json({ users: [] })
})

app.post('/api/users', (req, res) => {
  const user = req.body
  // 保存用户
  res.status(201).json(user)
})

// 错误处理
app.use((err, req, res, next) => {
  console.error(err.stack)
  res.status(500).json({ error: err.message })
})

app.listen(3000, () => {
  console.log('服务器运行在 3000 端口')
})
```

#### 异步处理与中间件

```javascript
// 异步路由处理
app.get('/api/data', async (req, res, next) => {
  try {
    const data = await fetchData()
    res.json(data)
  } catch (error) {
    next(error)
  }
})

// 自定义中间件
const authenticate = (req, res, next) => {
  const token = req.headers.authorization
  if (!token) {
    return res.status(401).json({ error: 'Unauthorized' })
  }
  try {
    const decoded = verifyToken(token)
    req.user = decoded
    next()
  } catch (error) {
    res.status(403).json({ error: 'Invalid token' })
  }
}

app.get('/api/protected', authenticate, (req, res) => {
  res.json({ user: req.user })
})
```

### 数据库设计

#### 关系型数据库设计原则

1. **第一范式（1NF）**：所有字段都是原子值
2. **第二范式（2NF）**：在 1NF 基础上，非主键属性完全依赖于主键
3. **第三范式（3NF）**：在 2NF 基础上，非主键属性之间没有依赖关系

#### 数据库设计示例

```sql
-- 用户表
CREATE TABLE users (
  id INT PRIMARY KEY AUTO_INCREMENT,
  username VARCHAR(50) UNIQUE NOT NULL,
  email VARCHAR(100) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

-- 文章表
CREATE TABLE articles (
  id INT PRIMARY KEY AUTO_INCREMENT,
  user_id INT NOT NULL,
  title VARCHAR(200) NOT NULL,
  content LONGTEXT NOT NULL,
  status ENUM('draft', 'published', 'archived') DEFAULT 'draft',
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE,
  INDEX (user_id),
  INDEX (status)
);

-- 评论表
CREATE TABLE comments (
  id INT PRIMARY KEY AUTO_INCREMENT,
  article_id INT NOT NULL,
  user_id INT NOT NULL,
  content TEXT NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (article_id) REFERENCES articles(id) ON DELETE CASCADE,
  FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE,
  INDEX (article_id),
  INDEX (user_id)
);
```

#### ORM 使用 - Sequelize

```javascript
const { DataTypes } = require('sequelize')
const sequelize = require('./database')

const User = sequelize.define('User', {
  username: {
    type: DataTypes.STRING,
    allowNull: false,
    unique: true
  },
  email: {
    type: DataTypes.STRING,
    allowNull: false,
    unique: true,
    validate: {
      isEmail: true
    }
  },
  password: {
    type: DataTypes.STRING,
    allowNull: false
  }
})

const Article = sequelize.define('Article', {
  title: {
    type: DataTypes.STRING,
    allowNull: false
  },
  content: {
    type: DataTypes.TEXT,
    allowNull: false
  },
  status: {
    type: DataTypes.ENUM('draft', 'published'),
    defaultValue: 'draft'
  }
})

// 关联关系
User.hasMany(Article, { foreignKey: 'userId' })
Article.belongsTo(User, { foreignKey: 'userId' })
```

## 深入后端开发

### Node.js 与 Express 框架

Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行时，允许在服务器端运行 JavaScript。Express 是 Node.js 最流行的 Web 框架，提供了简洁的 API 用于构建 Web 应用。

#### Express 基础应用

```javascript
// 这是一个基础的 Express 应用示例
const express = require('express')
const cors = require('cors')
const bodyParser = require('body-parser')
const app = express()

// 中间件配置：在请求到达路由前处理

// CORS：允许跨域请求
app.use(cors({
  origin: 'http://localhost:3000',  // 允许的源
  credentials: true                   // 允许发送凭证
}))

// 解析 JSON 请求体
app.use(express.json())

// 解析 URL 编码的请求体
app.use(express.urlencoded({ extended: true }))

// 日志中间件：记录每个请求
app.use((req, res, next) => {
  console.log(`${new Date().toISOString()} - ${req.method} ${req.path}`)
  next()
})

// 自定义中间件：例如验证用户身份
const authenticate = (req, res, next) => {
  const token = req.headers.authorization?.split(' ')[1]
  
  if (!token) {
    return res.status(401).json({ error: 'No token provided' })
  }
  
  try {
    // 这里应该验证 token（例如 JWT）
    const decoded = verifyJWT(token)
    req.user = decoded  // 将用户信息添加到请求对象
    next()
  } catch (error) {
    res.status(403).json({ error: 'Invalid token' })
  }
}

// 路由处理

// GET 请求：获取资源
app.get('/api/users', (req, res) => {
  // 这里通常会从数据库查询用户列表
  const users = [
    { id: 1, name: '张三', email: 'zhang@example.com' },
    { id: 2, name: '李四', email: 'li@example.com' }
  ]
  res.json({ success: true, data: users })
})

// GET 请求带路径参数：获取单个用户
app.get('/api/users/:id', (req, res) => {
  const userId = req.params.id
  // 查询特定用户
  res.json({ id: userId, name: '用户名' })
})

// POST 请求：创建新资源
app.post('/api/users', authenticate, (req, res) => {
  const { name, email } = req.body
  
  // 验证请求体
  if (!name || !email) {
    return res.status(400).json({ error: 'Name and email are required' })
  }
  
  // 这里通常会保存到数据库
  const newUser = {
    id: Date.now(),
    name,
    email,
    createdAt: new Date()
  }
  
  res.status(201).json({ success: true, data: newUser })
})

// PUT 请求：更新整个资源
app.put('/api/users/:id', authenticate, (req, res) => {
  const userId = req.params.id
  const { name, email } = req.body
  
  // 更新逻辑
  const updatedUser = { id: userId, name, email }
  res.json({ success: true, data: updatedUser })
})

// PATCH 请求：部分更新资源
app.patch('/api/users/:id', authenticate, (req, res) => {
  const userId = req.params.id
  // 只更新提供的字段
  res.json({ success: true, data: {} })
})

// DELETE 请求：删除资源
app.delete('/api/users/:id', authenticate, (req, res) => {
  const userId = req.params.id
  // 删除用户
  res.status(204).send()  // 204 No Content
})

// 查询字符串处理：获取过滤、排序、分页参数
app.get('/api/products', (req, res) => {
  const { page = 1, limit = 10, sort = 'name', category } = req.query
  // page: 页码，limit: 每页数量，sort: 排序字段，category: 分类过滤
  res.json({
    page: parseInt(page),
    limit: parseInt(limit),
    sort,
    category
  })
})

// 错误处理中间件：必须放在路由之后
app.use((err, req, res, next) => {
  console.error(err.stack)
  
  // 区分不同类型的错误
  if (err.name === 'ValidationError') {
    return res.status(400).json({ error: err.message })
  }
  
  if (err.name === 'UnauthorizedError') {
    return res.status(401).json({ error: 'Unauthorized' })
  }
  
  // 通用错误响应
  res.status(500).json({ error: 'Internal server error' })
})

// 404 处理
app.use((req, res) => {
  res.status(404).json({ error: 'Route not found' })
})

// 启动服务器
const PORT = process.env.PORT || 3000
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`)
})
```

#### 异步编程和高级特性

```javascript
// 异步路由处理：使用 async/await

app.get('/api/posts', async (req, res, next) => {
  try {
    // 从数据库查询文章
    const posts = await Post.find()
    res.json({ success: true, data: posts })
  } catch (error) {
    // 传递给错误处理中间件
    next(error)
  }
})

// 串行和并行 Promise
app.get('/api/user/:id/full', async (req, res, next) => {
  try {
    const userId = req.params.id
    
    // 串行执行：第二个操作等待第一个完成
    const user = await User.findById(userId)
    const posts = await Post.find({ userId })
    const comments = await Comment.find({ userId })
    
    // 并行执行：同时发起多个请求
    const [orders, preferences] = await Promise.all([
      Order.find({ userId }),
      Preferences.findOne({ userId })
    ])
    
    res.json({
      user,
      posts,
      comments,
      orders,
      preferences
    })
  } catch (error) {
    next(error)
  }
})

// 文件上传处理
const multer = require('multer')

const upload = multer({
  dest: 'uploads/',
  limits: { fileSize: 5 * 1024 * 1024 },  // 5MB 限制
  fileFilter: (req, file, cb) => {
    // 只允许特定的文件类型
    if (file.mimetype.startsWith('image/')) {
      cb(null, true)
    } else {
      cb(new Error('Only images are allowed'))
    }
  }
})

app.post('/api/upload', upload.single('file'), (req, res) => {
  res.json({
    filename: req.file.filename,
    size: req.file.size
  })
})
```

### 数据库操作详解

#### SQL 数据库设计和查询

```sql
-- 创建用户表
CREATE TABLE users (
  id INT PRIMARY KEY AUTO_INCREMENT,
  username VARCHAR(50) UNIQUE NOT NULL,
  email VARCHAR(100) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  full_name VARCHAR(100),
  avatar_url VARCHAR(255),
  bio TEXT,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

-- 创建文章表
CREATE TABLE articles (
  id INT PRIMARY KEY AUTO_INCREMENT,
  user_id INT NOT NULL,
  title VARCHAR(200) NOT NULL,
  content LONGTEXT NOT NULL,
  description VARCHAR(500),
  status ENUM('draft', 'published', 'archived') DEFAULT 'draft',
  view_count INT DEFAULT 0,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE,
  INDEX idx_user_id (user_id),
  INDEX idx_status (status),
  INDEX idx_created_at (created_at)
);

-- 创建评论表
CREATE TABLE comments (
  id INT PRIMARY KEY AUTO_INCREMENT,
  article_id INT NOT NULL,
  user_id INT NOT NULL,
  parent_id INT,  -- 用于嵌套评论
  content TEXT NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  FOREIGN KEY (article_id) REFERENCES articles(id) ON DELETE CASCADE,
  FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE,
  FOREIGN KEY (parent_id) REFERENCES comments(id) ON DELETE CASCADE,
  INDEX idx_article_id (article_id),
  INDEX idx_user_id (user_id)
);

-- 创建标签表
CREATE TABLE tags (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(50) UNIQUE NOT NULL,
  description VARCHAR(255)
);

-- 文章和标签的多对多关联表
CREATE TABLE article_tags (
  article_id INT NOT NULL,
  tag_id INT NOT NULL,
  PRIMARY KEY (article_id, tag_id),
  FOREIGN KEY (article_id) REFERENCES articles(id) ON DELETE CASCADE,
  FOREIGN KEY (tag_id) REFERENCES tags(id) ON DELETE CASCADE
);

-- 查询优化：常用查询

-- 查询：获取所有已发布的文章及其作者信息
SELECT a.id, a.title, a.description, a.view_count, 
       u.id as author_id, u.username, u.avatar_url,
       COUNT(c.id) as comment_count
FROM articles a
JOIN users u ON a.user_id = u.id
LEFT JOIN comments c ON a.id = c.article_id
WHERE a.status = 'published'
GROUP BY a.id
ORDER BY a.created_at DESC
LIMIT 10;

-- 查询：获取用户的所有文章及其标签
SELECT a.id, a.title, GROUP_CONCAT(t.name) as tags
FROM articles a
LEFT JOIN article_tags at ON a.id = at.article_id
LEFT JOIN tags t ON at.tag_id = t.id
WHERE a.user_id = 1
GROUP BY a.id;

-- 查询：获取最受欢迎的文章
SELECT a.id, a.title, COUNT(c.id) as comment_count
FROM articles a
LEFT JOIN comments c ON a.id = c.article_id
GROUP BY a.id
ORDER BY a.view_count DESC, comment_count DESC
LIMIT 5;

-- 更新：增加文章浏览次数
UPDATE articles SET view_count = view_count + 1 WHERE id = 1;

-- 删除：删除一个月前的草稿
DELETE FROM articles 
WHERE status = 'draft' AND created_at < DATE_SUB(NOW(), INTERVAL 1 MONTH);
```

#### ORM 框架 - Sequelize

```javascript
// Sequelize 是 Node.js 的 ORM 框架，提供了面向对象的数据库操作方式

const { Sequelize, DataTypes } = require('sequelize')

// 创建数据库连接
const sequelize = new Sequelize('database_name', 'username', 'password', {
  host: 'localhost',
  dialect: 'mysql'
})

// 定义 User 模型
const User = sequelize.define('User', {
  id: {
    type: DataTypes.INTEGER,
    primaryKey: true,
    autoIncrement: true
  },
  username: {
    type: DataTypes.STRING,
    allowNull: false,
    unique: true,
    validate: {
      len: [3, 50]  // 用户名长度 3-50
    }
  },
  email: {
    type: DataTypes.STRING,
    allowNull: false,
    unique: true,
    validate: {
      isEmail: true  // 验证邮箱格式
    }
  },
  password: {
    type: DataTypes.STRING,
    allowNull: false
  },
  fullName: {
    type: DataTypes.STRING
  }
}, {
  tableName: 'users',
  timestamps: true,  // 自动添加 createdAt 和 updatedAt
  underscored: true  // 使用蛇形命名（created_at）而不是驼峰命名
})

// 定义 Article 模型
const Article = sequelize.define('Article', {
  id: {
    type: DataTypes.INTEGER,
    primaryKey: true,
    autoIncrement: true
  },
  title: {
    type: DataTypes.STRING,
    allowNull: false
  },
  content: {
    type: DataTypes.TEXT,
    allowNull: false
  },
  status: {
    type: DataTypes.ENUM('draft', 'published', 'archived'),
    defaultValue: 'draft'
  }
}, {
  tableName: 'articles',
  timestamps: true
})

// 定义关联关系
User.hasMany(Article, {
  foreignKey: 'userId'
})

Article.belongsTo(User, {
  foreignKey: 'userId'
})

// 数据库操作示例

// 创建用户
const createUser = async () => {
  try {
    const user = await User.create({
      username: 'john',
      email: 'john@example.com',
      password: 'hashedPassword'
    })
    console.log('User created:', user.toJSON())
  } catch (error) {
    console.error('Error creating user:', error.message)
  }
}

// 查询用户
const findUser = async () => {
  try {
    // 查询单个用户
    const user = await User.findByPk(1)
    
    // 查询多个用户
    const users = await User.findAll({
      where: { status: 'active' },
      limit: 10,
      offset: 0,
      order: [['createdAt', 'DESC']]
    })
    
    // 带关联的查询
    const userWithArticles = await User.findByPk(1, {
      include: [{
        model: Article,
        as: 'Articles',
        where: { status: 'published' },
        required: false  // LEFT JOIN，而不是 INNER JOIN
      }]
    })
    
    console.log('User with articles:', userWithArticles)
  } catch (error) {
    console.error('Error fetching user:', error.message)
  }
}

// 更新用户
const updateUser = async () => {
  try {
    const user = await User.findByPk(1)
    
    if (user) {
      user.fullName = 'John Doe'
      user.email = 'newemail@example.com'
      await user.save()
      console.log('User updated')
    }
  } catch (error) {
    console.error('Error updating user:', error.message)
  }
}

// 删除用户
const deleteUser = async () => {
  try {
    const deleted = await User.destroy({
      where: { id: 1 }
    })
    console.log(`${deleted} user(s) deleted`)
  } catch (error) {
    console.error('Error deleting user:', error.message)
  }
}

// 事务处理：确保多个操作的一致性
const transferArticles = async (fromUserId, toUserId) => {
  const transaction = await sequelize.transaction()
  
  try {
    // 在事务中执行多个操作
    const articles = await Article.findAll({
      where: { userId: fromUserId },
      transaction
    })
    
    for (let article of articles) {
      article.userId = toUserId
      await article.save({ transaction })
    }
    
    // 如果一切顺利，提交事务
    await transaction.commit()
    console.log('Articles transferred successfully')
  } catch (error) {
    // 如果发生错误，回滚事务
    await transaction.rollback()
    console.error('Transfer failed:', error.message)
  }
}

// 批量操作
const bulkCreateUsers = async () => {
  try {
    const users = await User.bulkCreate([
      { username: 'user1', email: 'user1@example.com', password: 'pass' },
      { username: 'user2', email: 'user2@example.com', password: 'pass' },
      { username: 'user3', email: 'user3@example.com', password: 'pass' }
    ])
    console.log(`${users.length} users created`)
  } catch (error) {
    console.error('Error bulk creating users:', error.message)
  }
}
```

### RESTful API 设计最佳实践

#### API 设计原则

1. **使用 HTTP 方法表示操作**：
   - GET：获取资源
   - POST：创建资源
   - PUT：更新整个资源
   - PATCH：部分更新资源
   - DELETE：删除资源

2. **使用 HTTP 状态码**：
   - 2xx：成功（200、201、204）
   - 3xx：重定向（301、302、304）
   - 4xx：客户端错误（400、401、404）
   - 5xx：服务器错误（500、502、503）

#### 完整的 CRUD 示例

```javascript
// 获取所有文章（带分页）
app.get('/api/articles', async (req, res) => {
  const { page = 1, limit = 10 } = req.query
  const offset = (page - 1) * limit
  
  try {
    const { count, rows } = await Article.findAndCountAll({
      offset,
      limit: parseInt(limit),
      order: [['createdAt', 'DESC']]
    })
    
    res.json({
      data: rows,
      total: count,
      page: parseInt(page),
      pages: Math.ceil(count / limit)
    })
  } catch (error) {
    res.status(500).json({ error: error.message })
  }
})

// 获取单个文章
app.get('/api/articles/:id', async (req, res) => {
  try {
    const article = await Article.findByPk(req.params.id, {
      include: [
        { model: User, attributes: ['id', 'username'] },
        { model: Comment, include: [{ model: User, attributes: ['username'] }] }
      ]
    })
    
    if (!article) {
      return res.status(404).json({ error: 'Article not found' })
    }
    
    res.json(article)
  } catch (error) {
    res.status(500).json({ error: error.message })
  }
})

// 创建文章
app.post('/api/articles', authenticate, async (req, res) => {
  const { title, content } = req.body
  
  if (!title || !content) {
    return res.status(400).json({ error: 'Title and content are required' })
  }
  
  try {
    const article = await Article.create({
      title,
      content,
      userId: req.user.id
    })
    
    res.status(201).json(article)
  } catch (error) {
    res.status(500).json({ error: error.message })
  }
})

// 更新文章
app.put('/api/articles/:id', authenticate, async (req, res) => {
  try {
    const article = await Article.findByPk(req.params.id)
    
    if (!article) {
      return res.status(404).json({ error: 'Article not found' })
    }
    
    if (article.userId !== req.user.id) {
      return res.status(403).json({ error: 'Forbidden' })
    }
    
    const { title, content, status } = req.body
    
    if (title) article.title = title
    if (content) article.content = content
    if (status) article.status = status
    
    await article.save()
    res.json(article)
  } catch (error) {
    res.status(500).json({ error: error.message })
  }
})

// 删除文章
app.delete('/api/articles/:id', authenticate, async (req, res) => {
  try {
    const article = await Article.findByPk(req.params.id)
    
    if (!article) {
      return res.status(404).json({ error: 'Article not found' })
    }
    
    if (article.userId !== req.user.id) {
      return res.status(403).json({ error: 'Forbidden' })
    }
    
    await article.destroy()
    res.status(204).send()
  } catch (error) {
    res.status(500).json({ error: error.message })
  }
})
```

### RESTful API 设计最佳实践

#### API 设计原则

```
API 设计的核心原则：
1. 资源导向：API 应该围绕资源设计，而不是操作
   - 不好：/api/getUserInfo, /api/deleteUser
   - 好的：/api/users, DELETE /api/users/:id

2. 使用正确的 HTTP 方法：
   - GET：获取资源（幂等，无副作用）
   - POST：创建新资源
   - PUT：完全替换资源
   - PATCH：部分更新资源
   - DELETE：删除资源
   - HEAD：获取资源元数据（不返回响应体）

3. 版本控制：通过 URL 或 Header 指定 API 版本
   - URL 版本：/api/v1/users
   - Header 版本：Accept: application/vnd.myapi.v1+json

4. 状态码使用：
   - 2xx：成功
     - 200 OK：请求成功
     - 201 Created：创建成功
     - 204 No Content：删除成功，无返回内容
   - 3xx：重定向
     - 301 Moved Permanently：资源永久移动
     - 304 Not Modified：资源未修改
   - 4xx：客户端错误
     - 400 Bad Request：请求错误
     - 401 Unauthorized：未授权
     - 403 Forbidden：禁止访问
     - 404 Not Found：资源不存在
     - 422 Unprocessable Entity：验证失败
   - 5xx：服务器错误
     - 500 Internal Server Error：服务器错误
     - 503 Service Unavailable：服务不可用

5. 统一的响应格式：
   {
     "success": true,
     "code": 200,
     "message": "操作成功",
     "data": { ... },
     "timestamp": "2024-01-15T10:30:00Z"
   }

6. 错误响应格式：
   {
     "success": false,
     "code": 400,
     "message": "请求参数错误",
     "errors": [
       { "field": "email", "message": "邮箱格式不正确" }
     ]
   }
```

#### 完整的 CRUD API 实现

```javascript
// 完整的用户管理 API 示例
const express = require('express')
const router = express.Router()

// 验证中间件
const authenticate = (req, res, next) => {
  // 验证 token 逻辑
  next()
}

// 分页工具函数
const getPagination = (page = 1, limit = 10) => {
  const offset = (page - 1) * limit
  return { limit, offset }
}

// 错误处理包装器
const asyncHandler = (fn) => (req, res, next) => {
  Promise.resolve(fn(req, res, next)).catch(next)
}

// GET /api/v1/users - 获取用户列表（带分页、过滤、排序）
router.get('/users', asyncHandler(async (req, res) => {
  const { page = 1, limit = 10, search, sort = 'createdAt', order = 'DESC' } = req.query
  
  // 验证查询参数
  if (page < 1 || limit < 1 || limit > 100) {
    return res.status(400).json({
      success: false,
      message: 'Invalid pagination parameters'
    })
  }
  
  const { limit: queryLimit, offset } = getPagination(page, limit)
  
  // 构建查询条件
  const where = {}
  if (search) {
    where.username = { [Op.like]: `%${search}%` }
  }
  
  // 查询总数和数据
  const { count, rows } = await User.findAndCountAll({
    where,
    limit: queryLimit,
    offset,
    order: [[sort, order]],
    attributes: { exclude: ['password'] }  // 不返回密码字段
  })
  
  res.json({
    success: true,
    message: 'Users retrieved successfully',
    data: rows,
    pagination: {
      total: count,
      page: parseInt(page),
      limit: parseInt(limit),
      pages: Math.ceil(count / limit),
      hasNextPage: page * limit < count,
      hasPrevPage: page > 1
    },
    timestamp: new Date().toISOString()
  })
}))

// GET /api/v1/users/:id - 获取单个用户
router.get('/users/:id', asyncHandler(async (req, res) => {
  const { id } = req.params
  
  // 验证 ID 格式
  if (!Number.isInteger(parseInt(id))) {
    return res.status(400).json({
      success: false,
      message: 'Invalid user ID'
    })
  }
  
  const user = await User.findByPk(id, {
    include: [{
      model: Article,
      attributes: ['id', 'title', 'createdAt']
    }],
    attributes: { exclude: ['password'] }
  })
  
  if (!user) {
    return res.status(404).json({
      success: false,
      message: 'User not found'
    })
  }
  
  res.json({
    success: true,
    data: user
  })
}))

// POST /api/v1/users - 创建新用户
router.post('/users', asyncHandler(async (req, res) => {
  const { username, email, password } = req.body
  
  // 验证必需字段
  const errors = []
  if (!username) errors.push({ field: 'username', message: 'Username is required' })
  if (!email) errors.push({ field: 'email', message: 'Email is required' })
  if (!password) errors.push({ field: 'password', message: 'Password is required' })
  
  if (errors.length > 0) {
    return res.status(422).json({
      success: false,
      message: 'Validation failed',
      errors
    })
  }
  
  // 检查用户是否已存在
  const existingUser = await User.findOne({ where: { email } })
  if (existingUser) {
    return res.status(409).json({
      success: false,
      message: 'Email already in use'
    })
  }
  
  // 密码加密（实际应用中应使用 bcrypt）
  const hashedPassword = hashPassword(password)
  
  const user = await User.create({
    username,
    email,
    password: hashedPassword
  })
  
  res.status(201).json({
    success: true,
    message: 'User created successfully',
    data: {
      id: user.id,
      username: user.username,
      email: user.email
    }
  })
}))

// PUT /api/v1/users/:id - 完全替换用户
router.put('/users/:id', authenticate, asyncHandler(async (req, res) => {
  const { id } = req.params
  const { username, email, fullName } = req.body
  
  // 权限检查：用户只能更新自己的信息
  if (req.user.id !== parseInt(id)) {
    return res.status(403).json({
      success: false,
      message: 'Forbidden: Cannot update another user'
    })
  }
  
  const user = await User.findByPk(id)
  if (!user) {
    return res.status(404).json({
      success: false,
      message: 'User not found'
    })
  }
  
  // 更新所有字段
  user.username = username
  user.email = email
  user.fullName = fullName
  await user.save()
  
  res.json({
    success: true,
    message: 'User updated successfully',
    data: user
  })
}))

// PATCH /api/v1/users/:id - 部分更新用户
router.patch('/users/:id', authenticate, asyncHandler(async (req, res) => {
  const { id } = req.params
  const updates = req.body
  
  // 检查权限
  if (req.user.id !== parseInt(id)) {
    return res.status(403).json({
      success: false,
      message: 'Forbidden'
    })
  }
  
  const user = await User.findByPk(id)
  if (!user) {
    return res.status(404).json({
      success: false,
      message: 'User not found'
    })
  }
  
  // 只更新提供的字段
  const allowedFields = ['username', 'email', 'fullName']
  for (const field of allowedFields) {
    if (field in updates) {
      user[field] = updates[field]
    }
  }
  
  await user.save()
  
  res.json({
    success: true,
    message: 'User updated successfully',
    data: user
  })
}))

// DELETE /api/v1/users/:id - 删除用户
router.delete('/users/:id', authenticate, asyncHandler(async (req, res) => {
  const { id } = req.params
  
  // 权限检查
  if (req.user.id !== parseInt(id) && req.user.role !== 'admin') {
    return res.status(403).json({
      success: false,
      message: 'Forbidden'
    })
  }
  
  const user = await User.findByPk(id)
  if (!user) {
    return res.status(404).json({
      success: false,
      message: 'User not found'
    })
  }
  
  await user.destroy()
  
  // 204 No Content 表示成功删除且无返回内容
  res.status(204).send()
}))

module.exports = router
```

## 全栈开发流程

### 项目架构设计

一个典型的全栈应用包含以下几个部分：

```
project/
├── frontend/                 # 前端应用
│   ├── src/
│   │   ├── components/      # 可复用组件
│   │   ├── pages/           # 页面组件
│   │   ├── store/           # 状态管理
│   │   ├── api/             # API 请求层
│   │   ├── utils/           # 工具函数
│   │   ├── styles/          # 全局样式
│   │   └── main.js
│   ├── public/
│   ├── package.json
│   └── vite.config.js
├── backend/                  # 后端应用
│   ├── src/
│   │   ├── controllers/     # 控制器
│   │   ├── models/          # 数据模型
│   │   ├── routes/          # 路由
│   │   ├── middleware/      # 中间件
│   │   ├── utils/           # 工具函数
│   │   └── index.js
│   ├── config/              # 配置文件
│   ├── package.json
│   └── .env.example
├── docker-compose.yml       # Docker 容器编排
├── .gitignore
└── README.md
```

### 前后端通信

#### API 请求封装

```javascript
// frontend/src/api/request.js
import axios from 'axios'

const request = axios.create({
  baseURL: import.meta.env.VITE_API_URL || 'http://localhost:3000/api',
  timeout: 10000
})

// 请求拦截
request.interceptors.request.use(config => {
  const token = localStorage.getItem('token')
  if (token) {
    config.headers.Authorization = `Bearer ${token}`
  }
  return config
})

// 响应拦截
request.interceptors.response.use(
  response => response.data,
  error => {
    if (error.response?.status === 401) {
      // 处理未授权
      localStorage.removeItem('token')
      window.location.href = '/login'
    }
    return Promise.reject(error)
  }
)

export default request
```

#### API 服务层

```javascript
// frontend/src/api/articles.js
import request from './request'

export const articleApi = {
  // 获取文章列表
  getList(page = 1, limit = 10) {
    return request.get('/articles', {
      params: { page, limit }
    })
  },
  
  // 获取文章详情
  getDetail(id) {
    return request.get(`/articles/${id}`)
  },
  
  // 创建文章
  create(data) {
    return request.post('/articles', data)
  },
  
  // 更新文章
  update(id, data) {
    return request.put(`/articles/${id}`, data)
  },
  
  // 删除文章
  delete(id) {
    return request.delete(`/articles/${id}`)
  }
}
```

#### Vue 组件集成

```javascript
// frontend/src/pages/ArticleList.vue
<template>
  <div class="article-list">
    <div v-if="loading" class="loading">加载中...</div>
    <div v-else-if="error" class="error">{{ error }}</div>
    <div v-else>
      <div v-for="article in articles" :key="article.id" class="article-item">
        <h3>{{ article.title }}</h3>
        <p>{{ article.content.substring(0, 100) }}...</p>
        <router-link :to="`/articles/${article.id}`">阅读更多</router-link>
      </div>
      
      <!-- 分页 -->
      <div class="pagination">
        <button 
          v-if="page > 1" 
          @click="page--">上一页</button>
        <span>第 {{ page }} 页，共 {{ pages }} 页</span>
        <button 
          v-if="page < pages" 
          @click="page++">下一页</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, watch } from 'vue'
import { articleApi } from '@/api/articles'

const articles = ref([])
const loading = ref(false)
const error = ref(null)
const page = ref(1)
const pages = ref(0)
const limit = 10

const fetchArticles = async () => {
  loading.value = true
  error.value = null
  try {
    const response = await articleApi.getList(page.value, limit)
    articles.value = response.data
    pages.value = response.pages
  } catch (err) {
    error.value = err.message
  } finally {
    loading.value = false
  }
}

watch(() => page.value, () => {
  fetchArticles()
})

onMounted(() => {
  fetchArticles()
})
</script>

<style scoped>
.article-list {
  max-width: 800px;
  margin: 0 auto;
}

.article-item {
  padding: 20px;
  border: 1px solid #ddd;
  margin-bottom: 20px;
  border-radius: 4px;
}

.pagination {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-top: 20px;
}
</style>
```

## 性能优化实战

### 前端性能优化

#### 代码分割与懒加载

```javascript
// router/index.js
import { createRouter, createWebHistory } from 'vue-router'

const routes = [
  {
    path: '/',
    component: () => import('@/pages/Home.vue')
  },
  {
    path: '/articles',
    component: () => import('@/pages/ArticleList.vue')
  },
  {
    path: '/articles/:id',
    component: () => import('@/pages/ArticleDetail.vue')
  }
]

const router = createRouter({
  history: createWebHistory(),
  routes
})

export default router
```

#### 图片优化

```javascript
// 使用 Vite 内置的图片优化
import imageSrc from '@/assets/image.jpg?url'
import imageWebp from '@/assets/image.jpg?format=webp'

// 自适应图片
export function useResponsiveImage(basePath) {
  return {
    src: imageSrc,
    webp: imageWebp,
    alt: 'Optimized image'
  }
}
```

#### 缓存策略

```javascript
// 使用 HTTP 缓存头
// 后端配置
app.use(express.static('public', {
  maxAge: '1d',
  etag: false
}))

// 前端控制缓存
app.get('/api/static/:file', (req, res) => {
  res.set({
    'Cache-Control': 'public, max-age=31536000',
    'ETag': generateETag(file)
  })
  res.sendFile(file)
})
```

### 后端性能优化

#### 数据库查询优化

```javascript
// 使用索引
CREATE INDEX idx_user_email ON users(email);
CREATE INDEX idx_article_user_id ON articles(user_id);

// 使用 EXPLAIN 分析查询
EXPLAIN SELECT * FROM articles WHERE user_id = 1 AND status = 'published';

// 避免 N+1 查询问题
// 不好的做法
const articles = await Article.findAll()
for (let article of articles) {
  article.user = await User.findByPk(article.userId)
}

// 好的做法
const articles = await Article.findAll({
  include: [{ model: User }]
})
```

#### 缓存策略

```javascript
// 使用 Redis 缓存
const redis = require('redis')
const client = redis.createClient()

app.get('/api/articles/:id', async (req, res) => {
  const cacheKey = `article:${req.params.id}`
  
  // 尝试从缓存获取
  const cached = await client.get(cacheKey)
  if (cached) {
    return res.json(JSON.parse(cached))
  }
  
  // 从数据库获取
  const article = await Article.findByPk(req.params.id)
  
  // 存入缓存
  await client.set(cacheKey, JSON.stringify(article), { EX: 3600 })
  
  res.json(article)
})
```

## 安全最佳实践

### 认证与授权

```javascript
// JWT 认证
const jwt = require('jsonwebtoken')
const bcrypt = require('bcrypt')

const SECRET_KEY = process.env.JWT_SECRET

// 登录
app.post('/api/auth/login', async (req, res) => {
  const { username, password } = req.body
  
  try {
    const user = await User.findOne({ where: { username } })
    if (!user) {
      return res.status(401).json({ error: 'Invalid credentials' })
    }
    
    const isValidPassword = await bcrypt.compare(password, user.password)
    if (!isValidPassword) {
      return res.status(401).json({ error: 'Invalid credentials' })
    }
    
    const token = jwt.sign(
      { id: user.id, username: user.username },
      SECRET_KEY,
      { expiresIn: '24h' }
    )
    
    res.json({ token })
  } catch (error) {
    res.status(500).json({ error: error.message })
  }
})

// 验证 JWT
const verifyToken = (req, res, next) => {
  const token = req.headers.authorization?.split(' ')[1]
  
  if (!token) {
    return res.status(401).json({ error: 'No token provided' })
  }
  
  try {
    const decoded = jwt.verify(token, SECRET_KEY)
    req.user = decoded
    next()
  } catch (error) {
    res.status(403).json({ error: 'Invalid token' })
  }
}

app.get('/api/protected', verifyToken, (req, res) => {
  res.json({ user: req.user })
})
```

### SQL 注入防护

```javascript
// 使用参数化查询
const userId = req.params.id

// 不要这样做
const query = `SELECT * FROM users WHERE id = ${userId}`

// 应该这样做
const user = await sequelize.query(
  'SELECT * FROM users WHERE id = ?',
  { replacements: [userId] }
)

// 或使用 ORM
const user = await User.findByPk(userId)
```

### XSS 防护

```javascript
// 使用 xss 包防护
const xss = require('xss')

app.post('/api/comments', authenticate, (req, res) => {
  const { content } = req.body
  
  // 清理用户输入
  const cleanContent = xss(content, {
    whiteList: {},
    stripIgnoredTag: true
  })
  
  // 保存清理后的内容
})

// 前端也需要转义输出
// Vue 模板自动转义，但使用 v-html 时需要谨慎
<div>{{ userContent }}</div>  <!-- 安全 -->
<div v-html="userContent"></div>  <!-- 需要确保已清理 -->
```

## 常见问题

**Q: 应该先学前端还是后端？**
A: 可以同时学习，但建议先从前端开始。前端可以快速看到成果，这会增加学习动力。从 HTML、CSS、JavaScript 基础开始，然后学习框架。学习前端一段时间后，可以同时开始学习后端。

**Q: 如何快速入门 Web 开发？**
A: 选择一个简单的项目开始，比如待办事项应用或博客系统。边学边做，这样效率最高。建议遵循以下步骤：
1. 学习基础知识（HTML、CSS、JavaScript）
2. 选择一个前端框架（Vue 或 React）深入学习
3. 学习一个后端框架（Express 或 Django）
4. 结合前后端完成一个完整项目
5. 学习数据库和 SQL
6. 部署应用到云平台

**Q: 如何保持代码质量？**
A: 遵循以下实践：
1. 遵循代码规范（ESLint、Prettier）
2. 编写单元测试和集成测试
3. 定期重构代码，消除技术债务
4. 进行代码审查，与团队成员讨论
5. 使用版本控制系统（Git）
6. 编写清晰的注释和文档

**Q: 如何处理 CORS 跨域问题？**
A: CORS（跨域资源共享）在前后端分离的架构中很常见。解决方案：
```javascript
// 后端配置
const cors = require('cors')

app.use(cors({
  origin: 'http://localhost:3001',
  credentials: true,
  methods: ['GET', 'POST', 'PUT', 'DELETE'],
  allowedHeaders: ['Content-Type', 'Authorization']
}))
```

**Q: 如何进行前后端集成测试？**
A: 使用专业的测试工具：
- 单元测试：Jest、Vitest
- 集成测试：Supertest（后端）、Vue Test Utils（前端）
- E2E 测试：Cypress、Playwright
```javascript
// 使用 Supertest 测试 API
const request = require('supertest')
const app = require('@/app')

describe('Articles API', () => {
  it('should fetch all articles', async () => {
    const response = await request(app)
      .get('/api/articles')
      .expect(200)
    
    expect(response.body.data).toBeArray()
  })
})
```

**Q: 如何处理大量数据的性能问题？**
A: 
1. 使用分页而不是一次加载所有数据
2. 添加数据库索引优化查询
3. 使用缓存（Redis）减少数据库查询
4. 使用 CDN 加速静态资源加载
5. 前端使用虚拟滚动处理大列表
6. 后端使用消息队列处理耗时操作

---

加入我们，一起构建更好的 Web 应用！
