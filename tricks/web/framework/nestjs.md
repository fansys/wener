# NestJS

## Tips
* 设计来自 Angular + SpringFramework
* 核心概念
  * Module
  * Controller
  * Provider
  * Middleware
  * Exception filter
  * Pipe
  * Guard
  * Interceptor
  * decorator
* 特性
  * 底层平台无关 - 默认 Express，可用 Fastify
  * 支持 GraphQL、WebSocket
  * combine your config and your code seamlessly by making use of TypeScript decorators
* 集成
  * NextJS
    * [nestjs/nest#1122](https://github.com/nestjs/nest/issues/1122)
    * [kyle-mccarthy/nest-next](https://github.com/kyle-mccarthy/nest-next)
    * 因为 Next 可能在构建时有一些请求，两者共存可能会有些问题
    * 可能前后端分离更好
  * 数据库
    * `@nestjs/typeorm`
    * `@nestjs/sequelize`
  * 配置
    * `@nestjs/config` - dotenv
  * 校验
    * [class-validator](https://www.npmjs.com/package/class-validator)
  * 缓存
    * [cache-manager](https://www.npmjs.com/package/cache-manager) - Flexible NodeJS cache module
  * 序列化
    * [class-transformer](https://www.npmjs.com/package/class-transformer)
  * 任务调度
    * `@nestjs/schedule` - [node-cron](https://www.npmjs.com/package/node-cron)
  * 安全
    * [helmet](https://www.npmjs.com/package/helmet)
    * CSRF [csurf](https://www.npmjs.com/package/csurf)
    * 限流 [express-rate-limit](https://www.npmjs.com/package/express-rate-limit)
  * 队列
    * `@nestjs/bull` - bull
  * 日志
    * [winstonjs/winston](https://github.com/winstonjs/winston)
  * 文件上传
    * [expressjs/multer](https://github.com/expressjs/multer)
  * HTTP 客户端
    * axios
  * GraphQL
    * `@nestjs/graphql` apollo-server-express
