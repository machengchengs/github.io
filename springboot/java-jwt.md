## JSON WEB TOKEN
>java-jwt 是一个流行的 Java 库，用于创建和验证 JSON Web Tokens (JWTs)。
>
>JWT 是一种用于在网络应用环境中传递声明的开放标准（RFC 7519）。它通常用于身份验证和授权。

## 引入依赖

```xml
<dependency>
    <groupId>com.auth0</groupId>
    <artifactId>java-jwt</artifactId>
</dependency>
```

## encode & decode

```java
package com.tribe.store.util;

import com.auth0.jwt.JWT;
import com.auth0.jwt.algorithms.Algorithm;
import com.auth0.jwt.exceptions.JWTDecodeException;
import com.auth0.jwt.interfaces.Claim;
import com.auth0.jwt.interfaces.DecodedJWT;
import com.auth0.jwt.interfaces.Verification;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.boot.autoconfigure.security.oauth2.resource.OAuth2ResourceServerProperties;
import org.springframework.stereotype.Component;

import java.time.LocalDateTime;
import java.time.ZoneId;
import java.time.temporal.ChronoUnit;
import java.util.Date;
import java.util.Map;

public class JWTUtil {
    // 获取用于签名的密钥
    @Value("${jwt.secret}")
    private static String HMAC_SECRET;
    // 编码生成JWT令牌
    public static String encode(Map<String, Object> payload) {
        LocalDateTime expirationTime = LocalDateTime.now().plus(2, ChronoUnit.WEEKS);
        Date expirationDate = Date.from(expirationTime.atZone(ZoneId.systemDefault()).toInstant());

        return JWT.create().withPayload(payload).withExpiresAt(expirationDate).sign(Algorithm.HMAC256(HMAC_SECRET));
    }

    // 解码JWT令牌
    public static Map<String, Claim> decode(String token) {
        try {
            DecodedJWT decodedJWT = JWT.require(Algorithm.HMAC256(HMAC_SECRET))
                    .build()
                    .verify(token);
            return decodedJWT.getClaims(); // 返回解码后的负载信息
        } catch (JWTDecodeException e) {
            throw new RuntimeException("Invalid token: " + e.getMessage()); // 自定义异常处理
        }
    }
}
```
