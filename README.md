## 该项目是一个图书管理系统 采用redis+mysql  定时器+协程
### 角色：游客、管理员、用户  生成swagger文档并通过apifox测试接口  
### 功能：
###   1.注册登录：用户登录采用jwt；管理员登录采用session；手机验证码登录：通过实现阿里云三方接口，自己生成四位随机数验证码；微信登录(原理掌握，还未实现)。
###   2.管理员、用户模块：依据restful风格开发代码，实现管理员接口的增删改查。
###   3.限流：防止用户或管理员连续多次点击接口，使用tools.LimitedFlow(2, 2*time.Second)中间件，可以自行设计m秒内点击n次；
###   4.缓存预热、压缩数据：防止雪崩，为redis中key失效时间设置为随机数；出现热点书籍，出现击穿现象(考虑单飞)
###   5.分页：采用了两种分页方式，第一种传统方式：普通分页，mysql使用limit和offset实现；第二种：基于游标分页，根据书名、数量、封面创建索引，通过id和limit实现。
