# 小红书API服务文档

## 项目概述

小红书Web x-s、x-t、x-s-common 算法 支持获取笔记评论、获取笔记详情、获取用户发布的笔记、搜索笔记、获取用户信息、发送评论、收藏笔记、点赞评论

### 主要功能
- 获取笔记评论和详情
- 用户信息查询和笔记搜索
- 互动功能（点赞、收藏、评论）

### 🚀 支持的接口列表

| 接口 | 功能 | 方法 |
|------|------|------|
| `/api/get_comments` | 获取笔记评论 | POST |
| `/api/get_notes` | 获取笔记详情 | POST |
| `/api/get_user_notes` | 获取用户发布的笔记 | POST |
| `/api/search_notes` | 搜索笔记 | POST |
| `/api/get_user_info` | 获取用户信息 | POST |
| `/api/post_comment` | 发送评论 | POST |
| `/api/like_note` | 点赞笔记 | POST |
| `/api/collect_note` | 收藏笔记 | POST |
| `/api/like_comment` | 点赞评论 | POST |
| `/api/token/:token` | 查询Token信息 | GET |

## 作者提供的服务
- 1.在线获取xs、xt、x-s-common、xhs数据等
- 2.提供逆向源码，js Python都有
- 3.可出售整个api接口系统源码，搭建和我一样的系统，体验地址联系我

## 性能
api接口采用js计算，请求rt百毫秒级

## API接口

### Token认证
所有API调用都需要有效的Token进行认证。Token可以通过以下方式提供：

1. **请求头方式**（推荐）：
   ```
   X-API-Token: your_token_here
   ```

2. **Authorization头方式**：
   ```
   Authorization: Bearer your_token_here
   ```

3. **请求体方式**：
   ```json
   {
     "token": "your_token_here",
     "other_params": "..."
   }
   ```

### Token状态
- `active`: 有效状态，可正常使用
- `inactive`: 无效状态，无法使用
- `expired`: 已过期，需要续费
- `suspended`: 已暂停，联系管理员

## 基础信息

### 服务地址
```
Base URL: http://xhs.com
```

### 通用请求头
```
Content-Type: application/json
X-API-Token: your_token_here
```

### 通用响应格式
```json
{
  "success": true,
  "data": {},
  "error": "错误信息（仅在失败时）",
  "code": "错误代码（仅在失败时）"
}
```

## API端点详情

### 1. 获取笔记评论

**端点**: `POST /api/get_comments`

**描述**: 获取指定笔记的评论列表

**请求参数**:
```json
{
  "cookie": "小红书登录Cookie（必需）",
  "note_id": "笔记ID（必需）",
  "cursor": "分页游标（可选，默认为空）",
  "xsec_token": "安全令牌（必需）"
}
```

**响应示例**:
```json
{
  "success": true,
  "data": {
    "comments": [
      {
        "id": "评论ID",
        "content": "评论内容",
        "user_info": {
          "user_id": "用户ID",
          "nickname": "用户昵称"
        },
        "create_time": "创建时间",
        "like_count": 10
      }
    ],
    "cursor": "下一页游标",
    "has_more": true
  }
}
```

### 2. 获取笔记详情

**端点**: `POST /api/get_notes`

**描述**: 获取指定笔记的详细信息

**请求参数**:
```json
{
  "cookie": "小红书登录Cookie（必需）",
  "source_note_id": "笔记ID（必需）",
  "xsec_token": "安全令牌（必需）"
}
```

**响应示例**:
```json
{
  "success": true,
  "data": {
    "note_info": {
      "note_id": "笔记ID",
      "title": "笔记标题",
      "desc": "笔记描述",
      "user": {
        "user_id": "作者ID",
        "nickname": "作者昵称"
      },
      "interact_info": {
        "liked_count": "点赞数",
        "collected_count": "收藏数",
        "comment_count": "评论数"
      },
      "image_list": ["图片URL列表"]
    }
  }
}
```

### 3. 获取用户发布的笔记

**端点**: `POST /api/get_user_notes`

**描述**: 获取指定用户发布的笔记列表

**请求参数**:
```json
{
  "cookie": "小红书登录Cookie（必需）",
  "user_id": "用户ID（必需）",
  "cursor": "分页游标（可选，默认为空）"
}
```

### 4. 搜索笔记

**端点**: `POST /api/search_notes`

**描述**: 根据关键词搜索笔记

**请求参数**:
```json
{
  "cookie": "小红书登录Cookie（必需）",
  "keyword": "搜索关键词（必需）",
  "page": 1,
  "search_id": "搜索会话ID（必需）",
  "sort_type": "排序类型（可选，默认general）",
  "filter_type": "内容类型过滤（可选，默认不限）",
  "filter_time": "时间过滤（可选，默认不限）",
  "filter_range": "范围过滤（可选，默认不限）",
  "filter_distance": "距离过滤（可选，默认不限）"
}
```

### 5. 获取用户信息

**端点**: `POST /api/get_user_info`

**描述**: 获取指定用户的详细信息

**请求参数**:
```json
{
  "cookie": "小红书登录Cookie（必需）",
  "target_user_id": "目标用户ID（必需）"
}
```

### 6. 发送评论

**端点**: `POST /api/post_comment`

**描述**: 在指定笔记下发送评论

**请求参数**:
```json
{
  "cookie": "小红书登录Cookie（必需）",
  "note_id": "笔记ID（必需）",
  "content": "评论内容（必需）",
  "at_users": ["@用户列表（可选，默认为空数组）"]
}
```

### 7. 点赞笔记

**端点**: `POST /api/like_note`

**描述**: 对指定笔记进行点赞操作

**请求参数**:
```json
{
  "cookie": "小红书登录Cookie（必需）",
  "note_id": "笔记ID（必需）"
}
```

### 8. 收藏笔记

**端点**: `POST /api/collect_note`

**描述**: 收藏指定笔记

**请求参数**:
```json
{
  "cookie": "小红书登录Cookie（必需）",
  "note_id": "笔记ID（必需）"
}
```

### 9. 点赞评论

**端点**: `POST /api/like_comment`

**描述**: 对指定评论进行点赞

**请求参数**:
```json
{
  "cookie": "小红书登录Cookie（必需）",
  "note_id": "笔记ID（必需）",
  "comment_id": "评论ID（必需）"
}
```

### 10. 查询Token信息

**端点**: `GET /api/token/{token}`

**描述**: 查询指定Token的详细信息和使用状态

**响应示例**:
```json
{
  "success": true,
  "data": {
    "token": "token值",
    "user_name": "用户名",
    "remaining_requests": 950,
    "total_requests": 1000,
    "used_requests": 50,
    "status": "active",
    "is_valid": true,
    "is_expired": false,
    "created_at": "2024-01-01T00:00:00.000Z",
    "expires_at": "2024-02-01T00:00:00.000Z",
    "last_used_at": "2024-01-15T10:30:00.000Z",
    "description": "Token描述"
  }
}
```

## 错误处理

### 常见错误代码

| 状态码 | 错误代码 | 描述 | 解决方案 |
|--------|----------|------|----------|
| 400 | MISSING_PARAMS | 缺少必需参数 | 检查请求参数完整性 |
| 401 | MISSING_TOKEN | 缺少Token | 在请求头或请求体中提供Token |
| 401 | INVALID_TOKEN | Token无效 | 检查Token是否正确 |
| 401 | TOKEN_INACTIVE | Token已停用 | 联系管理员激活Token |
| 401 | TOKEN_EXPIRED | Token已过期 | 续费或申请新Token |
| 402 | INSUFFICIENT_REQUESTS | 积分不足 | 充值或购买更多积分 |
| 500 | SERVER_ERROR | 服务器内部错误 | 联系技术支持 |

### 错误响应格式
```json
{
  "success": false,
  "error": "具体错误信息",
  "code": "错误代码",
  "remaining_requests": 剩余积分数
}
```

### 小红书API错误
当小红书API返回错误时，服务会透传原始错误信息：
```json
{
  "success": false,
  "msg": "小红书API错误信息",
  "code": -1
}
```

## 使用示例

### cURL示例

#### 1. 获取笔记评论
```bash
curl -X POST http://xhs.com/api/get_comments \
  -H "Content-Type: application/json" \
  -H "X-API-Token: your_token_here" \
  -d '{
    "cookie": "your_xiaohongshu_cookie",
    "note_id": "64a1b2c3d4e5f6789",
    "xsec_token": "your_xsec_token",
    "cursor": ""
  }'
```

#### 2. 查询Token信息
```bash
curl -X GET http://xhs.com/api/token/your_token_here
```

#### 3. 健康检查
```bash
curl -X GET http://xhs.com/health
```

### JavaScript示例

```javascript
// 使用fetch API调用
const apiCall = async () => {
  try {
    const response = await fetch('http://xhs.com/api/get_comments', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'X-API-Token': 'your_token_here'
      },
      body: JSON.stringify({
        cookie: 'your_xiaohongshu_cookie',
        note_id: '64a1b2c3d4e5f6789',
        xsec_token: 'your_xsec_token',
        cursor: ''
      })
    });

    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('API调用失败:', error);
  }
};
```

### Python示例

```python
import requests
import json

# API配置
BASE_URL = "http://xhs.com"
TOKEN = "your_token_here"

# 请求头
headers = {
    "Content-Type": "application/json",
    "X-API-Token": TOKEN
}

# 获取笔记评论
def get_comments(note_id, cookie, xsec_token, cursor=""):
    url = f"{BASE_URL}/api/get_comments"
    data = {
        "cookie": cookie,
        "note_id": note_id,
        "xsec_token": xsec_token,
        "cursor": cursor
    }

    response = requests.post(url, headers=headers, json=data)
    return response.json()

# 查询Token信息
def get_token_info(token):
    url = f"{BASE_URL}/api/token/{token}"
    response = requests.get(url)
    return response.json()

# 使用示例
if __name__ == "__main__":
    # 获取评论
    comments = get_comments(
        note_id="64a1b2c3d4e5f6789",
        cookie="your_xiaohongshu_cookie",
        xsec_token="your_xsec_token"
    )
    print(json.dumps(comments, indent=2, ensure_ascii=False))

    # 查询Token信息
    token_info = get_token_info(TOKEN)
    print(f"剩余积分: {token_info['data']['remaining_requests']}")
```

## 联系方式
- 接口联系: 3270502
- 文档更新: 请关注项目GitHub仓库
- 问题反馈: 通过GitHub Issues提交
---

**重要声明**:
1. 本API服务仅供学习和研究使用
2. 请遵守小红书平台的使用条款和相关法律法规
3. 不得用于商业用途或恶意爬取
4. 使用者需自行承担使用风险

**版本信息**: v1.0.0
**最后更新**: 2025年7月25日

### 引流：
小红书爬虫，小红书采集，小红书数据，小红书账号，小红书逆向，小红书web，小红书app

小红书主页，小红书笔记，小红书作者页，小红书搜索，小红书发送笔记，小红书关注，小红书点赞，小红书评论，小红书作品。

批量发笔记，批量点赞，批量关注，批量评论，x-legacy-smid、x-legacy-did、x-legacy-fid、x-legacy-sid、x-mini-gid、x-mini-sig、x-mini-mua、xy-common-params、xy-platform-info、main_hmac

2025年05月26日更新
