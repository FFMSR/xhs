# 小红书API服务文档

[![GitHub stars](https://img.shields.io/github/stars/FFMSR/xhs/?style=social)](https://github.com/FFMSR/xhs/)
[![GitHub forks](https://img.shields.io/github/forks/FFMSR/xhs/?style=social)](https://github.com/FFMSR/xhs/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

> 专业、稳定、高效的小红书数据接口解决方案

## 🚀 快速开始

小红书API服务提供了完整的数据获取和互动操作接口，支持获取笔记详情、用户信息、评论数据等功能。

### 基本使用

```javascript
// 获取笔记详情
const response = await fetch('https://xhs.com/api/get_notes', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'X-API-Token': 'your_token_here'
  },
  body: JSON.stringify({
    cookie: 'your_cookie_here',
    source_note_id: 'note_id_here',
    xsec_token: 'your_xsec_token'
  })
});

const data = await response.json();
console.log(data);
```

## 📚 API文档导航

### 🔐 基础信息
- [认证说明](docs/authentication.md) - Token使用方法和安全实践
- [Token管理](docs/token.md) - Token状态查询和管理
- [错误码说明](docs/errors.md) - 完整的错误处理指南

### 📖 内容获取接口
- [获取评论](api/get-comments.md) - 获取笔记评论列表，支持分页
- [获取笔记详情](api/get-notes.md) - 获取笔记详细信息，包括内容、图片、作者信息
- [搜索笔记](api/search-notes.md) - 根据关键词搜索笔记，支持多种筛选条件

### 👤 用户数据接口
- [获取用户信息](api/get-user-info.md) - 获取用户基本信息和统计数据
- [获取用户笔记](api/get-user-notes.md) - 获取指定用户发布的所有笔记

### 💬 互动操作接口
- [发送评论](api/post-comment.md) - 在指定笔记下发表评论
- [点赞笔记](api/like-note.md) - 对笔记进行点赞或取消点赞
- [收藏笔记](api/collect-note.md) - 将笔记添加到收藏夹
- [点赞评论](api/like-comment.md) - 对评论进行点赞操作

## 🎯 使用指南

### 📋 快速入门
- [快速开始](guide/getting-started.md) - 5分钟快速体验指南
- [最佳实践](guide/best-practices.md) - 安全、性能、监控最佳实践
- [常见问题](guide/faq.md) - 详细的FAQ解答

### 🔧 技术文档
- [部署指南](guide/deployment.md) - 服务部署和配置说明
- [错误处理](guide/error-handling.md) - 错误处理和调试技巧

## 💰 计费说明

- **定价**: 1元 = 100次请求
- **计费规则**: 只有当小红书API返回成功时才扣除积分
- **失败保障**: 失败请求不计费，确保您的每一分钱都花得值

## 🔑 获取Token

请通过以下方式联系我们获取API Token：

- 📱 **微信客服**: xiaohongshu_api
- 💬 **QQ客服**: 123456789  
- 📧 **邮箱支持**: support@xiaohongshu-api.com
- 🔗 **Telegram**: @xiaohongshu_api

## 📊 接口概览

| 接口类型 | 接口数量 | 主要功能 |
|---------|---------|----------|
| 内容获取 | 3个 | 获取笔记、评论、搜索 |
| 用户数据 | 2个 | 用户信息、用户笔记 |
| 互动操作 | 4个 | 评论、点赞、收藏 |
| **总计** | **9个** | **完整的小红书数据解决方案** |

## 🌟 特色功能

### ✅ 完整的数据获取
- 笔记详情（标题、内容、图片、视频）
- 用户信息（昵称、头像、粉丝数、关注数）
- 互动数据（点赞数、收藏数、评论数）
- 评论列表（支持分页获取）

### ✅ 强大的搜索功能
- 关键词搜索
- 多种排序方式（综合、最新、最热）
- 内容类型筛选（图文、视频）
- 时间范围筛选

### ✅ 完整的互动操作
- 发表评论（支持@用户）
- 点赞笔记和评论
- 收藏笔记
- 自动化互动支持

## 🔒 安全保障

- **Token认证**: 每个请求都需要有效的Token
- **请求加密**: 支持HTTPS安全传输
- **频率限制**: 智能频率控制，避免被封
- **错误重试**: 自动重试机制，提高成功率

## 📈 性能优势

- **高并发**: 支持大量并发请求
- **低延迟**: 平均响应时间 < 2秒
- **高可用**: 99.9% 服务可用性
- **智能缓存**: 减少重复请求，提升效率

## 🛠️ 开发工具

### 支持的编程语言
- JavaScript/Node.js
- Python
- PHP
- Java
- Go
- 其他支持HTTP请求的语言

### 示例代码
每个API接口都提供了多种语言的示例代码：
- cURL命令
- JavaScript/Node.js
- Python requests
- 其他常用语言

### 联系方式
- 📱 **微信客服**: xiaohongshu_api（工作时间：9:00-22:00）
- 💬 **QQ客服**: 3270502
- 🔗 **Telegram**: @wtm30124（即时技术支持）
