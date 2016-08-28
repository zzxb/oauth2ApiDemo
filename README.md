这是一个基于oauth2设计的Spring restful安全的api案例，只为提供为ios/android等客户端提供安全的api设计参考,参考了微信api设计方式,主要提供client_credentials,password授权方式
- SpringMVC
- Spring Security
- Spring Security oauth

## 名词解释

#### Oauth2干什么用？   

我的理解是：新浪微博就是你的家。偶尔你会想让一些人（第三方应用）去你的家里帮你做一些事，或取点东西。你可以复制一把钥匙（用户名和密码）给他们，但这里有三个问题： 

1. 别人拿了钥匙后可以去所有的房间 
2. 别人拿到你的钥匙后也许会不小心丢到，甚至故意送到它人手里。这样你都不知到谁有你家钥匙。 
3. 过一段时间你也许会想要回自己的钥匙，但别人不还怎么办？ 



OAuth 是高级钥匙:

1.你可以配置不同权限的钥匙。有些只能进大厅（读取你的微博流）。有些钥匙可以进储藏柜（读取你的相片)                                     
2.钥匙上带着指纹验证的（指纹 = appkey)。收到钥匙的人只能自己用，不能转让     
3.你可以远程废除之前发出的钥匙

#### 用户，客户端，服务端（保护资源和授权服务器）之前的关系？

我的理解是：用户就是Users，客户端可以理解为APP,服务端就不用说了

#### grant类型分类？

说明Oauth支持的grant_type(授权方式)与功能

authorization_code -- 授权码模式(即先登录获取code,再获取token)

password -- 密码模式(将用户名,密码传过去,直接获取token)

refresh_token -- 刷新access_token

implicit -- 简化模式(在redirect_uri 的Hash传递token; Auth客户端运行在浏览器中,如JS,Flash)

client_credentials -- 客户端模式(无用户,用户向客户端注册,然后客户端以自己的名义向'服务端'获取资源)

#### 图解Oauth2流程？

详见：other目录下的图片


## 快速开始
1. 安装Maven
2. Maven编译
3. 快速部署
4. 测试

## 使用
1. 测试password授权方式。
2. 地址:http://localhost:8080/oauth2ApiDemo/oauth/token?grant_type=password&client_id=restapp&client_secret=restapp&username=zzxb&password=qaz123
3. 结果:<br/>
{<br/>
"access_token":"ec25d26c-24f9-4caa-ac07-34dae7403706",<br/>
"token_type":"bearer",<br/>
"refresh_token":"51797e4a-a69a-4e79-a770-e020af098657",<br/>
"expires_in":119</br/
}<br/>
4. 获得access_token后,就可以访问:http://localhost:8080/oauth2ApiDemo/api/users/?access_token=ec25d26c-24f9-4caa-ac07-34dae7403706
5. 结果:[{"id":1,"name":"user_a","email":"user_a@example.com","phone":"9898989898"},{"id":2,"name":"user_b","email":"user_b@example.com","phone":"9767989898"},{"id":3,"name":"user_c","email":"user_c@example.com","phone":"9898459898"}]
6. 超过访问时,访问结果为:
               <oauth>
               <error_description>
               Access token expired: ec25d26c-24f9-4caa-ac07-34dae7403706
               </error_description>
               <error>invalid_token</error>
               </oauth>
7. 测试client_credentials授权方式。
8. 测试:http://localhost:8080/oauth2ApiDemo/oauth/token?grant_type=client_credentials&client_id=restapp&client_secret=restapp
9. 结果:<br/>
{<br/>
"access_token":"c0455d2b-8965-46f7-a378-cbbc1320bf37",<br/>
"token_type":"bearer",<br/>
"expires_in":119<br/>
}<br/>
10. 重复第4步。

## 开发者

- 郑波


## 版本

V 0.1

## 修改日志
- 2016-8-28:
- [x] 创建oauth演示项目,并对一些配置文件进行了注解。

## 参考资源
以下是在编写案例中收集的关于OAuth的资源,对深入理解与运用OAuth有帮助

- [OAuth2.0协议(英文)](https://tools.ietf.org/html/rfc6749)
- [OAuth2.0官方网站](https://oauth.net/2/)
- [OAuth 2 开发人员指南（Spring security oauth2）](http://www.oschina.net/translate/oauth-2-developers-guide)
- [理解OAuth 2.0](http://www.ruanyifeng.com/blog/2014/05/oauth_2_0.html)
- [Spring官方Oauth2案例](https://github.com/spring-projects/spring-security-oauth)

------
建议使用IntelliJ Idea开发工具。

