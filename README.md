# **_欢迎来到 ccfox 算力云项目，[线上 Demo](https://mhashcloud.ccfox.com)_**

只需一周，拥有专属于您的算力交易功能

您只需要对接少量接口，即可快速接入，仅需 1 周！

=========== 欢迎联系我们：==================

**_微信：13066998399 （加好友请注明 b 端合作）_**

**_邮箱：sonic@ccfox.com_**

**_官网：[www.ccfox.com](https://www.ccfox.com)_**

============== thank =====================

## 算力云 B 端对接说明

如果您符合以下其中一种或多种条件，您可以 B 端对接端方式接入算力云，快速部署属于您的衍生品算力交易系统。

- 数字资产钱包
- 币币交易所
- 集成了 USDT/ETH/BTC 钱包的项目

通过接入算力云，您将获得：

- 高比例后端手续费分成，您的流量变现最佳手段
- 极致算力交易体验，
- 优化风控极致，客活率 up up up!
- 前期培训+持续运营支持，保障您的成功！

## 对接流程

算力云 B 端对接十分简单，仅需您完成以下几步即可。

1. 在 **您的系统** 中每个用户准备单独的算力交易账户，并 准备一个资金划转功能
   - 用户的资金可以在 普通账户 和 算力交易账户 之间互相划转。
2. 在**您的系统**准备一个为用户开通算力交易的确认功能，并：
   - 让用户勾同意选我们准备好的 算力用户协议
   - 用户提交开通确认后，通过 [子账户注册](https://github.com/ccfoxcloud/hash-cloud-api/blob/master/doc/api.md#%e5%ad%90%e8%b4%a6%e5%8f%b7%e6%b3%a8%e5%86%8c)接口为该用户在 **我们的系统** 注册账户，该账户是 **您 B 端母账户** 下的子账户。
3. 在 **您的系统** 中准备资金划转功能
   - 用户的资金可以在 普通账户 和 算力交易账户 之间互相划转
   - 当用户在 **您的系统** 中，由普通账户向 **算力交易账户** 转入资金时，您通过调用我们系统的[转账接口](https://github.com/ccfoxcloud/hash-cloud-api/blob/master/doc/api.md#%e8%bd%ac%e8%b4%a6)，将 B 端母账户的资金转入到 **用户的子账户**中。
   - 区块链转账时间比较长，为了提升用户体验，我们建议您在母账户中预存部分资金。
   - 您需要定期平衡 **您的网站中的资金** 和 **您在我们这边的 B 端母账户资金** ， 您可能会需要用到 [资产查询接口](https://github.com/ccfoxcloud/hash-cloud-api/blob/master/doc/api.md#%e8%b5%84%e4%ba%a7%e6%9f%a5%e8%af%a2) 查询 您的 B 端母账户或者您旗下的子账户的资产情况
4. 将我们准备好的 **算力交易页面前端**嵌入到您的网站中
   - 用户进入**交易页面前端**时，调用 [登陆接口](https://github.com/ccfoxcloud/hash-cloud-api/blob/master/doc/api.md#%e5%ad%90%e8%b4%a6%e5%8f%b7%e7%99%bb%e5%bd%95)为用户在 我们的系统 登陆

## 对接示意图

![对接示意图](https://www.processon.com/view/link/5e41133de4b0cffec6deafb3)

## 如何对接

- [前端(H5 版)对接](https://github.com/ccfoxcloud/hash-cloud-h5)(GitHub 私仓，需要先申请 GitHub 权限)
- [前端(PC 版)对接](https://github.com/ccfoxcloud/hash-cloud-pc)(GitHub 私仓，需要先申请 GitHub 权限)
- [服务端对接](./doc/api.md)
- [通知模板](通知模板.csv)

**_NOTE:_**

[前端(H5 版)对接](https://github.com/ccfoxcloud/hash-cloud-h5)和[前端(PC 版)对接](https://github.com/ccfoxcloud/hash-cloud-pc)这里是 GitHub 的私仓，如果没有 GitHub 账号的话需要先注册，再找 ccfox 技术对接人员提交表单（主要是提交 GitHub 账号）申请权限，ccfox 相关人员处理完之后才能访问并拉取相关代码。

## 算力列表配置事宜

1. 确认一下需要的算力列表,反馈给 ccfox
2. 向 ccfox 索要需要在代码里配置的 B 端合作商标识
3. 在前端项目里将合作商标识配置到.env.cloud 里的 REACT_APP_BROKERUUID
4. 后续算力列表有变更，联系 ccfox

## QA

1.  Q: 转账接口的 api 是否有白名单可以限制?
    A: 生产都要加白名单的，调试期见放开，上线的时候加白名单

2.  Q: 前端都使用的是算力云页面，例如 web 首次调用 xxx 接口获取好用户的 accesstoken 给到前端，保存下来，后续过期问题，包括保证 app 的 token 也不过期，对 xxx 来说这里如何对接
    A: 一旦过期，需要跳到 XXX 登录页面重新登录，然后再回到交易页面

3.  Q: mhashcloud.ccfox.com 能否单独运行在浏览器中
    A: 这个项目必须配合 app 使用，单独浏览器事件没有落地的地方，所以没有反馈；点击功能按钮后 js 会发事件出去 app 接住做处理 再交互下一步

4.  母账户能否交易
    出于方便对账的考虑，算力云的母账户 是不能用于交易的，我们会禁止交易权限。

5.  Q：对接方的邀请返佣体系如何处理。
    A：整个的邀请返佣模块，都可以由对接方按照自己需求自行开发，我们提供每个用户的数据接口。

## 更新记录

[变更记录](changeRecords.md)
