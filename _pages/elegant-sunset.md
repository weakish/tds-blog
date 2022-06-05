---
title: 优雅下线开发者服务
category: guide
---

对于开发者服务来说，每个 API 、每个参数都有大量的细节，和面向终端用户的产品很不一样。图形界面改了，用户自己会去适应，但调用 API 的程序不会自己适应，还是要开发者来改。

对于类似 LeanCloud 这种提供了十多种不同语言 SDK 、上百个 API 接口、加一起可能有几千个参数的服务来说，其实「下线功能」这种事情是经常会发生的。

对于客户端来说，能做的就是尽量遵守 Semantic Versioning （语义化版本号），把不兼容改动都放在 major （大版本）的更新里，甚至提前几个版本就开始打印警告，对于不兼容的改动提供详细的迁移文档（应该换成哪些 API 来替代）；要及时在文档和 Demo 中将即将废弃的接口去掉，如果整个 Demo 都不再支持的话也要在 GitHub 上修改 README 后 archive 掉。

对于服务端来说接口一旦下线就彻底无法使用，通常要更加慎重，比如需要在客户端去掉该接口比较长时间以后、从监控看到接口的使用量很小的情况下再下线；提前将功能的入口（如文档）去掉，避免新的开发者使用。

确实有时候迫于业务方向或者法规要求，还是会有一些比较生硬的「下线」，但无论如何还是要将这个事情提前通知到开发者。如果只是一个小功能最好能精确通知到受影响的用户，通知的时候态度还是要坚决，要约定明确的下线时间，否则开发者不会当回事；如果是整个产品的下线则应该有公开的公告，最好是能由 CEO 或者高层负责人在其中介绍一下前因后果。

对于涉及数据的应用要提供导出数据的方式和文档；涉及到费用的要为开发者退款，最好是在「从通知到下线」这个过渡期不再收取费用。

说到服务下线有个有趣的做法是「提前下线一小段时间来起到通知的作用」然后再恢复给开发留出迁移的时间，[GitHub 就曾经这么做过](https://developer.github.com/changes/2018-11-05-github-services-brownout)