# * 最新功能请参考[dev](https://github.com/VictorTzeng/Zxw.Framework.NetCore/tree/dev)分支


# * Demo地址：[Zxw.Framework.NetCore.Demo](https://github.com/VictorTzeng/Zxw.Framework.NetCore.Demo)


# Zxw.Framework.NetCore
基于EF Core的Code First模式的DotNetCore快速开发框架

**开发环境**
* VS2017 / VS Code
* .net core 2.1

**支持的数据库**
* SQL Server
* MySQL
* Sqlite
* InMemory
* PostgreSQL

**日志组件**
* log4net

**DI组件**
* Autofac

**缓存组件使用**

本项目采用的AOP中间件 ：[AspectCore-Framework](https://github.com/dotnetcore/AspectCore-Framework)
* MemoryCacheAttribute ：基于MemoryCache的缓存拦截组件
* RedisCacheAttribute ：基于Redis的缓存拦截组件

如何使用：

    public interface ITutorClassTypeRepository:IRepository<TutorClassType, Int32>
    {
        [MemoryCache]//使用MemoryCache，缓存有效时间默认10分钟
        IList<TutorClassType> GetByMemoryCached(Expression<Func<TutorClassType, bool>> where = null);

        [RedisCache(Expiration = 5)]//使用Redis，缓存有效时间为5分钟
        IList<TutorClassType> GetByRedisCached(Expression<Func<TutorClassType, bool>> where = null);
    }


**.net framework版本地址**
* [Zxw.Framework.Nfx](https://github.com/VictorTzeng/Zxw.Framework.Nfx)



**项目说明**
* 请参考我的博客：[http://www.cnblogs.com/zengxw/p/7673952.html](http://www.cnblogs.com/zengxw/p/7673952.html)

**2018/07/06 合并dev分支到master**
* 1.添加EFCore直接返回[DataTable](https://github.com/VictorTzeng/Zxw.Framework.NetCore/blob/d99b321006ad7ee12883e92742d3ef1fe44968f7/Zxw.Framework.NetCore/Extensions/EntityFrameworkCoreExtensions.cs#L20)功能
* 2.DBFirst功能，目前仅支持SQL Server、MySQL、NpgSQL三种数据库。根据已存在的数据表直接生成实体代码，详见[CodeGenerator](https://github.com/VictorTzeng/Zxw.Framework.NetCore/blob/d99b321006ad7ee12883e92742d3ef1fe44968f7/Zxw.Framework.NetCore/CodeGenerator/CodeGenerator.cs#L205)
* 3.添加单元测试项目，并完成对以上两点新功能的测试
* 4.引入IOC容器[Aspectcore.Injector](https://github.com/dotnetcore/AspectCore-Framework/blob/master/docs/injector.md)，详见[AspectCoreContainer.cs](https://github.com/VictorTzeng/Zxw.Framework.NetCore/blob/master/Zxw.Framework.NetCore/IoC/AspectCoreContainer.cs)
