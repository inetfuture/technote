# 前言

本文是对我自己及团队成员的一些要求，欢迎补充和改进。

# 必读资料书籍

- 《代码整洁之道》
- 《深入理解计算机系统》
- 《TCP/IP 详解 卷1》
- [how-to-name-things](http://slides.com/inetfuture/how-to-name-things)
- [Git相关](git.md)
- [RESTful api](restful_api.md)
- [the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line/blob/master/README-zh.md)

# 必备工具

- VPN：http://gjsq.me/6292696

    使用方法：

    - Linux PPTP：https://www.igreenjsq.mobi/shiyong/67.html
    - OS X：https://www.igreenjsq.mobi/mac.html

    VPN 是全局生效的，为了可以继续访问本地局域网（比如 192.168 网段）需要修改路由表：

    - Linux：`sudo route add -net 192.168.0.0 netmask 255.255.0.0 gw ${GATEWAY}`
    - OS X：`sudo route -n add 192.168.0.0/16 ${GATEWAY}`

    另外也可以将一些国内常用网站 IP 加进去绕过 VPN 提高访问速度，你可以把这些命令保存到一个 shell 脚本里，开机的时候自动或手动执行一下。

- Sublime Text：http://www.sublimetext.com/3

    安装 Package Control：https://packagecontrol.io/installation ，必备插件：Git，GitGutter，knockdown，SublimeLinter，DocBlockr，EditorConfig，Emmet，FileDiffs，SublimeCodeIntel

    可以将整个配置目录放到 GitHub 上，方便在多台机器上同步（也可以用 Dropbox 同步，参考下面），比如 https://github.com/inetfuture/sublime-config ，配置目录的位置：

    - Linux：~/.config/sublime-text-3/Packages/User
    - OS X：~/Library/Application\ Support/Sublime\ Text\ 3/Packages/User

- Oh My Zsh：https://github.com/robbyrussell/oh-my-zsh
- Dropbox：https://db.tt/N5tpOzTY

    全客户端支持，包括 Linux ，需要翻墙。国内类似的服务且支持 Linux 的，我试过金山快盘，可惜同步不稳定，经常出错。

    除了同步各种资料外，还可以用来同步一些配置文件，比如各种 dot files：~/.bashrc，~/.pep8，~/.gitconfig 等等，把它们放到 Dropbox 的同步目录下，然后建立软链接到本来的位置，这样公司、家里多台机器可以无缝同步，尤其重装系统或者换新机器的时候，各种用习惯了的配置可以快速重新启用。

- 印象笔记：https://www.yinxiang.com/

    不建议使用 Evernote 国际版，太卡，而且国内的版本提供的本地化服务更方便。

    - 剪藏浏览器插件：https://appcenter.yinxiang.com/app/evernote-webclipper/web-apps/
    - 关注微信公众号：“我的印象笔记”，可以快速收藏微信内容

# 开发环境配置

## 安装软件

- 优先使用语言版本管理器安装语言运行时，比如 nvm（Node.js），pyenv（Python），rvm（Ruby），jenv（Java），phpbrew（PHP）

    **注意，此类工具通常安装在你的 `$HOME` 下，通过修改当前 shell 的 `$PATH` 等环境变量生效，就是说安装或者使用它们的时候，你不需要也不应该使用 `sudo` 。**

    好处：

    - 不需要 `sudo`，不会污染系统环境，如果中间出错了，可以直接删掉重来。
    - 方便版本切换，包括最新版本。

- 优先使用语言包管理器安装语言依赖，比如 npm（Node.js），pip（Python），gem（Ruby），maven/gradle（Java），pecl/composer（PHP）
- 优先使用系统包管理器安装系统依赖，apt-get（Ubuntu），homebrew（OS X）
    - 优先使用第三方工具的官方源或者可靠的 PPA 源，比如在 Ubuntu 上安装 MongoDB 和 Redis 时：http://docs.mongodb.org/manual/tutorial/install-mongodb-on-ubuntu/#install-mongodb ，https://launchpad.net/~rwky/+archive/ubuntu/redis
- Ubuntu 必备软件包：`sudo apt-get install -y aptitude gdebi vim curl wget build-essential openssh-server`

# 做事原则

- 认真负责
    - 每一份需求都要理解之后再动手，需求不合理的提出来讨论，对产品要有责任心，不仅仅是 “按部就班” 得做事情。
    - 提交前仔细测试自己实现的功能，检查代码细节，有交付高质量代码的责任心，而不是依赖其他成员帮你 Reivew 或者 QA 帮你发现 bug 。
- 主动沟通而不是被动应付
    - 自己的代码被别人 Review 时，如果觉得某段代码可能有问题或者不是最优方案，主动提出来讨论，而不是等待审查者询问。前者可以使 Review 更高效，更利于培养同事间的相互信任，后者一是效率低，同时也是一种不负责任的表现。
    - 进度存在风险时主动知会其他人，而不是默默拖到最后一刻连累大家加班。
- 自我驱动
    - 自觉深入学习相关技术，而不是用多少学多少。
    - 主动思考产品的走向，自觉进行知识储备、调研。
    - 自觉重构低质量代码，保证项目的健康发展。
- 换位思考
    - 使用邮件、微信等工具交流时一次性提供必要的上下文，避免低效率的沟通，想一下，我这样描述对方是否可以理解并直接回复。
    - 无论是做 Code Review 还是提交功能给 QA 测试，尽自己最大努力保证质量。
- 从根本上解决问题
    - 思考问题的原因，不要停留于表面问题的修修补补。

        比如，QA 报了一个 Bug，说在一个输入项中填入 `<script>alert('haha');</script>` ，保存后页面上会弹出提示框，你来修复这个问题的时候要考虑从根本上杜绝脚本注入问题，比如使用 Angular.js 的 `$sanitize` service 过滤输入再显示。相比较而言，不太恰当的做法是仅仅用正则过滤掉输入中的 `<script />` 标签，虽然可以修复这个 Bug，却是治标不治本，如果输入中包含 `onmouseover="alert('haha')"` 这种代码呢？

        当然这种问题需要你有扎实的基本功，对开发各个方面有较全面的了解，才能一针见血的解决问题。

    - 每一个问题，想一下有没有办法一劳永逸？或者自动化？

- 用正确的方式解决问题
    - 很多问题都有不止一种的解决办法，不要满足于你最初想到的那种，也许有更好的呢？主动去思考目前的方案可维护吗？效率高吗？普适吗？
    - 多看一些最佳实践（Best Practice）的资料，多看一些优秀开源项目的源代码，多了解别人怎么做的你才能及时发现自己的不足。

        比如 RESTful API，是有一套业界公认的最佳实践的，其本身就是一套约定俗成的东西，如果你没有看过这些最佳实践，随意的设计 URL，随意的使用 HTTP 动词，那你设计出来的 API 其实只是 HTTP API，请不要称其为 RESTful API。

        再比如你对 Git 不熟，然后不知怎么得把工作目录搞的一团糟，你该怎么办？再 clone 一个重新开始？NO！除非你打算一辈子这么干。你应该去 google 解决方案，并充分认识到自己对 Git 不熟这个事实，然后拿出时间来补充知识。

# 编写整洁代码

## 基本要求

- Coding Style，如果有要求，应该严格遵循，例外的情况需要讨论决定。
- 可读性，是否容易理解，命名是否具有足够描述性，是否有歧义，代码路径、结构是否清晰、简洁。
- 一致性，包括但不限于标识符命名、错误处理、日志格式、文件组织方式、HTTP API 接口设计、UI 交互等各个方面，越是一致的系统越容易上手，越容易维护，反之则维护成本越高。
- 健壮性，是否进行必要的输入验证，边界情况是否考虑到，异常处理是否周全，会不会产生内存泄露，等等。
- 性能，数据量大或者访问频繁时是不是会有问题，对内存、数据库的使用是否高效，算法是否最优。
- 安全性，是否进行必要的权限检查，是否过度信任客户端输入。
- 重复代码，复制、粘贴的行为是要坚决禁止的，不知道如何复用代码的要主动与其他成员讨论。
- 单一职责原则，一个类、文件或者模块是否做的太多，是否干了它不该干的事。
- 开放、封闭原则，是否方便扩展，是否考虑到了以后的需求。
- 代码改动方式是否合适，是不是在一味得堆砌代码，是否需要停下来进行重构。
- 保持干净，不能存在任何无用的文件、代码，文档、注释需要同步更新，不能包含注释掉的代码，不能包含临时调试代码，如果确有原因应该添加注释说明。

## 进阶要求

- 使用多态减少或转移 `if` 判断，https://www.youtube.com/watch?v=4F72VULWFvc&index=1&list=PL693EFD059797C21E

## 提高可读性的小技巧

- return early, https://www.airpair.com/php/posts/best-practices-for-modern-php-development#4-2-try-not-to-use-else-

# Code Review

## 目的

- 提高代码质量，查漏补缺。
- 相互学习。
- 促进项目内知识流动，防止对某个个人过分依赖。

## Commit Message 规范

```
$(scope): $(subject)

$(description)
```

- `$(scope)`：取决于具体项目，一般为一组固定值，用来描述本次 commit 影响的范围，比如 https://github.com/nodejs/node/commits/master ，后加入项目的新成员应遵循已有的 scope 约定。
- `$(subject)`：50 字左右的简要说明，禁止出现 *update code* ， *fix bug* 等无实际意义的描述，好的例子： *select connector by sorting free memory* （不需要形如 *update about how to select connector ...* 的啰嗦写法）, *fix sucess tip can not show on IE8* （不需要形如 *fix bug of ...* 的啰嗦写法）。
- `$(description)`：详细说明，建议使用列表罗列。

## 流程

1. 提交者发起 topic 分支到目标分支的 Merge Request
    - 代码变动要尽量小且专注于一个任务，不要攒的很大，或者做多个任务，要保证审查者可以较快、较容易的 Review 。
    - 交给别人 Review 之前一定要自己先按此清单过一遍，别人只是帮你查漏补缺，对自己的代码负责，不要浪费别人的时间
    - 发起后，要在 GitLab 或者其它 Review 工具上 double check 变更集。
2. 审查者 Review 代码
    - 对 [编写整洁的代码](#编写整洁代码) 中各项要求进行检查
    - 在任何有疑问或建议的地方留 comment
    - 从中学习一些好的东西
    - 完成后，如果有问题需要修复，留 comment “Reviewed and waiting for fix”，否则进行第 4 步。
3. 提交者响应 comments
    - 确实有问题的，修复之。如果该分支未被其他人使用，应使用 `git commit --amend` 提交以减少不必要的 commit。
    - 不同意的，讨论。
    - 完成后，留 comment “Fixed”，审查者再次检查，回到第二步。
4. 审查者确认没有问题之后，将 Merge Request 转发给目标分支的维护者进行合并。
