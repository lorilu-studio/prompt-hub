
# Claude生成一个三维可视化大屏

来源：https://ueqty4qqat.feishu.cn/wiki/UmgawxWw3iqVJukA3l6cqPTqnFh?continueFlag=fa28a2b7a7003ed5bb7e7e86847047eb

## 提示词

```
设计一个极地气象预报系统可视化大屏，请模拟用户来提出需求，请自己构思好功能和界面，然后设计 UI/UX，然后像下面那样给我所有的页面的 html ( html 示例如下)

```

```html

<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>FeastMeet - 酷酷年轻人的约饭神器</title>
  <style>
    :root {
      /* 主色调 */
      --primary: #8C52FF;
      --primary-dark: #6E3AD9;
      --primary-light: #A875FF;
      
      /* 霓虹色调 */
      --neon-pink: #FF2E93;
      --neon-blue: #00E9FF;
      --neon-green: #00FF85;
      --neon-yellow: #FFDE59;
      
      /* 暗色背景 */
      --bg-dark: #121212;
      --bg-card: #1E1E1E;
      --bg-card-hover: #252525;
      
      /* 文本颜色 */
      --text-primary: #FFFFFF;
      --text-secondary: rgba(255, 255, 255, 0.7);
      --text-tertiary: rgba(255, 255, 255, 0.5);
      --text-disabled: rgba(255, 255, 255, 0.3);
      
      /* 边框与阴影 */
      --border-light: rgba(255, 255, 255, 0.1);
      --shadow-card: 0 4px 20px rgba(0, 0, 0, 0.25);
      --shadow-neon: 0 0 15px rgba(140, 82, 255, 0.5);
      
      /* 间距 */
      --space-xs: 4px;
      --space-sm: 8px;
      --space-md: 16px;
      --space-lg: 24px;
      --space-xl: 32px;
      
      /* 圆角 */
      --radius-sm: 8px;
      --radius-md: 12px;
      --radius-lg: 20px;
      --radius-full: 9999px;
    }
    
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Outfit', 'SF Pro Display', -apple-system, BlinkMacSystemFont, sans-serif;
    }
    
    body {
      background-color: var(--bg-dark);
      color: var(--text-primary);
      line-height: 1.5;
      -webkit-font-smoothing: antialiased;
      padding: var(--space-md);
    }
    
    .app-container {
      display: flex;
      flex-wrap: wrap;
      gap: var(--space-xl);
      justify-content: center;
      padding-bottom: var(--space-xl);
    }
    
    .screen {
      width: 360px;
      height: 720px;
      background: var(--bg-dark);
      border-radius: var(--radius-lg);
      overflow: hidden;
      position: relative;
      box-shadow: var(--shadow-card);
      border: 1px solid var(--border-light);
    }
    
    .header {
      padding: var(--space-md) var(--space-md);
      display: flex;
      align-items: center;
      justify-content: space-between;
      position: relative;
      z-index: 10;
    }
    
    .header-title {
      font-size: 20px;
      font-weight: 600;
    }
    
    .header-action {
      display: flex;
      gap: var(--space-sm);
    }
    
    .icon-button {
      width: 40px;
      height: 40px;
      border-radius: var(--radius-full);
      display: flex;
      align-items: center;
      justify-content: center;
      background: rgba(255, 255, 255, 0.1);
      color: var(--text-primary);
      border: none;
      cursor: pointer;
      transition: all 0.2s ease;
    }
    
    .icon-button:hover, .icon-button:active {
      background: rgba(255, 255, 255, 0.2);
    }
    
    .content {
      height: calc(100% - 160px);
      overflow-y: auto;
      padding: 0 var(--space-md) var(--space-md);
    }
    
    .full-content {
      height: calc(100% - 80px);
      overflow-y: auto;
      padding: 0 var(--space-md) var(--space-md);
    }
    
    .nav-bar {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      height: 80px;
      background: var(--bg-card);
      display: flex;
      justify-content: space-around;
      align-items: center;
      border-top: 1px solid var(--border-light);
      padding: 0 var(--space-md);
    }
    
    .nav-item {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      color: var(--text-tertiary);
      text-decoration: none;
      font-size: 12px;
    }
    
    .nav-item.active {
      color: var(--primary);
    }
    
    .nav-icon {
      font-size: 24px;
      margin-bottom: var(--space-xs);
    }
    
    .card {
      background: var(--bg-card);
      border-radius: var(--radius-md);
      padding: var(--space-md);
      margin-bottom: var(--space-md);
      border: 1px solid var(--border-light);
      transition: all 0.2s ease;
    }
    
    .card:active {
      transform: scale(0.98);
      background: var(--bg-card-hover);
    }
    
    .feast-card {
      background: var(--bg-card);
      border-radius: var(--radius-md);
      margin-bottom: var(--space-md);
      overflow: hidden;
      position: relative;
      box-shadow: var(--shadow-card);
    }
    
    .feast-image {
      height: 150px;
      position: relative;
      overflow: hidden;
    }
    
    .feast-image-bg {
      width: 100%;
      height: 100%;
      background-position: center;
      background-size: cover;
      filter: brightness(0.7);
    }
    
    .feast-details {
      padding: var(--space-md);
    }
    
    .feast-meta {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: var(--space-sm);
    }
    
    .feast-date {
      font-size: 14px;
      color: var(--text-secondary);
      display: flex;
      align-items: center;
    }
    
    .feast-icon {
      margin-right: var(--space-xs);
    }
    
    .tags-container {
      display: flex;
      flex-wrap: wrap;
      gap: var(--space-xs);
      margin: var(--space-sm) 0;
    }
    
    .tag {
      background: rgba(255, 255, 255, 0.1);
      color: var(--text-secondary);
      padding: var(--space-xs) var(--space-sm);
      border-radius: var(--radius-full);
      font-size: 12px;
    }
    
    .tag.highlighted {
      background: var(--primary);
      color: white;
    }
    
    .button {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      padding: var(--space-md) var(--space-lg);
      border-radius: var(--radius-full);
      font-weight: 600;
      border: none;
      cursor: pointer;
      transition: all 0.2s ease;
    }
    
    .button.primary {
      background: var(--primary);
      color: white;
    }
    
    .button.primary:hover, .button.primary:active {
      background: var(--primary-dark);
    }
    
    .button.outline {
      background: transparent;
      border: 1px solid var(--primary);
      color: var(--primary);
    }
    
    .button.outline:hover, .button.outline:active {
      background: rgba(140, 82, 255, 0.1);
    }
    
    .button.full {
      width: 100%;
    }
    
    .button-icon {
      margin-right: var(--space-sm);
    }
    
    .gradient-text {
      background: linear-gradient(to right, var(--neon-pink), var(--primary));
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      font-weight: 700;
    }
    
    .section-title {
      font-size: 18px;
      font-weight: 600;
      margin: var(--space-lg) 0 var(--space-md);
      display: flex;
      align-items: center;
    }
    
    .avatar {
      width: 50px;
      height: 50px;
      border-radius: var(--radius-full);
      object-fit: cover;
    }
    
    .avatar.small {
      width: 36px;
      height: 36px;
    }
    
    .avatar-group {
      display: flex;
      margin-left: var(--space-sm);
    }
    
    .avatar-group .avatar {
      margin-left: -10px;
      border: 2px solid var(--bg-card);
    }
    
    .avatar-group .avatar:first-child {
      margin-left: 0;
    }
    
    .users-more {
      width: 36px;
      height: 36px;
      border-radius: var(--radius-full);
      background: rgba(255, 255, 255, 0.1);
      color: white;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 12px;
      margin-left: -10px;
      border: 2px solid var(--bg-card);
    }
    
    .search-bar {
      display: flex;
      align-items: center;
      background: var(--bg-card);
      border-radius: var(--radius-full);
      padding: var(--space-sm) var(--space-md);
      margin-bottom: var(--space-md);
    }
    
    .search-icon {
      color: var(--text-tertiary);
      margin-right: var(--space-sm);
    }
    
    .search-input {
      background: transparent;
      border: none;
      color: var(--text-primary);
      flex: 1;
      font-size: 16px;
    }
    
    .search-input:focus {
      outline: none;
    }
    
    .categories {
      display: flex;
      overflow-x: auto;
      gap: var(--space-sm);
      padding: var(--space-xs) 0;
      margin-bottom: var(--space-md);
      scrollbar-width: none;
    }
    
    .categories::-webkit-scrollbar {
      display: none;
    }
    
    .category-item {
      padding: var(--space-sm) var(--space-md);
      background: var(--bg-card);
      border-radius: var(--radius-full);
      white-space: nowrap;
      color: var(--text-secondary);
    }
    
    .category-item.active {
      background: var(--primary);
      color: white;
    }
    
    .form-group {
      margin-bottom: var(--space-lg);
    }
    
    .form-label {
      display: block;
      margin-bottom: var(--space-sm);
      color: var(--text-secondary);
      font-weight: 500;
    }
    
    .form-input {
      width: 100%;
      padding: var(--space-md);
      background: var(--bg-card);
      border: 1px solid var(--border-light);
      border-radius: var(--radius-md);
      color: var(--text-primary);
      font-size: 16px;
    }
    
    .form-input:focus {
      outline: none;
      border-color: var(--primary);
    }
    
    textarea.form-input {
      min-height: 100px;
      resize: vertical;
    }
    
    .form-select {
      width: 100%;
      padding: var(--space-md);
      background: var(--bg-card);
      border: 1px solid var(--border-light);
      border-radius: var(--radius-md);
      color: var(--text-primary);
      font-size: 16px;
      appearance: none;
      background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='white' width='18px' height='18px'%3E%3Cpath d='M7 10l5 5 5-5z'/%3E%3C/svg%3E");
      background-repeat: no-repeat;
      background-position: right var(--space-md) center;
    }
    
    .form-select:focus {
      outline: none;
      border-color: var(--primary);
    }
    
    .chat-message {
      display: flex;
      margin-bottom: var(--space-md);
    }
    
    .chat-message.outgoing {
      flex-direction: row-reverse;
    }
    
    .message-avatar {
      width: 40px;
      height: 40px;
      border-radius: var(--radius-full);
      margin-right: var(--space-sm);
    }
    
    .chat-message.outgoing .message-avatar {
      margin-right: 0;
      margin-left: var(--space-sm);
    }
    
    .message-content {
      max-width: 70%;
    }
    
    .message-bubble {
      background: var(--bg-card);
      padding: var(--space-md);
      border-radius: var(--radius-md);
      margin-bottom: var(--space-xs);
    }
    
    .chat-message.outgoing .message-bubble {
      background: var(--primary);
    }
    
    .message-time {
      font-size: 12px;
      color: var(--text-tertiary);
      text-align: right;
    }
    
    .chat-input-container {
      position: fixed;
      bottom: 0;
      left: 0;
      right: 0;
      padding: var(--space-md);
      background: var(--bg-dark);
      border-top: 1px solid var(--border-light);
      display: flex;
      align-items: center;
    }
    
    .chat-input {
      flex: 1;
      padding: var(--space-md);
      background: var(--bg-card);
      border: none;
      border-radius: var(--radius-full);
      color: var(--text-primary);
      margin-right: var(--space-sm);
    }
    
    .chat-input:focus {
      outline: none;
    }
    
    .pulse {
      display: inline-block;
      width: 10px;
      height: 10px;
      border-radius: var(--radius-full);
      background: var(--neon-green);
      margin-right: var(--space-sm);
      animation: pulse 1.5s infinite;
    }
    
    @keyframes pulse {
      0% {
        transform: scale(0.95);
        box-shadow: 0 0 0 0 rgba(0, 255, 133, 0.5);
      }
      70% {
        transform: scale(1);
        box-shadow: 0 0 0 10px rgba(0, 255, 133, 0);
      }
      100% {
        transform: scale(0.95);
        box-shadow: 0 0 0 0 rgba(0, 255, 133, 0);
      }
    }
    
    .profile-header {
      background: linear-gradient(to right, var(--neon-blue), var(--primary));
      padding: var(--space-xl) var(--space-md) var(--space-lg);
      margin: -16px -16px 0;
      text-align: center;
      position: relative;
    }
    
    .profile-avatar {
      width: 100px;
      height: 100px;
      border-radius: var(--radius-full);
      border: 3px solid white;
      margin-bottom: var(--space-sm);
    }
    
    .profile-stats {
      display: flex;
      justify-content: space-around;
      margin: var(--space-md) 0;
    }
    
    .stat-item {
      text-align: center;
    }
    
    .stat-value {
      font-size: 24px;
      font-weight: 700;
    }
    
    .stat-label {
      font-size: 12px;
      color: var(--text-tertiary);
    }
    
    .login-logo {
      font-size: 36px;
      font-weight: 800;
      text-align: center;
      margin: var(--space-xl) 0;
    }
    
    .social-login {
      display: flex;
      justify-content: center;
      gap: var(--space-md);
      margin: var(--space-xl) 0;
    }
    
    .social-icon {
      width: 50px;
      height: 50px;
      background: var(--bg-card);
      border-radius: var(--radius-full);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 24px;
      color: var(--text-primary);
    }
    
    .divider {
      display: flex;
      align-items: center;
      color: var(--text-tertiary);
      margin: var(--space-xl) 0;
    }
    
    .divider:before, .divider:after {
      content: "";
      flex: 1;
      height: 1px;
      background: var(--border-light);
    }
    
    .divider:before {
      margin-right: var(--space-md);
    }
    
    .divider:after {
      margin-left: var(--space-md);
    }
    
    .create-feast-fab {
      position: absolute;
      bottom: 100px;
      right: var(--space-md);
      width: 60px;
      height: 60px;
      border-radius: var(--radius-full);
      background: var(--primary);
      color: white;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: var(--shadow-neon);
      border: none;
      font-size: 24px;
      z-index: 100;
    }
    
    /* Material Icons */
    .material-icons {
      font-family: 'Material Icons';
      font-weight: normal;
      font-style: normal;
      font-size: 24px;  /* Preferred icon size */
      display: inline-block;
      line-height: 1;
      text-transform: none;
      letter-spacing: normal;
      word-wrap: normal;
      white-space: nowrap;
      direction: ltr;
      -webkit-font-smoothing: antialiased;
      text-rendering: optimizeLegibility;
    }
  </style>
  <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
  <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@400;500;600;700;800&display=swap" rel="stylesheet">
</head>
<body>

<div class="app-container">

  <!-- 启动/登录页 -->
  <div class="screen" id="login">
    <div class="full-content">
      <div style="height: 30%"></div>
      
      <div class="login-logo">
        <span class="gradient-text">FeastMeet</span>
        <div style="font-size: 16px; color: var(--text-secondary); font-weight: normal; margin-top: 8px;">美食相遇，灵魂碰撞</div>
      </div>
      
      <div class="social-login">
        <a href="#home" class="social-icon">
          <span class="material-icons">alternate_email</span>
        </a>
        <a href="#home" class="social-icon">
          <span class="material-icons">chat</span>
        </a>
        <a href="#home" class="social-icon">
          <span class="material-icons">language</span>
        </a>
      </div>
      
      <div class="divider">或使用邮箱登录</div>
      
      <div class="form-group">
        <input type="email" class="form-input" placeholder="邮箱地址">
      </div>
      
      <div class="form-group">
        <input type="password" class="form-input" placeholder="密码">
      </div>
      
      <a href="#home" class="button primary full" style="margin-bottom: var(--space-md);">登录</a>
      <a href="#home" class="button outline full">注册新账号</a>
      
      <div style="text-align: center; margin-top: var(--space-xl); color: var(--text-tertiary);">
        登录即表示您同意我们的<br>
        <a href="#" style="color: var(--primary);">服务条款</a> 和 <a href="#" style="color: var(--primary);">隐私政策</a>
      </div>
    </div>
  </div>
  
  <!-- 主页/发现页 -->
  <div class="screen" id="home">
    <div class="header">
      <div class="header-title">探索饭局</div>
      <div class="header-action">
        <button class="icon-button">
          <span class="material-icons">notifications</span>
        </button>
        <button class="icon-button">
          <span class="material-icons">tune</span>
        </button>
      </div>
    </div>
    
    <div class="content">
      <div class="search-bar">
        <span class="material-icons search-icon">search</span>
        <input type="text" class="search-input" placeholder="搜索饭局、餐厅或美食...">
      </div>
      
      <div class="categories">
        <div class="category-item active">推荐</div>
        <div class="category-item">新奇体验</div>
        <div class="category-item">职场社交</div>
        <div class="category-item">音乐爱好者</div>
        <div class="category-item">电影交流</div>
        <div class="category-item">艺术文化</div>
      </div>
      
      <a href="#feast-detail" class="feast-card">
        <div class="feast-image">
          <div class="feast-image-bg" style="background-image: url('https://images.unsplash.com/photo-1555396273-367ea4eb4db5?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1074&q=80');"></div>
          <div style="position: absolute; top: var(--space-md); right: var(--space-md); background: rgba(0,0,0,0.6); padding: var(--space-xs) var(--space-sm); border-radius: var(--radius-full); font-size: 12px; color: white;">
            <span class="material-icons" style="font-size: 14px; vertical-align: middle; margin-right: 2px;">person</span> 3/6
          </div>
        </div>
        <div class="feast-details">
          <h3>创意料理夜 @ 深蓝餐厅</h3>
          <div class="feast-meta">
            <div class="feast-date">
              <span class="material-icons feast-icon">event</span>
              今晚 19:30
            </div>
            <div class="feast-date">
              <span class="material-icons feast-icon">location_on</span>
              1.2km
            </div>
          </div>
          <p style="color: var(--text-secondary); margin-bottom: var(--space-sm);">分享对创意料理的热爱，探讨未来美食趋势，交流味蕾体验。</p>
          <div class="tags-container">
            <span class="tag highlighted">美食探索</span>
                        <span class="tag">创意料理</span>
            <span class="tag">社交晚餐</span>
          </div>
          <div style="display: flex; align-items: center; margin-top: var(--space-md); justify-content: space-between;">
            <div style="display: flex; align-items: center;">
              <img src="https://randomuser.me/api/portraits/men/32.jpg" class="avatar small">
              <div style="margin-left: var(--space-sm); font-size: 14px;">
                <div>Alex Chen</div>
                <div style="color: var(--text-tertiary); font-size: 12px; display: flex; align-items: center;">
                  <span class="material-icons" style="font-size: 14px; margin-right: 2px;">star</span>
                  4.8
                </div>
              </div>
            </div>
            <div style="color: var(--neon-pink); font-weight: 600;">¥128/位</div>
          </div>
        </div>
      </a>
      
      <a href="#feast-detail" class="feast-card">
        <div class="feast-image">
          <div class="feast-image-bg" style="background-image: url('https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80');"></div>
          <div style="position: absolute; top: var(--space-md); right: var(--space-md); background: rgba(0,0,0,0.6); padding: var(--space-xs) var(--space-sm); border-radius: var(--radius-full); font-size: 12px; color: white;">
            <span class="material-icons" style="font-size: 14px; vertical-align: middle; margin-right: 2px;">person</span> 2/4
          </div>
        </div>
        <div class="feast-details">
          <h3>爵士乐与红酒之夜</h3>
          <div class="feast-meta">
            <div class="feast-date">
              <span class="material-icons feast-icon">event</span>
              明天 20:00
            </div>
            <div class="feast-date">
              <span class="material-icons feast-icon">location_on</span>
              3.5km
            </div>
          </div>
          <p style="color: var(--text-secondary); margin-bottom: var(--space-sm);">边听爵士乐边品红酒，聊聊音乐与艺术，结交志同道合的朋友。</p>
          <div class="tags-container">
            <span class="tag highlighted">音乐爱好者</span>
            <span class="tag">红酒</span>
            <span class="tag">爵士乐</span>
          </div>
          <div style="display: flex; align-items: center; margin-top: var(--space-md); justify-content: space-between;">
            <div style="display: flex; align-items: center;">
              <img src="https://randomuser.me/api/portraits/women/44.jpg" class="avatar small">
              <div style="margin-left: var(--space-sm); font-size: 14px;">
                <div>Sophia Lin</div>
                <div style="color: var(--text-tertiary); font-size: 12px; display: flex; align-items: center;">
                  <span class="material-icons" style="font-size: 14px; margin-right: 2px;">star</span>
                  4.9
                </div>
              </div>
            </div>
            <div style="color: var(--neon-pink); font-weight: 600;">¥168/位</div>
          </div>
        </div>
      </a>
      
      <a href="#feast-detail" class="feast-card">
        <div class="feast-image">
          <div class="feast-image-bg" style="background-image: url('https://images.unsplash.com/photo-1528605248644-14dd04022da1?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80');"></div>
          <div style="position: absolute; top: var(--space-md); right: var(--space-md); background: rgba(255,46,147,0.8); padding: var(--space-xs) var(--space-sm); border-radius: var(--radius-full); font-size: 12px; color: white;">
            火爆
          </div>
        </div>
        <div class="feast-details">
          <h3>科技创业者交流会 @ 云端咖啡</h3>
          <div class="feast-meta">
            <div class="feast-date">
              <span class="material-icons feast-icon">event</span>
              周六 13:00
            </div>
            <div class="feast-date">
              <span class="material-icons feast-icon">location_on</span>
              0.8km
            </div>
          </div>
          <p style="color: var(--text-secondary); margin-bottom: var(--space-sm);">轻松氛围中交流创业心得，寻找合作伙伴，碰撞创新火花。</p>
          <div class="tags-container">
            <span class="tag highlighted">职场社交</span>
            <span class="tag">创业</span>
            <span class="tag">科技</span>
          </div>
          <div style="display: flex; align-items: center; margin-top: var(--space-md); justify-content: space-between;">
            <div style="display: flex; align-items: center;">
              <div class="avatar-group">
                <img src="https://randomuser.me/api/portraits/men/85.jpg" class="avatar small">
                <img src="https://randomuser.me/api/portraits/women/79.jpg" class="avatar small">
                <div class="users-more">+3</div>
              </div>
              <div style="margin-left: var(--space-sm); font-size: 14px;">
                <div>多人主办</div>
              </div>
            </div>
            <div style="color: var(--neon-pink); font-weight: 600;">¥88/位</div>
          </div>
        </div>
      </a>
      
      <a href="#create-feast" class="create-feast-fab">
        <span class="material-icons">add</span>
      </a>
    </div>
    
    <div class="nav-bar">
      <a href="#home" class="nav-item active">
        <span class="material-icons nav-icon">explore</span>
        <span>发现</span>
      </a>
      <a href="#nearby" class="nav-item">
        <span class="material-icons nav-icon">map</span>
        <span>附近</span>
      </a>
      <a href="#messages" class="nav-item">
        <span class="material-icons nav-icon">chat</span>
        <span>消息</span>
      </a>
      <a href="#profile" class="nav-item">
        <span class="material-icons nav-icon">person</span>
        <span>我的</span>
      </a>
    </div>
  </div>

  <!-- 饭局详情页 -->
  <div class="screen" id="feast-detail">
    <div class="header">
      <button class="icon-button" onclick="window.location.href='#home'">
        <span class="material-icons">arrow_back</span>
      </button>
      <div class="header-title">饭局详情</div>
      <div class="header-action">
        <button class="icon-button">
          <span class="material-icons">share</span>
        </button>
      </div>
    </div>
    
    <div class="full-content">
      <div style="height: 200px; position: relative; margin: -16px -16px 16px;">
        <div style="position: absolute; inset: 0; background-image: url('https://images.unsplash.com/photo-1555396273-367ea4eb4db5?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1074&q=80'); background-size: cover; background-position: center;"></div>
        <div style="position: absolute; inset: 0; background: linear-gradient(to top, rgba(18,18,18,1) 0%, rgba(18,18,18,0) 100%);"></div>
      </div>
      
      <h2 style="margin-bottom: var(--space-sm);">创意料理夜 @ 深蓝餐厅</h2>
      
      <div class="feast-meta" style="margin-bottom: var(--space-md);">
        <div class="feast-date">
          <span class="material-icons feast-icon">event</span>
          今晚 19:30-21:30
        </div>
        <div class="feast-date">
          <span class="material-icons feast-icon">location_on</span>
          深蓝餐厅 · 1.2km
        </div>
      </div>
      
      <div class="card">
        <h4 style="margin-bottom: var(--space-sm);">关于这场饭局</h4>
        <p style="color: var(--text-secondary); line-height: 1.6;">分享对创意料理的热爱，探讨未来美食趋势，交流味蕾体验。今晚的主厨特别推出分子料理新菜单，我们将共同品尝并进行有趣的美食讨论。</p>
        <p style="color: var(--text-secondary); line-height: 1.6; margin-top: var(--space-sm);">适合喜欢尝试新事物、对料理有热情的朋友。席间将有轻松的交流环节，不用担心尴尬。</p>
        
        <div style="margin-top: var(--space-md);">
          <div class="tags-container">
            <span class="tag highlighted">美食探索</span>
            <span class="tag">创意料理</span>
            <span class="tag">社交晚餐</span>
            <span class="tag">分子料理</span>
          </div>
        </div>
      </div>
      
      <div class="card">
        <h4 style="margin-bottom: var(--space-md);">主办人</h4>
        <div style="display: flex; align-items: center;">
          <img src="https://randomuser.me/api/portraits/men/32.jpg" class="avatar">
          <div style="margin-left: var(--space-md);">
            <div style="font-weight: 500;">Alex Chen</div>
            <div style="color: var(--text-tertiary); font-size: 14px; margin-top: var(--space-xs);">美食博主 | 料理爱好者</div>
            <div style="display: flex; align-items: center; margin-top: var(--space-xs);">
              <span class="material-icons" style="font-size: 16px; color: var(--neon-yellow); margin-right: 2px;">star</span>
              <span>4.8</span>
              <span style="margin-left: var(--space-xs); color: var(--text-tertiary);">(已举办32场)</span>
            </div>
          </div>
        </div>
      </div>
      
      <div class="card">
        <h4 style="margin-bottom: var(--space-sm); display: flex; justify-content: space-between;">
          <span>已报名 (3/6)</span>
          <a href="#attendees" style="color: var(--primary); font-size: 14px; text-decoration: none;">查看全部 ></a>
        </h4>
        <div style="display: flex; margin-bottom: var(--space-md);">
          <img src="https://randomuser.me/api/portraits/women/33.jpg" class="avatar small" style="margin-right: var(--space-xs);">
          <img src="https://randomuser.me/api/portraits/men/54.jpg" class="avatar small" style="margin-right: var(--space-xs);">
          <img src="https://randomuser.me/api/portraits/women/68.jpg" class="avatar small" style="margin-right: var(--space-xs);">
          <div style="width: 36px; height: 36px; border-radius: var(--radius-full); border: 1px dashed var(--border-light); display: flex; align-items: center; justify-content: center;">
            <span class="material-icons" style="color: var(--text-tertiary);">add</span>
          </div>
        </div>
        
        <div style="color: var(--text-tertiary); font-size: 14px; margin-bottom: var(--space-md);">
          <span class="pulse"></span>
          刚刚有新朋友加入！
        </div>
      </div>
      
      <div class="card">
        <h4 style="margin-bottom: var(--space-md);">餐厅信息</h4>
        <div style="display: flex; margin-bottom: var(--space-md);">
          <div style="width: 80px; height: 80px; border-radius: var(--radius-sm); background-image: url('https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80'); background-size: cover; background-position: center;"></div>
          <div style="margin-left: var(--space-md);">
            <div style="font-weight: 500;">深蓝餐厅</div>
            <div style="color: var(--text-tertiary); font-size: 14px; margin-top: var(--space-xs);">创意西餐 | ¥¥¥</div>
            <div style="display: flex; align-items: center; margin-top: var(--space-xs);">
              <span class="material-icons" style="font-size: 16px; color: var(--neon-yellow); margin-right: 2px;">star</span>
              <span>4.6</span>
              <span style="margin-left: var(--space-md); color: var(--text-tertiary);">距您1.2km</span>
            </div>
          </div>
        </div>
        <a href="#map" style="display: block; height: 120px; border-radius: var(--radius-sm); background-image: url('https://i.imgur.com/2Z18SXa.png'); background-size: cover; background-position: center; margin-bottom: var(--space-sm);"></a>
        <div style="color: var(--text-tertiary); font-size: 14px;">中央商务区波特兰街89号</div>
      </div>
      
      <div style="margin-bottom: var(--space-xl); padding: var(--space-md) 0;">
        <div style="display: flex; align-items: center; justify-content: space-between; margin-bottom: var(--space-md);">
          <div>
            <div style="color: var(--text-tertiary);">人均费用</div>
            <div style="font-size: 20px; font-weight: 600; color: var(--neon-pink);">¥128</div>
          </div>
          <div>
            <div style="color: var(--text-tertiary);">剩余名额</div>
            <div style="font-size: 20px; font-weight: 600;">3位</div>
          </div>
        </div>
        
        <a href="#join-confirmation" class="button primary full">
          <span class="button-icon material-icons">check_circle</span>
          立即加入
        </a>
      </div>
    </div>
  </div>
  
  <!-- 创建饭局页 -->
  <div class="screen" id="create-feast">
    <div class="header">
      <button class="icon-button" onclick="window.location.href='#home'">
        <span class="material-icons">arrow_back</span>
      </button>
      <div class="header-title">创建新饭局</div>
    </div>
    
    <div class="full-content">
      <div class="form-group">
        <label class="form-label">饭局标题</label>
        <input type="text" class="form-input" placeholder="给你的饭局起个吸引人的名字">
      </div>
      
      <div class="form-group">
        <label class="form-label">饭局时间</label>
        <div style="display: flex; gap: var(--space-md);">
          <input type="date" class="form-input" style="flex: 1;">
          <input type="time" class="form-input" style="flex: 1;">
        </div>
      </div>
      
      <div class="form-group">
        <label class="form-label">选择餐厅</label>
        <div style="position: relative;">
          <input type="text" class="form-input" placeholder="搜索餐厅...">
          <span class="material-icons" style="position: absolute; right: var(--space-md); top: 50%; transform: translateY(-50%); color: var(--text-tertiary);">search</span>
        </div>
      </div>
      
      <div class="form-group">
        <label class="form-label">饭局描述</label>
        <textarea class="form-input" placeholder="描述一下你的饭局内容、氛围、适合什么样的人参加等..."></textarea>
      </div>
      
      <div class="form-group">
        <label class="form-label">人数上限</label>
        <select class="form-select">
          <option>2人</option>
          <option>4人</option>
          <option selected>6人</option>
          <option>8人</option>
          <option>10人</option>
          <option>不限</option>
        </select>
      </div>
      
      <div class="form-group">
        <label class="form-label">人均预算</label>
        <div style="position: relative;">
          <input type="number" class="form-input" placeholder="输入人均消费金额">
          <span style="position: absolute; left: var(--space-md); top: 50%; transform: translateY(-50%); color: var(--text-primary);">¥</span>
        </div>
      </div>
      
      <div class="form-group">
        <label class="form-label">添加标签 (最多选择3个)</label>
        <div class="tags-container" style="margin-top: 0;">
          <span class="tag highlighted">美食探索</span>
          <span class="tag">创意料理</span>
          <span class="tag">聊天交友</span>
          <span class="tag">职场社交</span>
          <span class="tag">音乐</span>
          <span class="tag">电影</span>
          <span class="tag">艺术</span>
          <span class="tag">读书会</span>
          <span class="tag">创业</span>
          <span class="tag">科技</span>
          <span class="tag">游戏</span>
          <span class="tag">运动</span>
        </div>
      </div>
      
      <div class="form-group">
        <label class="form-label">饭局封面</label>
        <div style="background: var(--bg-card); border-radius: var(--radius-md); height: 150px; display: flex; align-items: center; justify-content: center; border: 1px dashed var(--border-light);">
          <span class="material-icons" style="font-size: 36px; color: var(--text-tertiary);">add_photo_alternate</span>
        </div>
      </div>
      
      <div class="form-group">
        <label class="form-label">饭局类型</label>
        <div style="display: flex; gap: var(--space-md);">
          <div style="flex: 1; background: var(--bg-card); padding: var(--space-md); border-radius: var(--radius-md); text-align: center; border: 2px solid var(--primary);">
            <span class="material-icons" style="font-size: 36px; color: var(--primary);">group</span>
            <div style="margin-top: var(--space-xs);">公开饭局</div>
            <div style="font-size: 12px; color: var(--text-tertiary);">所有人可见</div>
          </div>
          <div style="flex: 1; background: var(--bg-card); padding: var(--space-md); border-radius: var(--radius-md); text-align: center; border: 1px solid var(--border-light);">
            <span class="material-icons" style="font-size: 36px; color: var(--text-tertiary);">lock</span>
            <div style="margin-top: var(--space-xs);">私密饭局</div>
            <div style="font-size: 12px; color: var(--text-tertiary);">仅邀请可见</div>
          </div>
        </div>
      </div>
      
      <a href="#home" class="button primary full" style="margin: var(--space-xl) 0;">
        <span class="button-icon material-icons">celebration</span>
        发布饭局
      </a>
    </div>
  </div>
  
  <!-- 附近餐厅/地图页 -->
  <div class="screen" id="nearby">
    <div class="header">
      <div class="header-title">附近饭局</div>
      <div class="header-action">
        <button class="icon-button">
          <span class="material-icons">filter_list</span>
        </button>
      </div>
    </div>
    
    <div style="position: absolute; top: 80px; left: 0; right: 0; bottom: 80px; background-image: url('https://i.imgur.com/4N1QiVN.png'); background-size: cover; background-position: center;">
      <!-- 地图标记 -->
      <div style="position: absolute; top: 30%; left: 45%; background: var(--neon-pink); width: 16px; height: 16px; border-radius: 50%; border: 3px solid white; box-shadow: 0 0 0 2px var(--neon-pink);"></div>
      
      <div style="position: absolute; top: 50%; left: 30%; background: var(--primary); width: 16px; height: 16px; border-radius: 50%; border: 3px solid white; box-shadow: 0 0 0 2px var(--primary);"></div>
      
      <div style="position: absolute; top: 40%; left: 70%; background: var(--neon-green); width: 16px; height: 16px; border-radius: 50%; border: 3px solid white; box-shadow: 0 0 0 2px var(--neon-green);"></div>
      
      <!-- 当前选中地点 -->
      <div style="position: absolute; top: 65%; left: 50%; transform: translateX(-50%); background: white; border-radius: var(--radius-md); padding: var(--space-sm); width: 90%; box-shadow: var(--shadow-card);">
        <div style="display: flex;">
          <div style="width: 80px; height: 80px; border-radius: var(--radius-sm); background-image: url('https://images.unsplash.com/photo-1555396273-367ea4eb4db5?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1074&q=80'); background-size: cover; background-position: center;"></div>
          <div style="margin-left: var(--space-md); flex: 1; color: var(--bg-dark);">
            <div style="font-weight: 600;">创意料理夜 @ 深蓝餐厅</div>
            <div style="font-size: 14px; opacity: 0.7; margin-bottom: var(--space-xs);">今晚 19:30 · 1.2km</div>
            <div style="display: flex; gap: var(--space-xs);">
              <span style="background: var(--primary); color: white; padding: 2px 8px; border-radius: 10px; font-size: 12px;">3/6人</span>
              <span style="background: var(--neon-pink); color: white; padding: 2px 8px; border-radius: 10px; font-size: 12px;">¥128/位</span>
            </div>
          </div>
          <div style="display: flex; align-items: center;">
            <span class="material-icons" style="color: var(--bg-dark);">navigate_next</span>
          </div>
        </div>
      </div>
    </div>
    
    <div class="categories" style="position: absolute; top: 90px; left: var(--space-md); right: var(--space-md); z-index: 10; background: rgba(18,18,18,0.8); padding: var(--space-sm); border-radius: var(--radius-full);">
      <div class="category-item active">全部</div>
      <div class="category-item">创意料理</div>
      <div class="category-item">红酒品鉴</div>
      <div class="category-item">咖啡馆</div>
      <div class="category-item">日料</div>
    </div>
    
    <div class="nav-bar">
      <a href="#home" class="nav-item">
        <span class="material-icons nav-icon">explore</span>
        <span>发现</span>
      </a>
      <a href="#nearby" class="nav-item active">
        <span class="material-icons nav-icon">map</span>
        <span>附近</span>
      </a>
      <a href="#messages" class="nav-item">
        <span class="material-icons nav-icon">chat</span>
        <span>消息</span>
      </a>
      <a href="#profile" class="nav-item">
        <span class="material-icons nav-icon">person</span>
        <span>我的</span>
      </a>
    </div>
  </div>
  
  <!-- 消息列表页 -->
  <div class="screen" id="messages">
    <div class="header">
      <div class="header-title">消息</div>
      <div class="header-action">
        <button class="icon-button">
          <span class="material-icons">edit</span>
        </button>
      </div>
    </div>
    
    <div class="content">
      <div class="search-bar">
        <span class="material-icons search-icon">search</span>
        <input type="text" class="search-input" placeholder="搜索消息...">
      </div>
      
      <div class="categories">
        <div class="category-item active">全部</div>
        <div class="category-item">饭局</div>
        <div class="category-item">好友</div>
        <div class="category-item">系统</div>
      </div>
      
      <a href="#chat" class="card" style="margin-bottom: var(--space-md); padding: var(--space-md);">
        <div style="display: flex; align-items: center;">
          <div style="position: relative;">
            <img src="https://randomuser.me/api/portraits/men/32.jpg" class="avatar">
            <span style="position: absolute; bottom: 0; right: 0; width: 12px; height: 12px; background: var(--neon-green); border-radius: 50%; border: 2px solid var(--bg-card);"></span>
          </div>
          <div style="margin-left: var(--space-md); flex: 1;">
            <div style="display: flex; justify-content: space-between;">
              <div style="font-weight: 500;">Alex Chen</div>
              <div style="font-size: 12px; color: var(--text-tertiary);">14:30</div>
            </div>
            <div style="display: flex; justify-content: space-between; margin-top: var(--space-xs);">
              <div style="color: var(--text-secondary); font-size: 14px;">期待今晚见到你！我已经准备...</div>
              ```html
              <div style="background: var(--primary); color: white; font-size: 12px; height: 20px; width: 20px; border-radius: 50%; display: flex; align-items: center; justify-content: center;">2</div>
            </div>
          </div>
        </div>
      </a>

      <a href="#feast-chat" class="card" style="margin-bottom: var(--space-md); padding: var(--space-md);">
        <div style="display: flex; align-items: center;">
          <div style="position: relative;">
            <div style="width: 50px; height: 50px; border-radius: var(--radius-md); background-image: url('https://images.unsplash.com/photo-1555396273-367ea4eb4db5?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1074&q=80'); background-size: cover; background-position: center;"></div>
          </div>
          <div style="margin-left: var(--space-md); flex: 1;">
            <div style="display: flex; justify-content: space-between;">
              <div style="font-weight: 500;">创意料理夜 (6人)</div>
              <div style="font-size: 12px; color: var(--text-tertiary);">12:05</div>
            </div>
            <div style="display: flex; justify-content: space-between; margin-top: var(--space-xs);">
              <div style="color: var(--text-secondary); font-size: 14px;">Alex: 大家可以提前10分钟到餐厅...</div>
              <div style="background: var(--primary); color: white; font-size: 12px; height: 20px; width: 20px; border-radius: 50%; display: flex; align-items: center; justify-content: center;">5</div>
            </div>
          </div>
        </div>
      </a>

      <a href="#chat" class="card" style="margin-bottom: var(--space-md); padding: var(--space-md);">
        <div style="display: flex; align-items: center;">
          <div style="position: relative;">
            <img src="https://randomuser.me/api/portraits/women/44.jpg" class="avatar">
          </div>
          <div style="margin-left: var(--space-md); flex: 1;">
            <div style="display: flex; justify-content: space-between;">
              <div style="font-weight: 500;">Sophia Lin</div>
              <div style="font-size: 12px; color: var(--text-tertiary);">昨天</div>
            </div>
            <div style="display: flex; justify-content: space-between; margin-top: var(--space-xs);">
              <div style="color: var(--text-secondary); font-size: 14px;">我很喜欢上次的红酒品鉴！下次...</div>
            </div>
          </div>
        </div>
      </a>

      <a href="#chat" class="card" style="margin-bottom: var(--space-md); padding: var(--space-md);">
        <div style="display: flex; align-items: center;">
          <div style="position: relative;">
            <img src="https://randomuser.me/api/portraits/men/85.jpg" class="avatar">
          </div>
          <div style="margin-left: var(--space-md); flex: 1;">
            <div style="display: flex; justify-content: space-between;">
              <div style="font-weight: 500;">Jack Zhang</div>
              <div style="font-size: 12px; color: var(--text-tertiary);">上周</div>
            </div>
            <div style="display: flex; justify-content: space-between; margin-top: var(--space-xs);">
              <div style="color: var(--text-tertiary); font-size: 14px;">你已成功加入科技创业者交流会</div>
            </div>
          </div>
        </div>
      </a>

      <div class="card" style="margin-bottom: var(--space-md); padding: var(--space-md); background: rgba(140, 82, 255, 0.1); border: 1px solid var(--primary);">
        <div style="display: flex; align-items: center;">
          <div style="position: relative;">
            <div style="width: 50px; height: 50px; border-radius: 50%; background: var(--primary); display: flex; align-items: center; justify-content: center;">
              <span class="material-icons" style="color: white; font-size: 28px;">notifications</span>
            </div>
          </div>
          <div style="margin-left: var(--space-md); flex: 1;">
            <div style="display: flex; justify-content: space-between;">
              <div style="font-weight: 500;">系统通知</div>
              <div style="font-size: 12px; color: var(--text-tertiary);">3天前</div>
            </div>
            <div style="display: flex; justify-content: space-between; margin-top: var(--space-xs);">
              <div style="color: var(--primary); font-size: 14px;">你的饭局评价获得了5个赞！查看...</div>
              <div style="background: var(--primary); color: white; font-size: 12px; height: 20px; width: 20px; border-radius: 50%; display: flex; align-items: center; justify-content: center;">1</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="nav-bar">
      <a href="#home" class="nav-item">
        <span class="material-icons nav-icon">explore</span>
        <span>发现</span>
      </a>
      <a href="#nearby" class="nav-item">
        <span class="material-icons nav-icon">map</span>
        <span>附近</span>
      </a>
      <a href="#messages" class="nav-item active">
        <span class="material-icons nav-icon">chat</span>
        <span>消息</span>
      </a>
      <a href="#profile" class="nav-item">
        <span class="material-icons nav-icon">person</span>
        <span>我的</span>
      </a>
    </div>
  </div>

  <!-- 聊天页面 -->
  <div class="screen" id="chat">
    <div class="header">
      <button class="icon-button" onclick="window.location.href='#messages'">
        <span class="material-icons">arrow_back</span>
      </button>
      <div class="header-title" style="display: flex; align-items: center;">
        <div>Alex Chen</div>
        <div style="width: 8px; height: 8px; background: var(--neon-green); border-radius: 50%; margin-left: var(--space-xs);"></div>
      </div>
      <div class="header-action">
        <button class="icon-button">
          <span class="material-icons">more_vert</span>
        </button>
      </div>
    </div>

    <div style="height: calc(100% - 140px); overflow-y: auto; padding: var(--space-md);">
      <div style="text-align: center; color: var(--text-tertiary); font-size: 12px; margin: var(--space-md) 0;">
        今天 14:25
      </div>

      <div class="chat-message">
        <img src="https://randomuser.me/api/portraits/men/32.jpg" class="message-avatar">
        <div class="message-content">
          <div class="message-bubble">
            嘿！很高兴你加入了今晚的创意料理夜！
          </div>
          <div class="message-time">14:25</div>
        </div>
      </div>

      <div class="chat-message">
        <img src="https://randomuser.me/api/portraits/men/32.jpg" class="message-avatar">
        <div class="message-content">
          <div class="message-bubble">
            我是主办人Alex，今晚的主厨会带来一些分子料理的新创作，希望你会喜欢！
          </div>
          <div class="message-time">14:26</div>
        </div>
      </div>

      <div class="chat-message outgoing">
        <img src="https://randomuser.me/api/portraits/women/33.jpg" class="message-avatar">
        <div class="message-content">
          <div class="message-bubble">
            你好Alex！我很期待今晚的活动，我对分子料理很感兴趣！
          </div>
          <div class="message-time">14:28</div>
        </div>
      </div>

      <div class="chat-message">
        <img src="https://randomuser.me/api/portraits/men/32.jpg" class="message-avatar">
        <div class="message-content">
          <div class="message-bubble">
            太好了！今晚除了美食，我们还会讨论一些创意料理的趋势和技巧，你有什么特别感兴趣的方面吗？
          </div>
          <div class="message-time">14:30</div>
        </div>
      </div>

      <div class="chat-message outgoing">
        <img src="https://randomuser.me/api/portraits/women/33.jpg" class="message-avatar">
        <div class="message-content">
          <div class="message-bubble">
            我最近在尝试一些植物性料理，对可持续美食很感兴趣。希望能听到大家的经验和想法！
          </div>
          <div class="message-time">14:45</div>
        </div>
      </div>
    </div>

    <div style="position: absolute; bottom: 0; left: 0; right: 0; padding: var(--space-md); background: var(--bg-dark); border-top: 1px solid var(--border-light); display: flex; align-items: center;">
      <input type="text" placeholder="发送消息..." class="chat-input">
      <button class="icon-button" style="background: var(--primary);">
        <span class="material-icons" style="color: white;">send</span>
      </button>
    </div>
  </div>

  <!-- 个人资料页 -->
  <div class="screen" id="profile">
    <div class="profile-header">
      <img src="https://randomuser.me/api/portraits/women/33.jpg" class="profile-avatar">
      <h2>Lisa Wang</h2>
      <div style="color: rgba(255,255,255,0.7);">美食探险家 | 摄影爱好者</div>
    </div>

    <div class="content" style="padding-top: 0;">
      <div class="profile-stats">
        <div class="stat-item">
          <div class="stat-value">15</div>
          <div class="stat-label">已参与饭局</div>
        </div>
        <div class="stat-item">
          <div class="stat-value">3</div>
          <div class="stat-label">已创建饭局</div>
        </div>
        <div class="stat-item">
          <div class="stat-value">28</div>
          <div class="stat-label">好友</div>
        </div>
      </div>

      <div class="card" style="display: flex; justify-content: space-between; align-items: center;">
        <div>
          <div style="font-weight: 500;">社交信用分</div>
          <div style="font-size: 20px; font-weight: 700; color: var(--neon-green); display: flex; align-items: center;">
            <span>4.9</span>
            <span class="material-icons" style="font-size: 16px; margin-left: var(--space-xs);">verified</span>
          </div>
        </div>
        <div style="width: 50px; height: 50px; border-radius: var(--radius-full); background: var(--neon-green); display: flex; align-items: center; justify-content: center; box-shadow: 0 0 15px rgba(0, 255, 133, 0.5);">
          <span class="material-icons" style="color: var(--bg-dark); font-size: 28px;">emoji_events</span>
        </div>
      </div>

      <div class="section-title">兴趣标签</div>
      <div class="tags-container">
        <span class="tag highlighted">分子料理</span>
        <span class="tag highlighted">咖啡文化</span>
        <span class="tag highlighted">摄影</span>
        <span class="tag">旅行</span>
        <span class="tag">艺术展览</span>
        <span class="tag">音乐剧</span>
        <span class="tag">建筑设计</span>
      </div>

      <div class="section-title">即将参加</div>
      <a href="#feast-detail" class="card" style="margin-bottom: var(--space-md); padding: var(--space-md);">
        <div style="display: flex; align-items: center;">
          <div style="width: 60px; height: 60px; border-radius: var(--radius-md); background-image: url('https://images.unsplash.com/photo-1555396273-367ea4eb4db5?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1074&q=80'); background-size: cover; background-position: center; margin-right: var(--space-md);"></div>
          <div>
            <div style="font-weight: 500;">创意料理夜 @ 深蓝餐厅</div>
            <div style="color: var(--text-secondary); font-size: 14px; margin-top: var(--space-xs);">今晚 19:30 · 3/6人</div>
          </div>
        </div>
      </a>

      <div class="section-title">我的动态</div>
      <div class="card">
        <div style="display: flex;">
          <img src="https://randomuser.me/api/portraits/women/33.jpg" class="avatar small">
          <div style="margin-left: var(--space-md); flex: 1;">
            <div style="font-weight: 500;">Lisa Wang</div>
            <div style="color: var(--text-tertiary); font-size: 12px;">昨天 · 公开</div>
          </div>
        </div>
        <p style="margin: var(--space-md) 0; color: var(--text-secondary);">
          昨天参加了"爵士与红酒之夜"，遇到了几位志同道合的朋友，聊得很开心！音乐氛围很棒，红酒也很精选。感谢 @Sophia 的组织！
        </p>
        <div style="border-radius: var(--radius-md); overflow: hidden; height: 150px; background-image: url('https://images.unsplash.com/photo-1470225620780-dba8ba36b745?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80'); background-size: cover; background-position: center; margin-bottom: var(--space-md);"></div>

        <div style="display: flex; align-items: center; color: var(--text-tertiary);">
          <div style="display: flex; align-items: center; margin-right: var(--space-lg);">
            <span class="material-icons" style="font-size: 18px; margin-right: var(--space-xs);">favorite</span>
            <span>12</span>
          </div>
          <div style="display: flex; align-items: center;">
            <span class="material-icons" style="font-size: 18px; margin-right: var(--space-xs);">comment</span>
            <span>3</span>
          </div>
        </div>
      </div>

      <div style="height: 80px;"></div>
    </div>

    <div class="nav-bar">
      <a href="#home" class="nav-item">
        <span class="material-icons nav-icon">explore</span>
        <span>发现</span>
      </a>
      <a href="#nearby" class="nav-item">
        <span class="material-icons nav-icon">map</span>
        <span>附近</span>
      </a>
      <a href="#messages" class="nav-item">
        <span class="material-icons nav-icon">chat</span>
        <span>消息</span>
      </a>
      <a href="#profile" class="nav-item active">
        <span class="material-icons nav-icon">person</span>
        <span>我的</span>
      </a>
    </div>
  </div>

  <!-- 加入饭局确认页 -->
  <div class="screen" id="join-confirmation">
    <div class="header">
      <button class="icon-button" onclick="window.location.href='#feast-detail'">
        <span class="material-icons">arrow_back</span>
      </button>
      <div class="header-title">确认加入</div>
    </div>

    <div class="full-content" style="display: flex; flex-direction: column; align-items: center; padding-top: var(--space-xl);">
      <div style="width: 100px; height: 100px; background: var(--primary); border-radius: 50%; display: flex; align-items: center; justify-content: center; margin-bottom: var(--space-lg); box-shadow: 0 0 20px rgba(140, 82, 255, 0.4);">
        <span class="material-icons" style="font-size: 48px; color: white;">restaurant</span>
      </div>

      <h2 style="margin-bottom: var(--space-md);">创意料理夜 @ 深蓝餐厅</h2>

      <div style="text-align: center; color: var(--text-secondary); margin-bottom: var(--space-xl); padding: 0 var(--space-lg);">
        你即将加入由 <span style="color: var(--primary);">Alex Chen</span> 主办的饭局，与其他美食爱好者一起探索创意料理！
      </div>

      <div class="card" style="width: 100%;">
        <h4 style="margin-bottom: var(--space-md);">饭局详情</h4>
        <div style="display: flex; justify-content: space-between; margin-bottom: var(--space-sm);">
          <div style="color: var(--text-tertiary);">时间</div>
          <div>今晚 19:30-21:30</div>
        </div>
        <div style="display: flex; justify-content: space-between; margin-bottom: var(--space-sm);">
          <div style="color: var(--text-tertiary);">地点</div>
          <div>深蓝餐厅 (1.2km)</div>
        </div>
        <div style="display: flex; justify-content: space-between; margin-bottom: var(--space-sm);">
          <div style="color: var(--text-tertiary);">人均费用</div>
          <div style="color: var(--neon-pink); font-weight: 600;">¥128</div>
        </div>
        <div style="display: flex; justify-content: space-between;">
          <div style="color: var(--text-tertiary);">已报名</div>
          <div>3/6人</div>
        </div>
      </div>

      <div class="form-group" style="width: 100%; margin-top: var(--space-lg);">
        <label class="form-label">留言给主办人 (选填)</label>
        <textarea class="form-input" placeholder="有什么想告诉主办人的吗？比如饮食禁忌、过敏原等..."></textarea>
      </div>

      <div style="margin-top: var(--space-xl); width: 100%;">
        <a href="#join-success" class="button primary full" style="margin-bottom: var(--space-md);">
          <span class="button-icon material-icons">check_circle</span>
          确认加入
        </a>
        <a href="#feast-detail" class="button outline full">返回</a>
      </div>
    </div>
  </div>

  <!-- 加入成功页面 -->
  <div class="screen" id="join-success">
    <div style="height: 100%; display: flex; flex-direction: column; align-items: center; justify-content: center; padding: var(--space-xl);">
      <div style="width: 120px; height: 120px; background: var(--neon-green); border-radius: 50%; display: flex; align-items: center; justify-content: center; margin-bottom: var(--space-lg); box-shadow: 0 0 30px rgba(0, 255, 133, 0.4); animation: pulse 1.5s infinite;">
        <span class="material-icons" style="font-size: 60px; color: white;">check</span>
      </div>

      <h2 style="margin-bottom: var(--space-md); text-align: center;">饭局加入成功！</h2>

      <div style="text-align: center; color: var(--text-secondary); margin-bottom: var(--space-xl);">
        恭喜你成功加入「创意料理夜」！<br>已将饭局信息添加到你的日程中，我们向你发送了一条确认消息。
      </div>

      <div style="display: flex; gap: var(--space-md); width: 100%; margin-bottom: var(--space-xl);">
        <a href="#messages" class="button outline" style="flex: 1;">
          <span class="button-icon material-icons">chat</span>
          聊天群组
        </a>
        <a href="#feast-detail" class="button outline" style="flex: 1;">
          <span class="button-icon material-icons">info</span>
          饭局详情
        </a>
      </div>

      <a href="#home" class="button primary full">
        <span class="button-icon material-icons">explore</span>
        继续探索
      </a>
    </div>
  </div>

</div>

</body>
</html>


```

## 完整代码
```html
      
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>极地气象预报系统 - 三维地球</title>
  <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+SC:wght@300;400;500;700&display=swap" rel="stylesheet">
  <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.0/font/bootstrap-icons.css" rel="stylesheet">
  <style>
    :root {
      --primary: #00a8ff;
      --secondary: #0097e6;
      --accent: #00d2d3;
      --dark: #1e272e;
      --light: #f5f6fa;
      --danger: #ff3f34;
      --warning: #ffa801;
      --success: #05c46b;
      --card-bg: rgba(30, 39, 46, 0.8);
      --card-border: rgba(0, 168, 255, 0.3);
    }
    
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Noto Sans SC', sans-serif;
    }
    
    body {
      margin: 0;
      padding: 0;
      overflow: hidden;
      background-color: #000;
      color: var(--light);
    }
    
    #container {
      position: absolute;
      width: 100%;
      height: 100%;
    }
    
    .header {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      padding: 20px 30px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      z-index: 100;
      background: linear-gradient(to bottom, rgba(0,0,0,0.7) 0%, rgba(0,0,0,0) 100%);
    }
    
    .title {
      font-size: 24px;
      font-weight: 700;
      display: flex;
      align-items: center;
    }
    
    .title::before {
      content: '';
      display: inline-block;
      width: 4px;
      height: 24px;
      background: var(--primary);
      margin-right: 10px;
    }
    
    .date-time {
      font-size: 16px;
      opacity: 0.8;
      text-align: right;
    }
    
    .controls-panel {
      position: absolute;
      top: 100px;
      left: 30px;
      background: var(--card-bg);
      border: 1px solid var(--card-border);
      border-radius: 10px;
      padding: 20px;
      width: 280px;
      backdrop-filter: blur(10px);
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
      z-index: 100;
    }
    
    .panel-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 15px;
      padding-bottom: 10px;
      border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    }
    
    .panel-title {
      font-size: 16px;
      font-weight: 500;
    }
    
    .btn-group {
      display: flex;
      gap: 10px;
      margin: 15px 0;
    }
    
    .btn {
      background: rgba(0, 168, 255, 0.2);
      color: var(--light);
      border: 1px solid var(--primary);
      border-radius: 5px;
      padding: 8px 15px;
      cursor: pointer;
      transition: all 0.3s;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 5px;
      flex: 1;
    }
    
    .btn:hover {
      background: var(--primary);
      color: var(--dark);
    }
    
    .btn i {
      font-size: 14px;
    }
    
    .data-layers {
      margin-top: 20px;
    }
    
    .layer-item {
      display: flex;
      align-items: center;
      margin-bottom: 10px;
      padding: 8px;
      border-radius: 5px;
      transition: all 0.3s;
    }
    
    .layer-item:hover {
      background: rgba(255, 255, 255, 0.1);
    }
    
    .layer-checkbox {
      appearance: none;
      width: 16px;
      height: 16px;
      border: 1px solid var(--primary);
      border-radius: 3px;
      margin-right: 10px;
      position: relative;
      cursor: pointer;
    }
    
    .layer-checkbox:checked {
      background: var(--primary);
    }
    
    .layer-checkbox:checked::after {
      content: '✓';
      position: absolute;
      color: var(--dark);
      font-size: 12px;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
    
    .layer-label {
      flex: 1;
    }
    
    .layer-color {
      width: 16px;
      height: 16px;
      border-radius: 50%;
      margin-left: 10px;
    }
    
    .data-panel {
      position: absolute;
      top: 100px;
      right: 30px;
      background: var(--card-bg);
      border: 1px solid var(--card-border);
      border-radius: 10px;
      padding: 20px;
      width: 320px;
      backdrop-filter: blur(10px);
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
      z-index: 100;
    }
    
    .data-item {
      display: flex;
      align-items: center;
      margin-bottom: 15px;
    }
    
    .data-icon {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      background: rgba(0, 168, 255, 0.2);
      display: flex;
      align-items: center;
      justify-content: center;
      margin-right: 15px;
    }
    
    .data-icon i {
      font-size: 20px;
      color: var(--primary);
    }
    
    .data-content {
      flex: 1;
    }
    
    .data-label {
      font-size: 12px;
      opacity: 0.7;
      margin-bottom: 3px;
    }
    
    .data-value {
      font-size: 18px;
      font-weight: 500;
    }
    
    .data-unit {
      font-size: 12px;
      opacity: 0.7;
      margin-left: 5px;
    }
    
    .station-info {
      position: absolute;
      bottom: 30px;
      left: 30px;
      background: var(--card-bg);
      border: 1px solid var(--card-border);
      border-radius: 10px;
      padding: 20px;
      width: 280px;
      backdrop-filter: blur(10px);
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
      z-index: 100;
      transform: translateY(20px);
      opacity: 0;
      transition: all 0.3s;
      pointer-events: none;
    }
    
    .station-info.visible {
      transform: translateY(0);
      opacity: 1;
      pointer-events: all;
    }
    
    .station-header {
      display: flex;
      align-items: center;
      margin-bottom: 15px;
    }
    
    .station-icon {
      width: 36px;
      height: 36px;
      border-radius: 50%;
      background: rgba(0, 168, 255, 0.2);
      display: flex;
      align-items: center;
      justify-content: center;
      margin-right: 15px;
    }
    
    .station-name {
      font-size: 16px;
      font-weight: 500;
    }
    
    .station-coords {
      font-size: 12px;
      opacity: 0.7;
    }
    
    .timeline {
      position: absolute;
      bottom: 30px;
      left: 50%;
      transform: translateX(-50%);
      background: var(--card-bg);
      border: 1px solid var(--card-border);
      border-radius: 10px;
      padding: 15px 20px;
      width: 60%;
      backdrop-filter: blur(10px);
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
      z-index: 100;
    }
    
    .timeline-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 10px;
    }
    
    .timeline-title {
      font-size: 14px;
      opacity: 0.8;
    }
    
    .timeline-controls {
      display: flex;
      gap: 10px;
    }
    
    .timeline-btn {
      background: none;
      border: none;
      color: var(--light);
      cursor: pointer;
      font-size: 16px;
      opacity: 0.7;
      transition: all 0.3s;
    }
    
    .timeline-btn:hover {
      opacity: 1;
      color: var(--primary);
    }
    
    .timeline-slider {
      width: 100%;
      height: 4px;
      background: rgba(255, 255, 255, 0.1);
      border-radius: 2px;
      position: relative;
      cursor: pointer;
    }
    
    .timeline-progress {
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
      width: 30%;
      background: var(--primary);
      border-radius: 2px;
    }
    
    .timeline-handle {
      position: absolute;
      top: 50%;
      left: 30%;
      transform: translate(-50%, -50%);
      width: 16px;
      height: 16px;
      background: var(--light);
      border-radius: 50%;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
    }
    
    .timeline-ticks {
      display: flex;
      justify-content: space-between;
      margin-top: 10px;
      padding: 0 8px;
    }
    
    .timeline-tick {
      font-size: 12px;
      opacity: 0.7;
    }
    
    .loading {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: #000;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      z-index: 1000;
      transition: opacity 0.5s;
    }
    
    .loading.hidden {
      opacity: 0;
      pointer-events: none;
    }
    
    .loading-spinner {
      width: 50px;
      height: 50px;
      border: 3px solid rgba(0, 168, 255, 0.3);
      border-radius: 50%;
      border-top-color: var(--primary);
      animation: spin 1s linear infinite;
      margin-bottom: 20px;
    }
    
    @keyframes spin {
      to { transform: rotate(360deg); }
    }
    
    .loading-text {
      font-size: 18px;
      opacity: 0.8;
    }
    
    .marker {
      position: absolute;
      width: 20px;
      height: 20px;
      margin-left: -10px;
      margin-top: -10px;
      border-radius: 50%;
      cursor: pointer;
      background: var(--primary);
      box-shadow: 0 0 10px var(--primary);
      transform: scale(0);
      animation: pulse 2s infinite;
    }
    
    @keyframes pulse {
      0% { transform: scale(0.5); opacity: 1; }
      70% { transform: scale(0.8); opacity: 0.7; }
      100% { transform: scale(0.5); opacity: 1; }
    }
    
    .marker::after {
      content: '';
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 8px;
      height: 8px;
      background: white;
      border-radius: 50%;
    }
    
    .legend {
      position: absolute;
      bottom: 30px;
      right: 30px;
      background: var(--card-bg);
      border: 1px solid var(--card-border);
      border-radius: 10px;
      padding: 15px;
      backdrop-filter: blur(10px);
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
      z-index: 100;
    }
    
    .legend-title {
      font-size: 14px;
      margin-bottom: 10px;
    }
    
    .legend-gradient {
      height: 10px;
      width: 100%;
      border-radius: 5px;
      margin-bottom: 5px;
      background: linear-gradient(to right, #00d2d3, #00a8ff, #0097e6, #ffa801, #ff3f34);
    }
    
    .legend-labels {
      display: flex;
      justify-content: space-between;
    }
    
    .legend-label {
      font-size: 12px;
      opacity: 0.7;
    }
    
    /* 粒子效果 */
    .particles {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: -1;
    }
    
    /* 数据可视化效果 */
    .data-visualization {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
    }
    
    /* 光晕效果 */
    .glow {
      position: absolute;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle at center, rgba(0, 168, 255, 0.2) 0%, rgba(0, 0, 0, 0) 70%);
      pointer-events: none;
      z-index: -1;
    }
    
    /* 响应式调整 */
    @media (max-width: 1200px) {
      .timeline {
        width: 80%;
      }
    }
    
    @media (max-width: 768px) {
      .controls-panel, .data-panel {
        width: 250px;
      }
      
      .timeline {
        width: 90%;
      }
      
      .legend {
        display: none;
      }
    }
  </style>
</head>
<body>
  <div id="container"></div>
  <div class="glow"></div>
  
  <div class="header">
    <div class="title">极地气象预报系统</div>
    <div class="date-time">
      <div id="current-date">2025年2月28日</div>
      <div id="current-time">星期五 15:30:00</div>
    </div>
  </div>
  
  <div class="controls-panel">
    <div class="panel-header">
      <div class="panel-title">控制面板</div>
      <i class="bi bi-gear"></i>
    </div>
    
    <div class="btn-group">
      <button class="btn" id="focusAntarctica">
        <i class="bi bi-geo-alt"></i>
        <span>南极洲</span>
      </button>
      <button class="btn" id="resetView">
        <i class="bi bi-arrow-counterclockwise"></i>
        <span>重置</span>
      </button>
    </div>
    
    <div class="data-layers">
      <div class="panel-title" style="margin-bottom: 10px;">数据图层</div>
      
      <div class="layer-item">
        <input type="checkbox" class="layer-checkbox" id="layer-temp" checked>
        <label class="layer-label" for="layer-temp">温度分布</label>
        <div class="layer-color" style="background: linear-gradient(45deg, #00d2d3, #ff3f34);"></div>
      </div>
      
      <div class="layer-item">
        <input type="checkbox" class="layer-checkbox" id="layer-wind">
        <label class="layer-label" for="layer-wind">风速风向</label>
        <div class="layer-color" style="background: linear-gradient(45deg, #00a8ff, #0097e6);"></div>
      </div>
      
      <div class="layer-item">
        <input type="checkbox" class="layer-checkbox" id="layer-pressure">
        <label class="layer-label" for="layer-pressure">气压场</label>
        <div class="layer-color" style="background: linear-gradient(45deg, #ffa801, #ff3f34);"></div>
      </div>
      
      <div class="layer-item">
        <input type="checkbox" class="layer-checkbox" id="layer-stations" checked>
        <label class="layer-label" for="layer-stations">观测站点</label>
        <div class="layer-color" style="background: var(--primary);"></div>
      </div>
      
      <div class="layer-item">
        <input type="checkbox" class="layer-checkbox" id="layer-clouds" checked>
        <label class="layer-label" for="layer-clouds">云层</label>
        <div class="layer-color" style="background: rgba(255, 255, 255, 0.7);"></div>
      </div>
    </div>
  </div>
  
  <div class="data-panel">
    <div class="panel-header">
      <div class="panel-title">南极洲气象数据</div>
      <div style="font-size: 12px; opacity: 0.7;">实时更新</div>
    </div>
    
    <div class="data-item">
      <div class="data-icon">
        <i class="bi bi-thermometer-half"></i>
      </div>
      <div class="data-content">
        <div class="data-label">地表气温</div>
        <div class="data-value">-26.8<span class="data-unit">°C</span></div>
      </div>
    </div>
    
    <div class="data-item">
      <div class="data-icon">
        <i class="bi bi-thermometer-low"></i>
      </div>
      <div class="data-content">
        <div class="data-label">2m气温</div>
        <div class="data-value">-32.4<span class="data-unit">°C</span></div>
      </div>
    </div>
    
    <div class="data-item">
      <div class="data-icon">
        <i class="bi bi-wind"></i>
      </div>
      <div class="data-content">
        <div class="data-label">风速</div>
        <div class="data-value">8.6<span class="data-unit">m/s</span></div>
      </div>
    </div>
    
    <div class="data-item">
      <div class="data-icon">
        <i class="bi bi-cloud-rain"></i>
      </div>
      <div class="data-content">
        <div class="data-label">降水量</div>
        <div class="data-value">0.2<span class="data-unit">mm</span></div>
      </div>
    </div>
    
    <div class="data-item">
      <div class="data-icon">
        <i class="bi bi-speedometer"></i>
      </div>
      <div class="data-content">
        <div class="data-label">气压</div>
        <div class="data-value">1012<span class="data-unit">hPa</span></div>
      </div>
    </div>
  </div>
  
  <div class="station-info" id="station-info">
    <div class="station-header">
      <div class="station-icon">
        <i class="bi bi-broadcast-pin"></i>
      </div>
      <div>
        <div class="station-name">中山站</div>
        <div class="station-coords">69°22'24.6"S, 76°22'14.0"E</div>
      </div>
    </div>
    
    <div class="data-item">
      <div class="data-icon" style="width: 30px; height: 30px;">
        <i class="bi bi-thermometer-half" style="font-size: 16px;"></i>
      </div>
      <div class="data-content">
        <div class="data-label">气温</div>
        <div class="data-value">-28.5<span class="data-unit">°C</span></div>
      </div>
    </div>
    
    <div class="data-item">
      <div class="data-icon" style="width: 30px; height: 30px;">
        <i class="bi bi-wind" style="font-size: 16px;"></i>
      </div>
      <div class="data-content">
        <div class="data-label">风速</div>
        <div class="data-value">9.8<span class="data-unit">m/s</span></div>
      </div>
    </div>
    
    <div class="data-item" style="margin-bottom: 0;">
      <div class="data-icon" style="width: 30px; height: 30px;">
        <i class="bi bi-moisture" style="font-size: 16px;"></i>
      </div>
      <div class="data-content">
        <div class="data-label">相对湿度</div>
        <div class="data-value">75<span class="data-unit">%</span></div>
      </div>
    </div>
  </div>
  
  <div class="timeline">
    <div class="timeline-header">
      <div class="timeline-title">时间轴 - 2025年2月28日</div>
      <div class="timeline-controls">
        <button class="timeline-btn" id="play-btn"><i class="bi bi-play-fill"></i></button>
        <button class="timeline-btn" id="pause-btn"><i class="bi bi-pause-fill"></i></button>
      </div>
    </div>
    
    <div class="timeline-slider" id="timeline-slider">
      <div class="timeline-progress" id="timeline-progress"></div>
      <div class="timeline-handle" id="timeline-handle"></div>
    </div>
    
    <div class="timeline-ticks">
      <div class="timeline-tick">10:00</div>
      <div class="timeline-tick">12:00</div>
      <div class="timeline-tick">14:00</div>
      <div class="timeline-tick">16:00</div>
      <div class="timeline-tick">18:00</div>
      <div class="timeline-tick">20:00</div>
    </div>
  </div>
  
  <div class="legend">
    <div class="legend-title">温度分布 (°C)</div>
    <div class="legend-gradient"></div>
    <div class="legend-labels">
      <div class="legend-label">-40</div>
      <div class="legend-label">-30</div>
      <div class="legend-label">-20</div>
      <div class="legend-label">-10</div>
      <div class="legend-label">0</div>
    </div>
  </div>
  
  <div class="loading" id="loading">
    <div class="loading-spinner"></div>
    <div class="loading-text">加载中，请稍候...</div>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/three@0.132.2/build/three.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/three@0.132.2/examples/js/controls/OrbitControls.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/gsap@3.9.1/dist/gsap.min.js"></script>
  
  <script>
    // 等待资源加载
    window.addEventListener('load', init);
    
    let scene, camera, renderer, earth, clouds, controls;
    let antarcticaHighlight, temperatureLayer, windLayer, pressureLayer;
    let stations = [];
    let timelineProgress = 0.3;
    let isPlaying = false;
    let playInterval;
    
    function init() {
      // 创建场景
      scene = new THREE.Scene();
      
      // 创建相机
      camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 0.1, 1000);
      camera.position.z = 3;
      
      // 创建渲染器
      renderer = new THREE.WebGLRenderer({ 
        antialias: true,
        alpha: true
      });
      renderer.setSize(window.innerWidth, window.innerHeight);
      renderer.setPixelRatio(window.devicePixelRatio);
      document.getElementById('container').appendChild(renderer.domElement);
      
      // 添加环境光
      const ambientLight = new THREE.AmbientLight(0xffffff, 0.5);
      scene.add(ambientLight);
      
      // 添加定向光（模拟太阳光）
      const directionalLight = new THREE.DirectionalLight(0xffffff, 1);
      directionalLight.position.set(5, 3, 5);
      scene.add(directionalLight);
      
      // 添加点光源（增强视觉效果）
      const pointLight = new THREE.PointLight(0x00a8ff, 0.8, 10);
      pointLight.position.set(-5, 2, -5);
      scene.add(pointLight);
      
      // 创建地球
      createEarth();
      
      // 创建南极洲高亮
      createAntarcticaHighlight();
      
      // 创建数据可视化层
      createDataLayers();
      
      // 创建站点标记
      createStations();
      
      // 添加控制器
      controls = new THREE.OrbitControls(camera, renderer.domElement);
      controls.enableDamping = true;
      controls.dampingFactor = 0.05;
      controls.rotateSpeed = 0.5;
      controls.minDistance = 1.5;
      controls.maxDistance = 10;
      
      // 添加事件监听器
      window.addEventListener('resize', onWindowResize);
      document.getElementById('focusAntarctica').addEventListener('click', focusAntarctica);
      document.getElementById('resetView').addEventListener('click', resetView);
      
      // 时间轴控制
      setupTimelineControls();
      
      // 图层控制
      setupLayerControls();
      
      // 隐藏加载提示
      setTimeout(() => {
        document.getElementById('loading').classList.add('hidden');
      }, 1500);
      
      // 开始动画循环
      animate();
      
      // 初始化时聚焦南极洲
      setTimeout(focusAntarctica, 2000);
    }
    
    function createEarth() {
      // 地球几何体
      const earthGeometry = new THREE.SphereGeometry(1, 64, 64);
      
      // 加载地球纹理
      const textureLoader = new THREE.TextureLoader();
      
      // 地球表面纹理（卫星图像）
      const earthTexture = textureLoader.load('https://cdn.jsdelivr.net/npm/three-globe/example/img/earth-blue-marble.jpg', function() {
        renderer.render(scene, camera);
      });
      
      // 地球凹凸纹理（地形）
      const bumpMap = textureLoader.load('https://cdn.jsdelivr.net/npm/three-globe/example/img/earth-topology.png', function() {
        renderer.render(scene, camera);
      });
      
      // 地球高光纹理（海洋反光）
      const specularMap = textureLoader.load('https://cdn.jsdelivr.net/npm/three-globe/example/img/earth-water.png', function() {
        renderer.render(scene, camera);
      });
      
      // 地球夜间光照纹理
      const nightMap = textureLoader.load('https://cdn.jsdelivr.net/npm/three-globe/example/img/earth-night.jpg', function() {
        renderer.render(scene, camera);
      });
      
      // 地球材质
      const earthMaterial = new THREE.MeshPhongMaterial({
        map: earthTexture,
        bumpMap: bumpMap,
        bumpScale: 0.05,
        specularMap: specularMap,
        specular: new THREE.Color(0x333333),
        shininess: 15
      });
      
      // 创建地球网格
      earth = new THREE.Mesh(earthGeometry, earthMaterial);
      scene.add(earth);
      
      // 添加云层
      const cloudsTexture = textureLoader.load('https://cdn.jsdelivr.net/npm/three-globe/example/img/earth-clouds.png', function() {
        renderer.render(scene, camera);
      });
      
      const cloudsMaterial = new THREE.MeshPhongMaterial({
        map: cloudsTexture,
        transparent: true,
        opacity: 0.4
      });
      
      clouds = new THREE.Mesh(
        new THREE.SphereGeometry(1.01, 64, 64),
        cloudsMaterial
      );
      
      scene.add(clouds);
      
      // 添加大气层光晕效果
      const atmosphereGeometry = new THREE.SphereGeometry(1.15, 64, 64);
      const atmosphereMaterial = new THREE.ShaderMaterial({
        vertexShader: `
          varying vec3 vNormal;
          void main() {
            vNormal = normalize(normalMatrix * normal);
            gl_Position = projectionMatrix * modelViewMatrix * vec4(position, 1.0);
          }
        `,
        fragmentShader: `
          varying vec3 vNormal;
          void main() {
            float intensity = pow(0.7 - dot(vNormal, vec3(0.0, 0.0, 1.0)), 2.0);
            gl_FragColor = vec4(0.1, 0.5, 1.0, 1.0) * intensity;
          }
        `,
        blending: THREE.AdditiveBlending,
        side: THREE.BackSide,
        transparent: true
      });
      
      const atmosphere = new THREE.Mesh(atmosphereGeometry, atmosphereMaterial);
      scene.add(atmosphere);
    }
    
    function createAntarcticaHighlight() {
      // 创建南极洲高亮（使用更精确的形状）
      const antarcticaGeometry = new THREE.CircleGeometry(0.3, 32);
      const antarcticaMaterial = new THREE.MeshBasicMaterial({
        color: 0x00a8ff,
        transparent: true,
        opacity: 0.5,
        side: THREE.DoubleSide
      });
      
      antarcticaHighlight = new THREE.Mesh(antarcticaGeometry, antarcticaMaterial);
      
      // 将南极洲高亮放置在地球底部
      antarcticaHighlight.position.set(0, -0.97, 0);
      antarcticaHighlight.rotation.x = Math.PI / 2;
      
      scene.add(antarcticaHighlight);
      
      // 添加一个发光效果
      const antarcticaGlowGeometry = new THREE.CircleGeometry(0.35, 32);
      const antarcticaGlowMaterial = new THREE.MeshBasicMaterial({
        color: 0x00a8ff,
        transparent: true,
        opacity: 0.3,
        side: THREE.DoubleSide
      });
      
      const antarcticaGlow = new THREE.Mesh(antarcticaGlowGeometry, antarcticaGlowMaterial);
      antarcticaGlow.position.set(0, -0.97, 0);
      antarcticaGlow.rotation.x = Math.PI / 2;
      
      scene.add(antarcticaGlow);
      
      // 添加脉冲动画效果
      const pulseTween = gsap.to(antarcticaGlowMaterial, {
        opacity: 0.1,
        duration: 1.5,
        repeat: -1,
        yoyo: true,
        ease: "sine.inOut"
      });
    }
    
    function createDataLayers() {
      // 创建温度分布图层
      const temperatureGeometry = new THREE.SphereGeometry(1.02, 64, 64);
      const temperatureMaterial = new THREE.MeshBasicMaterial({
        transparent: true,
        opacity: 0.6,
        map: createTemperatureTexture()
      });
      
      temperatureLayer = new THREE.Mesh(temperatureGeometry, temperatureMaterial);
      scene.add(temperatureLayer);
      
      // 创建风速图层（初始隐藏）
      const windGeometry = new THREE.SphereGeometry(1.02, 64, 64);
      const windMaterial = new THREE.MeshBasicMaterial({
        transparent: true,
        opacity: 0,
        map: createWindTexture()
      });
      
      windLayer = new THREE.Mesh(windGeometry, windMaterial);
      scene.add(windLayer);
      
      // 创建气压图层（初始隐藏）
      const pressureGeometry = new THREE.SphereGeometry(1.02, 64, 64);
      const pressureMaterial = new THREE.MeshBasicMaterial({
        transparent: true,
        opacity: 0,
        map: createPressureTexture()
      });
      
      pressureLayer = new THREE.Mesh(pressureGeometry, pressureMaterial);
      scene.add(pressureLayer);
    }
    
    function createTemperatureTexture() {
      // 创建温度分布纹理（南极洲区域的热力图）
      const canvas = document.createElement('canvas');
      canvas.width = 1024;
      canvas.height = 512;
      const ctx = canvas.getContext('2d');
      
      // 清空画布
      ctx.fillStyle = 'rgba(0, 0, 0, 0)';
      ctx.fillRect(0, 0, canvas.width, canvas.height);
      
      // 创建南极洲区域的温度分布
      const gradient = ctx.createRadialGradient(
        canvas.width / 2, 
        canvas.height * 0.85, 
        0, 
        canvas.width / 2, 
        canvas.height * 0.85, 
        canvas.width * 0.3
      );
      
      gradient.addColorStop(0, 'rgba(255, 63, 52, 0.7)');    // 中心较暖
      gradient.addColorStop(0.3, 'rgba(255, 168, 1, 0.6)');  // 中温区域
      gradient.addColorStop(0.6, 'rgba(0, 151, 230, 0.5)');  // 较冷区域
      gradient.addColorStop(1, 'rgba(0, 210, 211, 0.3)');    // 边缘最冷
      
      ctx.fillStyle = gradient;
      ctx.fillRect(0, 0, canvas.width, canvas.height);
      
      // 创建纹理
      const texture = new THREE.CanvasTexture(canvas);
      return texture;
    }
    
    function createWindTexture() {
      // 创建风速分布纹理
      const canvas = document.createElement('canvas');
      canvas.width = 1024;
      canvas.height = 512;
      const ctx = canvas.getContext('2d');
      
      // 清空画布
      ctx.fillStyle = 'rgba(0, 0, 0, 0)';
      ctx.fillRect(0, 0, canvas.width, canvas.height);
      
      // 创建南极洲区域的风速分布
      const gradient = ctx.createRadialGradient(
        canvas.width / 2, 
        canvas.height * 0.85, 
        0, 
        canvas.width / 2, 
        canvas.height * 0.85, 
        canvas.width * 0.3
      );
      
      gradient.addColorStop(0, 'rgba(0, 168, 255, 0.7)');
      gradient.addColorStop(0.5, 'rgba(0, 151, 230, 0.5)');
      gradient.addColorStop(1, 'rgba(0, 0, 0, 0)');
      
      ctx.fillStyle = gradient;
      ctx.fillRect(0, 0, canvas.width, canvas.height);
      
      // 添加风向箭头
      ctx.strokeStyle = 'rgba(255, 255, 255, 0.7)';
      ctx.lineWidth = 2;
      
      for (let i = 0; i < 20; i++) {
        const x = canvas.width / 2 + (Math.random() - 0.5) * canvas.width * 0.5;
        const y = canvas.height * 0.85 + (Math.random() - 0.5) * canvas.height * 0.3;
        const length = 10 + Math.random() * 20;
        const angle = Math.random() * Math.PI * 2;
        
        ctx.beginPath();
        ctx.moveTo(x, y);
        ctx.lineTo(x + Math.cos(angle) * length, y + Math.sin(angle) * length);
        ctx.stroke();
        
        // 箭头
        ctx.beginPath();
        ctx.moveTo(x + Math.cos(angle) * length, y + Math.sin(angle) * length);
        ctx.lineTo(
          x + Math.cos(angle) * length - Math.cos(angle + Math.PI / 4) * 5,
          y + Math.sin(angle) * length - Math.sin(angle + Math.PI / 4) * 5
        );
        ctx.stroke();
      }
      
      // 创建纹理
      const texture = new THREE.CanvasTexture(canvas);
      return texture;
    }
    
    function createPressureTexture() {
      // 创建气压分布纹理
      const canvas = document.createElement('canvas');
      canvas.width = 1024;
      canvas.height = 512;
      const ctx = canvas.getContext('2d');
      
      // 清空画布
      ctx.fillStyle = 'rgba(0, 0, 0, 0)';
      ctx.fillRect(0, 0, canvas.width, canvas.height);
      
      // 创建南极洲区域的气压分布
      const centerX = canvas.width / 2;
      const centerY = canvas.height * 0.85;
      
      // 绘制等压线
      ctx.strokeStyle = 'rgba(255, 168, 1, 0.5)';
      ctx.lineWidth = 1.5;
      
      for (let radius = 20; radius < canvas.width * 0.3; radius += 40) {
        ctx.beginPath();
        ctx.arc(centerX, centerY, radius, 0, Math.PI * 2);
        ctx.stroke();
      }
      
      // 添加高低压标记
      ctx.fillStyle = 'rgba(255, 63, 52, 0.7)';
      ctx.beginPath();
      ctx.arc(centerX, centerY, 15, 0, Math.PI * 2);
      ctx.fill();
      
      ctx.fillStyle = 'rgba(0, 151, 230, 0.7)';
      ctx.beginPath();
      ctx.arc(centerX + 100, centerY - 50, 15, 0, Math.PI * 2);
      ctx.fill();
      
      // 创建纹理
      const texture = new THREE.CanvasTexture(canvas);
      return texture;
    }
    
    function createStations() {
      // 南极洲观测站点数据
      const stationData = [
        { name: "中山站", lat: -69.3735, lon: 76.3725, temp: -28.5, wind: 9.8, humidity: 75 },
        { name: "长城站", lat: -62.2167, lon: -58.9667, temp: -15.2, wind: 12.3, humidity: 82 },
        { name: "昆仑站", lat: -80.4167, lon: 77.1167, temp: -42.8, wind: 5.6, humidity: 65 },
        { name: "泰山站", lat: -73.8614, lon: 76.9764, temp: -32.1, wind: 8.4, humidity: 70 }
      ];
      
      // 将站点添加到地球上
      stationData.forEach(station => {
        // 将经纬度转换为3D坐标
        const phi = (90 - station.lat) * (Math.PI / 180);
        const theta = (station.lon + 180) * (Math.PI / 180);
        
        const x = -1 * Math.sin(phi) * Math.cos(theta);
        const y = Math.cos(phi);
        const z = Math.sin(phi) * Math.sin(theta);
        
        // 创建站点标记
        const stationGeometry = new THREE.SphereGeometry(0.01, 16, 16);
        const stationMaterial = new THREE.MeshBasicMaterial({ color: 0x00a8ff });
        
        const stationMesh = new THREE.Mesh(stationGeometry, stationMaterial);
        stationMesh.position.set(x, y, z);
        stationMesh.scale.set(1, 1, 1);
        stationMesh.userData = station;
        
        scene.add(stationMesh);
        stations.push(stationMesh);
        
        // 添加发光效果
        const glowGeometry = new THREE.SphereGeometry(0.015, 16, 16);
        const glowMaterial = new THREE.MeshBasicMaterial({
          color: 0x00a8ff,
          transparent: true,
          opacity: 0.5
        });
        
        const glow = new THREE.Mesh(glowGeometry, glowMaterial);
        stationMesh.add(glow);
        
        // 添加脉冲动画
        gsap.to(glow.scale, {
          x: 1.5,
          y: 1.5,
          z: 1.5,
          duration: 1 + Math.random(),
          repeat: -1,
          yoyo: true,
          ease: "sine.inOut"
        });
      });
    }
    
    function setupTimelineControls() {
      const timelineSlider = document.getElementById('timeline-slider');
      const timelineProgress = document.getElementById('timeline-progress');
      const timelineHandle = document.getElementById('timeline-handle');
      
      // 设置时间轴初始位置
      timelineProgress.style.width = `${timelineProgress * 100}%`;
      timelineHandle.style.left = `${timelineProgress * 100}%`;
      
      // 添加时间轴拖动功能
      let isDragging = false;
      
      timelineSlider.addEventListener('mousedown', (e) => {
        isDragging = true;
        updateTimelinePosition(e);
      });
      
      document.addEventListener('mousemove', (e) => {
        if (isDragging) {
          updateTimelinePosition(e);
        }
      });
      
      document.addEventListener('mouseup', () => {
        isDragging = false;
      });
      
      // 播放/暂停控制
      document.getElementById('play-btn').addEventListener('click', () => {
        if (!isPlaying) {
          startPlayback();
        }
      });
      
      document.getElementById('pause-btn').addEventListener('click', () => {
        stopPlayback();
      });
    }
    
    function updateTimelinePosition(e) {
      const timelineSlider = document.getElementById('timeline-slider');
      const timelineProgress = document.getElementById('timeline-progress');
      const timelineHandle = document.getElementById('timeline-handle');
      
      const rect = timelineSlider.getBoundingClientRect();
      let progress = (e.clientX - rect.left) / rect.width;
      
      // 限制在0-1范围内
      progress = Math.max(0, Math.min(1, progress));
      
      // 更新进度条和手柄位置
      timelineProgress.style.width = `${progress * 100}%`;
      timelineHandle.style.left = `${progress * 100}%`;
      
      // 更新全局进度变量
      timelineProgress = progress;
      
      // 根据时间轴位置更新数据
      updateDataByTime(progress);
    }
    
    function startPlayback() {
      isPlaying = true;
      
      // 清除之前的定时器
      if (playInterval) {
        clearInterval(playInterval);
      }
      
      // 设置定时器，每100毫秒更新一次进度
      playInterval = setInterval(() => {
        const timelineProgress = document.getElementById('timeline-progress');
        const timelineHandle = document.getElementById('timeline-handle');
        
        // 增加进度
        timelineProgress += 0.005;
        
        // 如果到达末尾，重置到开始
        if (timelineProgress >= 1) {
          timelineProgress = 0;
        }
        
        // 更新UI
        timelineProgress.style.width = `${timelineProgress * 100}%`;
        timelineHandle.style.left = `${timelineProgress * 100}%`;
        
        // 更新数据
        updateDataByTime(timelineProgress);
      }, 100);
    }
    
    function stopPlayback() {
      isPlaying = false;
      
      if (playInterval) {
        clearInterval(playInterval);
        playInterval = null;
      }
    }
    
    function updateDataByTime(progress) {
      // 根据时间轴位置更新数据
      // 这里可以添加实际的数据更新逻辑
      
      // 示例：更新温度数据
      const baseTemp = -26.8;
      const tempVariation = Math.sin(progress * Math.PI * 2) * 5;
      const newTemp = (baseTemp + tempVariation).toFixed(1);
      
      document.querySelector('.data-panel .data-item:nth-child(2) .data-value').innerHTML = 
        `${newTemp}<span class="data-unit">°C</span>`;
      
      // 更新风速数据
      const baseWind = 8.6;
      const windVariation = Math.cos(progress * Math.PI * 2) * 3;
      const newWind = (baseWind + windVariation).toFixed(1);
      
      document.querySelector('.data-panel .data-item:nth-child(4) .data-value').innerHTML = 
        `${newWind}<span class="data-unit">m/s</span>`;
      
      // 更新云层旋转
      if (clouds) {
        clouds.rotation.y = progress * Math.PI * 2;
      }
    }
    
    function setupLayerControls() {
      // 温度图层控制
      document.getElementById('layer-temp').addEventListener('change', (e) => {
        if (e.target.checked) {
          gsap.to(temperatureLayer.material, { opacity: 0.6, duration: 0.5 });
          document.querySelector('.legend-title').textContent = '温度分布 (°C)';
          document.querySelector('.legend-gradient').style.background = 'linear-gradient(to right, #00d2d3, #00a8ff, #0097e6, #ffa801, #ff3f34)';
        } else {
          gsap.to(temperatureLayer.material, { opacity: 0, duration: 0.5 });
        }
      });
      
      // 风速图层控制
      document.getElementById('layer-wind').addEventListener('change', (e) => {
        if (e.target.checked) {
          gsap.to(windLayer.material, { opacity: 0.6, duration: 0.5 });
          gsap.to(temperatureLayer.material, { opacity: 0, duration: 0.5 });
          document.getElementById('layer-temp').checked = false;
          document.getElementById('layer-pressure').checked = false;
          document.querySelector('.legend-title').textContent = '风速分布 (m/s)';
          document.querySelector('.legend-gradient').style.background = 'linear-gradient(to right, #ffffff, #00a8ff, #0097e6)';
        } else {
          gsap.to(windLayer.material, { opacity: 0, duration: 0.5 });
        }
      });
      
      // 气压图层控制
      document.getElementById('layer-pressure').addEventListener('change', (e) => {
        if (e.target.checked) {
          gsap.to(pressureLayer.material, { opacity: 0.6, duration: 0.5 });
          gsap.to(temperatureLayer.material, { opacity: 0, duration: 0.5 });
          document.getElementById('layer-temp').checked = false;
          document.getElementById('layer-wind').checked = false;
          document.querySelector('.legend-title').textContent = '气压分布 (hPa)';
          document.querySelector('.legend-gradient').style.background = 'linear-gradient(to right, #0097e6, #ffa801, #ff3f34)';
        } else {
          gsap.to(pressureLayer.material, { opacity: 0, duration: 0.5 });
        }
      });
      
      // 站点图层控制
      document.getElementById('layer-stations').addEventListener('change', (e) => {
        stations.forEach(station => {
          station.visible = e.target.checked;
        });
      });
      
      // 云层控制
      document.getElementById('layer-clouds').addEventListener('change', (e) => {
        if (e.target.checked) {
          gsap.to(clouds.material, { opacity: 0.4, duration: 0.5 });
        } else {
          gsap.to(clouds.material, { opacity: 0, duration: 0.5 });
        }
      });
    }
    
    function focusAntarctica() {
      // 动画过渡到南极洲视角
      gsap.to(camera.position, {
        x: 0,
        y: -3,
        z: 0.5,
        duration: 2,
        ease: "power2.inOut",
        onUpdate: function() {
          camera.lookAt(0, 0, 0);
        }
      });
      
      // 显示站点信息
      setTimeout(() => {
        document.getElementById('station-info').classList.add('visible');
      }, 2000);
    }
    
    function resetView() {
      // 动画过渡到默认视角
      gsap.to(camera.position, {
        x: 0,
        y: 0,
        z: 3,
        duration: 2,
        ease: "power2.inOut",
        onUpdate: function() {
          camera.lookAt(0, 0, 0);
        }
      });
      
      // 隐藏站点信息
      document.getElementById('station-info').classList.remove('visible');
    }
    
    function onWindowResize() {
      camera.aspect = window.innerWidth / window.innerHeight;
      camera.updateProjectionMatrix();
      renderer.setSize(window.innerWidth, window.innerHeight);
    }
    
    function animate() {
      requestAnimationFrame(animate);
      
      // 缓慢旋转地球（当不在南极洲视角时）
      if (camera.position.y > -2) {
        earth.rotation.y += 0.0005;
        if (clouds) {
          clouds.rotation.y += 0.0008;
        }
      }
      
      // 更新控制器
      controls.update();
      
      // 更新时间
      updateTime();
      
      // 渲染场景
      renderer.render(scene, camera);
    }
    
    function updateTime() {
      // 更新当前时间显示
      const now = new Date();
      const hours = now.getHours().toString().padStart(2, '0');
      const minutes = now.getMinutes().toString().padStart(2, '0');
      const seconds = now.getSeconds().toString().padStart(2, '0');
      
      document.getElementById('current-time').textContent = 
        `星期五 ${hours}:${minutes}:${seconds}`;
    }
    
    // 添加射线检测，用于点击站点显示信息
    const raycaster = new THREE.Raycaster();
    const mouse = new THREE.Vector2();
    
    window.addEventListener('click', (event) => {
      // 计算鼠标位置的标准化设备坐标
      mouse.x = (event.clientX / window.innerWidth) * 2 - 1;
      mouse.y = -(event.clientY / window.innerHeight) * 2 + 1;
      
      // 更新射线
      raycaster.setFromCamera(mouse, camera);
      
      // 检测射线与站点的交叉
      const intersects = raycaster.intersectObjects(stations);
      
      if (intersects.length > 0) {
        const station = intersects[0].object.userData;
        
        // 更新站点信息面板
        document.querySelector('.station-name').textContent = station.name;
        document.querySelector('.station-coords').textContent = 
          `${Math.abs(station.lat)}°${station.lat < 0 ? 'S' : 'N'}, ${Math.abs(station.lon)}°${station.lon < 0 ? 'W' : 'E'}`;
        
        document.querySelector('.station-info .data-item:nth-child(2) .data-value').innerHTML = 
          `${station.temp}<span class="data-unit">°C</span>`;
        
        document.querySelector('.station-info .data-item:nth-child(3) .data-value').innerHTML = 
          `${station.wind}<span class="data-unit">m/s</span>`;
        
        document.querySelector('.station-info .data-item:nth-child(4) .data-value').innerHTML = 
          `${station.humidity}<span class="data-unit">%</span>`;
        
        // 显示站点信息面板
        document.getElementById('station-info').classList.add('visible');
      }
    });
  </script>
</body>
</html>

    
```
