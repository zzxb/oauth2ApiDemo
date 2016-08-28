这是一个基于oauth2设计的Spring restful安全的api案例，只为提供为ios/android等客户端提供安全的api设计参考,参考了微信api设计方式,主要提供client_credentials,password授权方式
- SpringMVC
- Spring Security
- Spring Security oauth

## 快速开始
1. 安装Maven
2. Maven编译
3. 快速部署
4. 测试

## 使用
1. 测试password授权方式。
2. 地址:http://localhost:8080/oauth/token?grant_type=password&client_id=restapp&client_secret=restapp&username=zzxb&password=qaz123
3. 结果:{"access_token":"ec25d26c-24f9-4caa-ac07-34dae7403706","token_type":"bearer","refresh_token":"51797e4a-a69a-4e79-a770-e020af098657","expires_in":119}
4. 获得access_token后,就可以访问:http://localhost:8080/api/users/?access_token=ec25d26c-24f9-4caa-ac07-34dae7403706
5. 结果:[{"id":1,"name":"user_a","email":"user_a@example.com","phone":"9898989898"},{"id":2,"name":"user_b","email":"user_b@example.com","phone":"9767989898"},{"id":3,"name":"user_c","email":"user_c@example.com","phone":"9898459898"}]
6. 超过访问时,访问结果为:
               <oauth>
               <error_description>
               Access token expired: ec25d26c-24f9-4caa-ac07-34dae7403706
               </error_description>
               <error>invalid_token</error>
               </oauth>
7. 测试client_credentials授权方式。
8. 测试:http://localhost:8080/oauth/token?grant_type=client_credentials&client_id=restapp&client_secret=restapp
9. 结果:{"access_token":"c0455d2b-8965-46f7-a378-cbbc1320bf37","token_type":"bearer","expires_in":119}
10. 重复第4步。

## 开发者

- 郑波


## 版本

V0.1

## 修改日志
- 2016-8-2:
- [x] 创建oauth演示项目,并对一些配置文件进行了注解。


------
建议使用IntelliJ Idea开发工具。
