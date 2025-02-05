# API 鉴权文档

## 认证方式

### Access Token

**请求头中的 `Authorization` 字段**

    将 Access Token 放置于 HTTP 请求头部的 `Authorization` 字段中，格式如下：

    ```
    Authorization: <your_access_token>
    ```

    其中 `<your_access_token>` 需要替换为实际的 Access Token 值。


    将用户 ID 放置于 HTTP 请求头部的 `New-Api-User` 字段中，格式如下：

    ```
    New-Api-User: <your_user_id>
    ```

    其中 `<your_user_id>` 需要替换为实际的用户 ID。

**注意：**
*   如果用户已被禁用，则会返回 `403 Forbidden` 错误，并提示“用户已被封禁”。
*   如果用户权限不足，则会返回 `403 Forbidden` 错误，并提示“无权进行此操作，权限不足”。
*   如果用户信息无效，则会返回 `403 Forbidden` 错误，并提示“无权进行此操作，用户信息无效”。

## Curl 示例

假设您的 Access Token 为 `access_token`，要访问的 API 接口为 `/api/user/self`，则可以使用以下 curl 命令：

```bash
curl -X GET \
  -H "Authorization: access_token" \
  https://your-domain.com/api/user/self
```

请将 `access_token`、 和 `https://your-domain.com` 替换为实际的值。

