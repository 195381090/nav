# 拾光集 - 精品网址导航站

<p align="center">
  <img src="https://www.wangwangit.com/img/favicon.webp" alt="拾光集Logo" width="200">
</p>


<p align="center">
  一个优雅的书签收藏与分享平台，基于Cloudflare Workers构建
</p>

<p align="center">
  <a href="#✨-特性">特性</a> •
  <a href="#🚀-快速开始">快速开始</a> •
  <a href="#📦-部署指南">部署指南</a> •
  <a href="#🔧-技术栈">技术栈</a> •
  <a href="#🌟-贡献">贡献</a>
</p>

## ✨ 特性

- 📱 **响应式设计** - 完美适配各种设备屏幕
- 📋 **分类浏览** - 按类别组织书签，简单直观
- 🔍 **站内搜索** - 快速查找需要的网站
- 📝 **书签提交** - 用户可申请添加新书签
- 🛡️ **审核机制** - 管理员审批流程保证内容质量
- 🔒 **安全认证** - 支持KV存储保存管理员凭据
- 📊 **后台管理** - 完整的书签管理界面
- 📤 **导入导出** - 支持批量导入导出书签

## 🖼️ 预览图

![image-20250428165157470.png](https://img.wangwango.me/file/1745887672724_image-20250428165157470.png)

![image-20250428165221411.png](https://img.wangwango.me/file/1745887688601_image-20250428165221411.png)

## 🚀 快速开始

### 在线体验

访问示例网站：https://nav.wangwangit.com

管理员入口：https://nav.wangwangit.com/admin

> **注意**: 示例站点仅供演示，请勿提交敏感信息

## 📦 部署指南

### 步骤 1: 创建DB数据库和KV键值对

创建D1数据库,输入名称**book** ,点击创建!

![image-20250428165900854.png](https://img.wangwango.me/file/1745887730401_image-20250428165900854.png)

点击控制台,分别创建表**sites**,**pending_sites**,看下图字段!

![image-20250428170500147.png](https://img.wangwango.me/file/1745887778749_image-20250428170500147.png)

![image-20250428170554713.png](https://img.wangwango.me/file/1745887766412_image-20250428170554713.png)

创建KV,名称**NAV_AUTH**,根据自己实际情况修改密钥的值,这是后续用于登陆后台管理的账号密码!

![image-20250428170648030.png](https://img.wangwango.me/file/1745887794533_image-20250428170648030.png)

![image-20250428170820688.png](https://img.wangwango.me/file/1745887835068_image-20250428170820688.png)

### 步骤 2: 创建workers

看下图,点击hello worker创建一个workers,输入自定义名称进行创建!

![image-20250428171210030.png](https://img.wangwango.me/file/1745887862851_image-20250428171210030.png)

然后点击编辑代码,将本项目中的worker.js代码复制粘贴进去,替换原有代码,点击部署!

![image-20250428171351061.png](https://img.wangwango.me/file/1745887887776_image-20250428171351061.png)

然后前往设置中,绑定KV和DB

![image-20250428171621951.png](https://img.wangwango.me/file/1745887901043_image-20250428171621951.png)

然后访问页面即可,此时由于没有添加书签,访问首页会提示没有数据,可以前往admin后台登陆之后,添加一个书签,即可看到页面!

![image-20250428172320000.png](https://img.wangwango.me/file/1745887918992_image-20250428172320000.png)

页面提示这个信息!

![image-20250428172204575.png](https://img.wangwango.me/file/1745887932630_image-20250428172204575.png)

网址后面拼接 /admin 即可进入后台页面,输入在DB中设置的密码,然后进行添加!

![image-20250428172455849.png](https://img.wangwango.me/file/1745887961338_image-20250428172455849.png)

再回到首页,就能看到网站了!

![image-20250428172518433.png](https://img.wangwango.me/file/1745887973348_image-20250428172518433.png)



## 🔧 技术栈

- [Cloudflare Workers](https://workers.cloudflare.com/) - 边缘计算平台
- [Cloudflare D1](https://developers.cloudflare.com/d1/) - 边缘SQL数据库
- [Cloudflare KV](https://developers.cloudflare.com/workers/runtime-apis/kv/) - 键值存储
- [TailwindCSS](https://tailwindcss.com/) - 实用程序优先的CSS框架

## 💻 项目结构

```
nav/
├── worker.js          # 主应用代码
├── schema.sql         # 数据库结构
└── README.md          # 项目文档
```

## 🛠️ 自定义开发

### 修改样式和主题

编辑`worker.js`中的TailwindCSS配置部分：

```js
tailwind.config = {
  theme: {
    extend: {
      colors: {
        primary: {
          // 修改主色调
          500: '#7209b7',
        },
        // ...其他颜色配置
      },
    }
  }
}
```

### 添加自定义功能

本项目使用Cloudflare Workers的单文件结构，所有逻辑都在`worker.js`中。主要模块:

- `api`: API请求处理
- `admin`: 管理后台逻辑
- `handleRequest`: 前端页面渲染

## 🌟 贡献

欢迎贡献代码，提交问题或者建议！

1. Fork 仓库
2. 创建你的功能分支 (`git checkout -b feature/amazing-feature`)
3. 提交更改 (`git commit -m '添加一些令人惊叹的功能'`)
4. 推送到分支 (`git push origin feature/amazing-feature`)
5. 开启一个Pull Request

## 📄 许可证

本项目采用 MIT 许可证 - 详情参见 [LICENSE](LICENSE) 文件

## 📞 联系方式

项目作者 - [@一只会飞的旺旺](https://github.com/wangwangit)

项目链接: [https://github.com/wangwangit/nav](https://github.com/wangwangit/nav)

---

<p align="center">如果你喜欢这个项目，别忘了给它一个⭐️!</p>
