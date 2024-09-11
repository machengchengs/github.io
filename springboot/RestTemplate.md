RestTemplate  发送请求
---
> 是 Spring 框架提供的一个用于同步客户端 HTTP 访问的类。
> 提供了常见 HTTP 方法（如 GET、POST、PUT、DELETE 等）的支持。
> RestTemplate 隐藏了底层的 HTTP 库（如 Apache HttpComponents、OkHttp 等）的复杂性，使得开发者可以更方便地进行 HTTP 请求和响应的处理。

## 主要功能

- 发送 HTTP 请求：

  支持 GET、POST、PUT、DELETE、HEAD、OPTIONS、PATCH 等 HTTP 方法。

- 处理 HTTP 响应：

  可以将 HTTP 响应自动转换为 Java 对象，支持 JSON、XML 等格式。（依赖于java某个接口类）

- 请求参数和头信息：

  支持设置请求参数、请求头、请求体等。

- 异常处理：

  提供了对 HTTP 状态码的异常处理机制。

## 使用示例
1. 创建 RestTemplate Bean
首先，确保在 Spring Boot 配置中定义了 RestTemplate Bean

```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.client.RestTemplate;

@Configuration
public class AppConfig {

    @Bean
    public RestTemplate restTemplate() {
        return new RestTemplate();
    }
}
```
2. 使用 RestTemplate 发送 GET 请求
```java
package com.tribe.store.util;

import com.tribe.store.config.WechatConfig;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;
import org.springframework.web.client.RestTemplate;

import java.util.HashMap;
import java.util.Map;

@Component
public class WechatUtil {

    public static final String OAUTH2_BASE = "https://api.weixin.qq.com/sns/";
    private final WechatConfig wechatConfig;
    private final RestTemplate restTemplate;

    @Autowired
    public WechatUtil(WechatConfig wechatConfig, RestTemplate restTemplate) {
        this.wechatConfig = wechatConfig;
        this.restTemplate = restTemplate;
    }

    public String getToken(String code) {
        // 构建请求参数
        Map<String, String> params = new HashMap<>();
        params.put("appid", wechatConfig.getAppId());
        params.put("secret", wechatConfig.getAppSecret());
        params.put("js_code", code);
        params.put("grant_type", "authorization_code");

        // 拼接 URL，参数通过模板传递
        String url = OAUTH2_BASE + "jscode2session?appid={appid}&secret={secret}&js_code={js_code}&grant_type={grant_type}";

        // 使用 RestTemplate 发送 GET 请求并获取响应
        String response = restTemplate.getForObject(url, String.class, params);

        // 返回响应数据（这里可能是 JSON 格式，需要解析）
        return response;
    }
}
```

