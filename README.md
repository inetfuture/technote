# 前言

本文是对我自己及团队成员工作上的一些要求或指导，欢迎补充和改进。

# 必读资料书籍

- 《代码整洁之道》
- 《深入理解计算机系统》
- 《TCP/IP 详解 卷1》
- [how-to-name-things](http://slides.com/inetfuture/how-to-name-things)
- [RESTful API](restful_api.md)
- [Git](git.md)
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

- Chrome 插件：
    - https://chrome.google.com/webstore/detail/evernote-web-clipper/pioclpoplcdbaefihamjohnefbikjilc?hl=en
    - https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop?hl=en

# 开发环境配置

## 安装软件

- 优先使用语言版本管理器安装语言运行时，比如 nvm（Node.js），pyenv（Python），rvm（Ruby），jenv（Java），phpbrew（PHP）

    **注意，此类工具通常安装在你的 `$HOME` 下，通过修改当前 shell 的 `$PATH` 等环境变量生效，就是说安装或者使用它们的时候，你不需要也不应该使用 `sudo` 。**

    好处：

    - 不需要 `sudo`，不会污染系统环境，如果某天坏掉了，可以直接删掉重来。
    - 方便版本切换，及时用上最新版本。

- 优先使用语言包管理器安装语言依赖，比如 npm（Node.js），pip（Python），gem（Ruby），maven/gradle（Java），pecl/composer（PHP）
- 优先使用系统包管理器安装系统依赖，apt-get（Ubuntu），homebrew（OS X）
    - 对于一些第三方工具，优先使用其官方源或者可靠的 PPA 源，比如在 Ubuntu 上安装 MongoDB 和 Redis 时分别使用：http://docs.mongodb.org/manual/tutorial/install-mongodb-on-ubuntu/#install-mongodb ，https://launchpad.net/~rwky/+archive/ubuntu/redis
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
    - 无论是做 Code Review 还是提交功能给 QA 测试，尽自己最大努力保证质量，做好自己分内的事，减轻队友的负担。
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

    - 不要重复造轮子，尤其是使用第三方库时，也许人家已经提供了现成的解决方案，只是因为你没有仔细看文档，所以不知道。
- 磨刀不误砍柴工
    - 学习新知识要尽可能的系统、全面，不要只是为了应付当前工作片面了解。
    - 使用第三方库、框架时应尽量通读其文档，至少要知道它可以做什么，有哪些限制，遇到具体问题后可以迅速到文档中查看细节。
    - 常用的东西要舍得花时间搞清楚其运行原理、内部机制，免的每次出问题都像无头苍蝇，只能瞎猜。比如 Angular.js 的 directive 编译流程是怎样的？
- 关注细节
    - 细节不一定决定成败但却可以充分体现一个人的工作态度，你愿意被队友认为是个不靠谱的人吗？
    - 认真对待各种流程、规范，比如写英文邮件时，从语法、格式到每一个拼写、标点，再比如 Commit Message 的格式。

# 编写整洁代码

## 基本要求

- Coding Style，如果有要求，应该严格遵循，任何例外的情况需要讨论决定。
- 可读性，要容易理解，命名要具有足够描述性，不能有歧义，代码路径、结构要清晰、简洁。
- 一致性，包括但不限于标识符命名、错误处理、日志格式、文件组织方式、HTTP API 接口设计、UI 交互等各个方面，越是一致的系统越容易上手，越容易维护，反之则维护成本越高。
- 健壮性，进行必要的输入验证，充分得考虑边界情况，异常处理要周全，防止内存泄露，防止竞态条件，多线程安全，等等。
- 性能，考虑数据量大或者访问频繁时的情况，对内存、数据库的使用要高效，算法要尽量最优。
    - 数据库
        - 操作应尽量批量进行，减少 IO 消耗。
        - 特别大的查询应在数据库中分页，全量取出在内存中分页或者根本不考虑数据量大小是常见的低级错误。
        - 合理使用索引。
- 安全性，进行必要的权限检查，不能过度信任客户端输入。
- DRY（Don't Repeat Yourself）原则，复制、粘贴的行为是要坚决禁止的，不知道如何复用代码的要主动与其他成员讨论。
- 单一职责原则，一个类、文件或者模块不能做的太多，不能做不该它做的事，好的设计是只把一件事做好。
- 开放、封闭原则，要方便扩展，要考虑到以后的需求。
- 代码改动方式要合适，不能一味得堆砌代码，需要适时停下来进行重构。
- 保持干净，不能存在任何无用的文件、代码，所有文档、注释需要同步更新，不能包含注释掉的代码，不能包含临时调试代码，例外情况应该添加注释说明。
- 所有 Warning 都应该被立即修复，觉得不需要修的，讨论决定后通过修改配置文件禁用掉。

## 进阶要求

- 使用多态减少或转移 `if` 判断，https://www.youtube.com/watch?v=4F72VULWFvc&index=1&list=PL693EFD059797C21E

## 提高可读性的技巧

- 局部变量尽量就近声明。
- return early, https://www.airpair.com/php/posts/best-practices-for-modern-php-development#4-2-try-not-to-use-else-
- 在语言本身语法允许的情况下，将主流程放在文件上部，子流程按被调用顺序放在文件下部，这样打开文件后可以比较快的抓住重点，比如：

    ```coffee
    main = ->
      doStuff1()
      doStuff2()
      doStuff3()

    doStuff1 = ->
      console.log '1'

    doStuff2 = ->
      console.log '2'

    doStuff3 = ->
      console.log '3'
    ```

- 相关的代码尽量按使用顺序组织在一起，尤其是添加新代码时，不要一味得添加到文件尾部。
- 布尔变量命名应尽量采用肯定形势。
- 避免硬编码数字、字符串。
- 传递简单数据类型时，适当添加临时变量提高可读性，例如：

    ```coffee
    ignoreError = true
    doStuff(ignoreError)
    ```

## 如何写注释

- 代码的意图应该由代码自身来表达，即所谓的可读性，不应该依赖于注释说明，所以优先考虑写更可读的代码。
- 代码意图明显的情况下，不要加注释重复说明。
- 以下情况需要写注释：
    - 纲要性的注释，简要的描述某一个文件、某一个类或某一个流程。
    - 确实无法从代码本身提高可读性的情况，比如复杂业务逻辑、算法。
    - 代码的作用并不直观时，解释这样做的原因。
    - 存在多种可选方案时，解释为什么选择现在这种。
    - 因为某些限制而使代码不一致或不优雅时，应注明原因。
    - 参考了外部一些资料时，应注明链接，方便其他人查看。
- 注释应随代码更新。

# 调试技巧

- 查看日志，比如做 PHP Web 开发要知道 Nginx，PHP-FPM，PHP 的日志文件的位置，必要的时候从中寻找线索。使用 `tail -F file1 file2` 命令可以持续监控多个文件。
- 通过添加临时 log 语句或断点的形式检查代码路径，很多时候调试是个体力活，并没有什么难度。检查代码是否按预期路径执行了，如果没有，为什么？输入数据的原因吗？或者中间一步数据处理是错的？从数据进入系统开始一步步从前往后分析，用排除法逐步缩小范围，bug 必将无所遁形。另外，有时候代码路径可能牵扯到第三方库，这个时候不要畏惧，代码都是人写的，尤其开源项目通常质量较高，进去看一下，通常没你想象的那么难。
- 确保读懂日志消息、异常信息、错误输出等，特别是英文内容，不要因为是英文不想读，结果非常明显的线索摆在你面前你却视而不见。比如常见的 git 错误，都会有相应的描述甚至建议的解决办法。再比如做 Web 开发，一个页面打不开，最起码你要先看一下 HTTP Response 是什么，状态码，body 等。如果实在看不懂，goole 之。
- 有意识的组织整理常见错误，依据过往经验快速定位问题。例如 PHP 开发时碰到 HTTP 404，基本可以排除代码逻辑问题，应该检查拼写错误、Nginx 配置、MVC 框架路由配置、文件路径等。

# Code Review

## 目的

- 提高代码质量，查漏补缺。
- 相互学习。
- 促进项目内知识流动，防止对某个个人过分依赖。

## Commit Message 规范

规定格式如下：

```
$(scope): $(subject)

$(description)
```

- `$(scope)`：必需，取决于具体项目，一般为一组固定值，用来描述本次 commit 影响的范围，比如 https://github.com/nodejs/node/commits/master ，后加入项目的新成员应遵循已有的 scope 约定。
- `$(subject)`：必需，50 个字符左右的简要说明，首字母小写，通常是动宾结构，描述做了什么事情，动词用一般现在时，禁止出现 *update code* ， *fix bug* 等无实际意义的描述，好的例子： *select connector by sorting free memory* （不需要形如 *update about how to select connector ...* 的啰嗦写法）, *fix sucess tip can not show on IE8* （不需要形如 *fix bug of ...* 的啰嗦写法）。
- `$(description)`：可选，详细说明，建议使用列表罗列要点。

## 流程

1. 提交者发起 topic 分支到目标分支的 Merge Request 。
    - 代码变动要尽量小且专注于一个任务，不要攒的很大，或者做多个任务，要保证审查者可以较快、较容易的 Review 。
    - 交给别人之前一定要自己先 Review 一遍，别人只是帮你查漏补缺，对自己的代码负责，不要浪费别人的时间。
    - 发起后，要在 GitLab 或者其它 Review 工具上 double check 变更集。
2. 审查者 Review 代码。
    - 对 [编写整洁的代码](#编写整洁代码) 中各项要求进行检查
    - 在任何有疑问或建议的地方留 comment。
    - 从中学习一些好的东西。
    - 完成后，如果有问题需要修复，留 comment “Reviewed and waiting for fix”，否则进行第 4 步。
3. 提交者响应 comments 。
    - 确实有问题的，修复之。如果该分支未被其他人使用，应使用 `git commit --amend` 提交以减少不必要的 commit 历史。
    - 不同意的，讨论。
    - 完成后，留 comment “Fixed”，审查者再次检查，回到第二步。
4. 审查者确认没有问题之后，将 Merge Request 转发给目标分支的维护者进行合并。
