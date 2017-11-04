# dotnet-rest-api
DotNet Core 应用和 Spring Boot 很像，都是基于构造函数进行依赖注入，同样使用 Controller 做 Rest API 的 endpoint。

这个范例应用采用 Microsoft.EntityFrameworkCore 作为 ORM，使用 Pomelo.EntityFrameworkCore.MySql 作为 MySQL 的 EF 扩展。

工程支持 Docker

可以在工程目录下采用如下命令手动生成 Docker 文件

```
docker build -t aspnetapp .
```

但更推荐使用 docker-compose

启动数据库和 .net API 服务

```
docker-compose up
```

关闭数据库和 .net API 服务

```
docker-compose down
```
