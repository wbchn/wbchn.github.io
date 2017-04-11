<!---
title: Zeppelin
header: Zeppelin
--->

[官方资料](https://zeppelin.apache.org)

下面安装了 zeppelin 0.7.1，以 0.7.1 版本为例。


----


## 认证权限

Security: available security support in Apache Zeppelin
[Authentication for NGINX](https://zeppelin.apache.org/docs/0.7.1/security/authentication.html)
[Shiro Authentication](https://zeppelin.apache.org/docs/0.7.1/security/shiroauthentication.html)
[Notebook Authorization](https://zeppelin.apache.org/docs/0.7.1/security/notebook_authorization.html)
[Data Source Authorization](https://zeppelin.apache.org/docs/0.7.1/security/datasource_authorization.html)

这里使用 Shiro 来做认证：

### Shiro 认证
配置比较简单，在两个配置文件中做修改：
1. shiro.ini

**添加用户**
```
[users]
# List of users with their password allowed to access Zeppelin.
# To use a different strategy (LDAP / Database / ...) check the shiro doc at http://shiro.apache.org/configuration.html#Configuration-INISections
admin = superpassword, admin
visitor = password, user
# user3 = password4, role2
```

**配置权限**
> /api/interpreter/setting/restart/** = authc  允许普通用户重启`interpreter`
```
[urls]
# anon means the access is anonymous.
# authcBasic means Basic Auth Security
# authc means Form based Auth Security
# To enfore security, comment the line below and uncomment the next one
/api/version = anon
/api/interpreter/setting/restart/** = authc
/api/interpreter/** = authc, roles[admin]
/api/configurations/** = authc, roles[admin]
/api/credential/** = authc, roles[admin]
/** = authc
```

2. zeppelin-site.xml
找到 `zeppelin.anonymous.allowed` 修改为 `false`，即不允许匿名访问。

重启zeppelin，右上角将出现 `Login`的按钮。

