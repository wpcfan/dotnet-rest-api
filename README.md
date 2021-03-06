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

创建表的脚本可以放在 DbScripts 目录下，我们通过将这个目录映射到 Docker 的 `docker-entrypoint-initdb.d` 来完成数据库启动之后的脚本自动执行。

```
volumes:
    - ./DbScripts:/docker-entrypoint-initdb.d
```

在开发时可以不使用 MySql Docker，连接本地数据库，可以参看 `appsettings.Development.json` 文件中的 `DbContextSettings`

```json
"DbContextSettings" :{
    "ConnectionString" : "server=localhost;userid=root;password=Wp770521;database=eftest;"
  }
```

macOS 运行时，使用下面的命令启动即可以开发模式的配置进行服务的启动

```
ASPNETCORE_ENVIRONMENT=Development dotnet run
```

改变监听端口也可以使用设置环境变量的方式进行，比如下面就是在开发中指定 8080 为监听端口

```
ASPNETCORE_URLS=http://0.0.0.0:8080 ASPNETCORE_ENVIRONMENT=Development dotnet run
```
