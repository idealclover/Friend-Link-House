# idealclover Blogroll

> 🍭 翠翠和他的朋友们的博客更新

[预览链接 blogroll.icl.moe](https://blogroll.icl.moe/)

![](https://s2.loli.net/2022/05/04/KTSp2DoxMEtCZWu.png)

> 仅收录友链博客文章，不代表翠翠本人观点

## 这是什么

因为自己在经营着 [个人网站](https://idealclover.top) ~~别骂了别骂了 会更新的~~ 所以也认识了一些有自己独立博客的校友朋友以及网络小伙伴们。

最初的时候还会时不时去友链中逛逛，但随着这个列表越来越长，自己也就没有时间精力一个个点进去了。往往点进去发现有新的更新，但我却一直没看到。

痛定思痛，想着用 RSS 的方式订阅自己友链们的博客更新，这样可以时常去拜访拜访。

说来也巧，自己的一个学弟 [orangex4](https://orangex4.cool/) 搞了个项目，聚合了我南的一些独立博客。想着就可以魔改一下，用到自己的友链们上。因此趁着五一假期搞了搞。

看了下，原项目的原理是通过 GitHub Actions 每天两次对列表进行爬取，生成出对应的静态网站并更新到 cloudflare workers 上，也是很巧妙了。

代码很强，傻翠就是狗尾续貂改了个小样式就拿来用了~ [预览链接 blogroll.icl.moe](https://blogroll.icl.moe/)

## 如何使用

如果你也想整一个的话，其实也不难，相对还是比较好办的

### Fork 项目

这个就不用我教了吧，看见右上角那个 fork 按钮了不，点就完事了！

生成一个自己的仓库之后好方便做更新和修改。

### 配置 CloudFlare

最重要的是先配置 CloudFlare，让整个链路先跑起来，之后的具体代码再怎么改都来得及。

CloudFlare 的网站在 [这里](https://cloudflare.com/)，注册账号之后先在左侧选中 `workers`， 注册一个 workers

然后在 [这里](https://dash.cloudflare.com/profile/api-tokens) 注册一个 api 密钥，并且在你 fork 的 GitHub 仓库中 `Settings` 的 `Secrets` 里添加一个叫 `CF_WORKERS_TOKEN` 的密钥，把刚刚申请的 api 密钥添加进去

最后进入到 [wrangler.toml](wrangler.toml) 中，修改这个文件里面的 `account_id` 和 `zone_id`，其中 `account_id` 可以在 `workers` 中获取到，而对于 `zone_id`，如果你没有自定义域名的诉求，可以在最前面加井号注释掉

修改完成并同步到 main 分支之后，GitHub Actions 应该会自动启动，观察执行情况就可以了。正常来讲应该会执行成功的。

### 本地部署与修改

既然基础已经跑起来了，接下来需要把它变成自己的，需要修改的有几处，当然，具体修改哪些看你需求：

更便捷的配置化功能什么的，接下来交给学弟实现吧。

- 修改获取的链接：直接修改这个 README.md 中下方的表格就可以了
- 修改 logo 等其他前端展现（已标记 TODO）
  - ./web/public/favicon.ico -- 网站 icon
  - ./src/assets/logo.png -- 页内显示 logo
  - ./src/index.html -- 页面 title
  - ./src/APP.vue -- 页内标题及 banner 文案
- 修改自动生成的 RSS 信息（已标记 TODO）：index.js

在本地想部署起来的话，直接 clone 你自己 fork 出的仓库到本地，然后作为标准 npm 项目去部署

```
# 安装依赖
npm install

# 开发
npm run dev

# 测试 RSS 获取

npm run gen

# 构建
npm run build
```

## 想加翠翠友链？

和 [关于](https://idealclover.top/about.html) 页面中的要求一样，可以在关于页面中进行申请，也可以直接在这个项目中提 [issue](https://github.com/idealclover/blogroll/issues) 或者直接提 [pull request](https://github.com/idealclover/blogroll/pulls)

但不保证照单全收哦！

## LICENSE

项目基于 [NJU-LUG/Blogroll](https://github.com/nju-lug/blogroll)，采用 [MIT Licence](./LICENSE)

## 傻翠的朋友 list

| 名称               | 网站                           | 描述（选填）                                                     | 头像（默认为/favicon.ico）                                                                             | RSS（默认为/feed）                       | 分类        |
| ------------------ | ------------------------------ | ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ | ---------------------------------------- | ----------- |
| idealclover        | https://idealclover.top        | 是翠翠的个人网站！                                               |                                                                                                        |                                          | friend      |
| NJU-LUG            | https://blogroll.njulug.org    |                                                                  |                                                                                                        |                                          | friend      |
| gq's Blog          | https://blog.izgq.net          | gq's blog                                                        | https://zgq.me/favicon.png                                                                             | https://zgq.me/feed.xml                  | friend      |
| bus1996            | https://bus1996.me             |                                                                  | https://bus1996.me/assets/img/favicon.ico                                                              |                                          | friend      |
| HiKi               | https://www.aneureka.cn        |                                                                  | https://www.aneureka.cn/img/favicon.ico                                                                | https://www.aneureka.cn/atom.xml         | friend      |
| lizhihao6          | https://lizhihao6.online       |                                                                  | https://lizhihao6.online/wp-content/uploads/2019/06/cropped-22297584-32x32.jpg                         |                                          | friend      |
| Jennifer's Blog    | https://jyzhangchn.github.io   |                                                                  | https://jyzhangchn.github.io/images/gavin.JPG                                                          |                                          | friend      |
| DIYGod             | https://diygod.me              | 写代码是热爱，写到世界充满爱！                                   | https://4everland.xyz/ipfs/bafybeibefx2tyow77m2wcnsh5anaaxfy7ypxbcuapb52c4h255onqp72ye                 | http://diygod.me/atom.xml                | net         |
| 咸鱼不咸           | https://lcblog.cn              |                                                                  |                                                                                                        |                                          | net         |
| XZYMOE'S BLOG      | https://www.xzymoe.com         |                                                                  |                                                                                                        |                                          | net         |
| Tianyun Zhang      | https://doowzs.com             | doowzs's personal blog                                           |                                                                                                        |                                          | friend      |
| 鹏鹏               | https://blog.chper.cn          |                                                                  |                                                                                                        |                                          | friend      |
| 毛若昕             | https://www.maorx.cn           | 这里是毛若昕的个人主页                                           |                                                                                                        |                                          | friend      |
| 冰凌胧月的小窝     | https://imiku.me               | 聆听最初的声音，向往无尽的未来                                   |                                                                                                        | https://imiku.me/index.xml               | net         |
| Zero               | https://mikuac.com             | 凉风乍起，一叶知秋。                                             | https://mikuac.com/img/avatar.jpg                                                                      | https://mikuac.com/atom.xml              | net         |
| VicBlog            | https://ddadaal.me             |                                                                  |                                                                                                        | https://ddadaal.me/rss.xml               | friend      |
| YSZ 的个人主页     | https://yangshangzhen.com      |                                                                  | https://www.yangshangzhen.com/images/avatar.png                                                        |                                          | friend      |
| 热铁盒             | https://rthsoftware.cn         |                                                                  |                                                                                                        |                                          | friend      |
| iznauy             | https://iznauy.github.io       |                                                                  | https://avatars0.githubusercontent.com/u/22297856?s=400&u=9ac5d0437ef685b62e402ed130d67d589d234f0b&v=4 |                                          | friend      |
| Literature         | https://www.literature.hk      |                                                                  |                                                                                                        |                                          | net         |
| JBESU              | https://jbesu.com              |                                                                  |                                                                                                        |                                          | friend      |
| 青空之蓝           | https://www.ixk.me             | 站在时光一端，回忆过往记忆。                                     | https://ixk.me/_next/image?url=%2Fimage%2Fconfig%2Fauthor%2Favatar.400x400.png&w=1920&q=75             | https://blog.ixk.me/rss.xml              | net         |
| 樱花庄的白猫       | https://2heng.xin              |                                                                  | https://2heng.xin/wp-content/static/favicon-96x96.png                                                  |                                          | net         |
| 水风车             | https://blog.shuifengche.top   |                                                                  |                                                                                                        |                                          | friend      |
| 辣椒の酱           | https://removeif.github.io     | 后端开发，技术分享                                               | https://removeif.github.io/images/avatar.jpg                                                           | https://removeif.github.io/atom.xml      | net         |
| BoBo               | https://hewanyue.com/          | BOHC is just a blog of hechao                                    | https://hewanyue.com/images/favicon.ico                                                                | https://hewanyue.com/atom.xml            | friend      |
| Domon              | https://www.domon.cn           | Life is Simple.                                                  |                                                                                                        | https://www.domon.cn/rss                 | net         |
| BOHC!              | https://hewanyue.com           |                                                                  | https://hewanyue.com/images/favicon.ico                                                                |                                          | net         |
| SangSir            | https://sangsir.com            |                                                                  |                                                                                                        |                                          | net         |
| 恶魔菌の记事簿     | https://meow3.family.blog      |                                                                  |                                                                                                        |                                          | net         |
| 蓝小柠的博客       | https://bleshi.com             | 是可爱的蓝孩子呀—                                                |                                                                                                        |                                          | net         |
| 宇宙よりも遠い場所 | https://kirainmoe.com          |                                                                  |                                                                                                        | https://kirainmoe.com/index.xml          | net         |
| Souta              | https://souta.cc               |                                                                  |                                                                                                        |                                          | net         |
| NoneData           | https://www.nonedata.com       |                                                                  | https://gravatar.loli.net/avatar/8195a7772cd06cfc4fa303770d577c97                                      | https://www.nonedata.com/atom.xml        | net         |
| dna049             | https://dna049.com             |                                                                  |                                                                                                        |                                          | net         |
| Mengzelev's Blog   | https://mengzelev.github.io    |                                                                  | https://mengzelev.github.io/assets/moe.ico                                                             |                                          | friend      |
| beyondstars        | https://exploro.one            |                                                                  |                                                                                                        | https://idx.best/api/feeds/atom          | supporter   |
| Sukka              | https://blog.skk.moe           |                                                                  |                                                                                                        | https://blog.skk.moe/atom.xml            | net         |
| fengkx             | https://www.fengkx.top         |                                                                  | https://www.fengkx.top/images/icons/icon-128x128.png                                                   | https://www.fengkx.top/atom.xml          | friend      |
| JosePhilo          | https://josephilo.com          |                                                                  |                                                                                                        |                                          | net         |
| 蝉时雨             | https://chanshiyu.com          |                                                                  |                                                                                                        |                                          | lost-net    |
| ChrAlpha 的幻想乡  | https://ichr.me                |                                                                  | https://cdn.jsdelivr.net/npm/ckx@0.0.1/favicon/favicon-32x32.png                                       | https://blog.ichr.me/atom.xml            | net         |
| SpencerWoo         | https://spencerwoo.com         |                                                                  | https://spencerwoo.com/assets/logo.png                                                                 | https://spencerwoo.com/feed.xml          | supporter   |
| LadderOperator     | https://ladderoperator.top     |                                                                  | https://ladderoperator.top/img/favicon.jpg                                                             | https://ladderoperator.top/index.xml     | friend      |
| 木子的博客         | https://blog.k8s.li            | 垃圾佬、搬砖社畜、运维工程师                                     |                                                                                                        |                                          | net         |
| c0sMx              | https://www.c0smx.com          |                                                                  | https://c0smx.lajiya.cn/favicon.ico                                                                    |                                          | net         |
| 云游君的小站       | https://www.yunyoujun.cn       | 希望能成为一个有趣的人。                                         | https://www.yunyoujun.cn/favicon.svg                                                                   | https://www.yunyoujun.cn/atom.xml        | net         |
| 猫鱼的小站         | https://2cat.net               | 記錄貓魚日常嘅生活感受同好玩趣事。                               | https://2cat.net/wp-content/uploads/2020/04/cropped-YZSC.TAOBAO.COM-24-192x192.png                     | https://2cat.net/?feed=rss2              | net         |
| MiaoTony's 小窝    | https://miaotony.xyz           | 仰望星空，脚踏实地，未来可期                                     |                                                                                                        | https://miaotony.xyz/atom.xml            | net         |
| Timegg             | https://timegg.top             |                                                                  | https://timegg.top/images/favicon.ico                                                                  | https://timegg.top/index.xml             | lost-net    |
| Aengus Blog        | https://www.aengus.top         | Stay Hungry, Stay Foolish.                                       | https://img.aengus.top/common/profile.png                                                              | https://www.aengus.top/rss.xml           | net         |
| ALID               | https://calmtime.github.io     |                                                                  | https://calmtime.github.io/img/avatar-my.jpg                                                           |                                          | friend      |
| klaus & laura      | https://klauslaura.cn          |                                                                  |                                                                                                        |                                          | net         |
| Kant               | https://deathfugue.com/        |                                                                  |                                                                                                        | https://deathfugue.com/index.php/feed/   | net         |
| Orangex4           | https://orangex4.cool          |                                                                  | https://orangex4.cool/images/icons/profile.jpg                                                         | https://orangex4.cool/atom.xml           | lost-friend |
| GeRongcun          | https://www.gerongcun.xyz/blog |                                                                  |                                                                                                        |                                          | friend      |
| 王荣胜             | https://sqdxwz.com             |                                                                  |                                                                                                        |                                          | net         |
| 小丁的个人博客     | https://tding.top              |                                                                  | https://tding.top/images/avatar.webp                                                                   | https://tding.top/atom.xml               | lost-net    |
| 风景工作室         | https://aspire.studio          |                                                                  |                                                                                                        |                                          | lost-net    |
| Manami             | https://www.manami.top         |                                                                  |                                                                                                        |                                          | net         |
| Oasis's Blog       | https://blog.imoasis.cn        |                                                                  |                                                                                                        |                                          | net         |
| 不鉴的安全屋       | https://ryushane.com           |                                                                  |                                                                                                        |                                          | friend      |
| 吴志成的博客       | https://hitigerzzz.github.io   |                                                                  |                                                                                                        |                                          | friend      |
| 南雍随笔           | https://ydjsir.com.cn          |                                                                  | https://ydjsir.com.cn/img/avatar.png                                                                   | https://ydjsir.com.cn/atom.xml           | friend      |
| Cyris              | https://cyris.moe              |                                                                  | https://cyris.moe/images/favicon.ico                                                                   | https://sound.cyris.moe/atom.xml         | net         |
| Dejavu's Blog      | https://blog.dejavu.moe        | Not for success, just for growing.                               | https://blog.dejavu.moe/avatar.webp                                                                    | https://blog.dejavu.moe/index.xml        | net         |
| remiliacn          | https://www.remiliacn.com      | 东拼西凑的个人小站                                               | https://avatars.githubusercontent.com/remiliacn                                                        |                                          | net         |
| 青鱼博客           | https://qingyu.me              |                                                                  |                                                                                                        |                                          | friend      |
| 太隐               | https://www.wangyurui.top      | 一个人的思想发育史就是他的阅读史                                 | https://i.typlog.com/wangyr45/8354037003_3266735.png?x-oss-process=style/ss                            | https://wangyurui.com/feed.xml           | net         |
| 送报少年           | https://okarin.cn              |                                                                  |                                                                                                        |                                          | net         |
| itsNekoDeng        | https://dyfa.top               |                                                                  | https://nekodeng.gitee.io/medias/avatar.jpg                                                            |                                          | net         |
| LarryZhao          | https://larryzhao.com          |                                                                  | https://larryzhao.com/headimg.png                                                                      | https://feeds.feedburner.com/larryzhao   | friend      |
| Pemp's Blog        | https://pemp.top               |                                                                  | https://pemp.top/images/logo.jpg                                                                       |                                          | friend      |
| SkyWT              | https://skywt.cn               | 热爱与激情永不止息。                                             | https://blog.skywt.cn/usr/themes/Daydream/assets/img/avatar.png                                        | https://skywt.cn/rss.xml                 | net         |
| Anomie ZJU         | https://dong2000.xyz           | A blog of whatever goes                                          | https://dong2000.xyz/wombo.png                                                                         | https://dong2000.xyz/index.xml           | net         |
| Cysime Moflu       | https://blog.cysi.me           | 再不会遇见第二个时光                                             | https://image.glaceon.net/uploads/202205012353016.jpg                                                  | https://blog.cysi.me/index.xml           | net         |
| RK blog            | https://blog.ohtoai.fun/       | Think N Thought                                                  | https://blog.ohtoai.fun/assets/avater.png                                                              |                                          | net         |
| Good Morning       | https://y-ichen.github.io      | 子喵的个人博客站！                                               | https://y-ichen.github.io/img/favicon.png                                                              | https://y-ichen.github.io/atom.xml       | friend      |
| Chlorine           | https://www.yoghurtlee.com     | Como el viento.                                                  | https://img.clnya.fun/chlorine-juice-safer.avif                                                        |                                          | net         |
| 烫烫烫的记事本     | https://leostudiooo.github.io/ | Stay hungry, stay foolish.                                       | https://cdn.jsdelivr.net/gh/leostudiooo/leostudiooo.cdn/img/avatar.jpg                                 | https://leostudiooo.github.io/atom.xml   | net         |
| 山茶花舍           | https://irithys.com            | 吕楪在记录自己的生活                                             | https://pic.imgdb.cn/item/63e38acc4757feff3372eb7e.webp                                                | https://irithys.com/rss/                 | net         |
| 张洪 Heo           | https://blog.zhheo.com         | 分享设计与科技生活                                               | https://bu.dusays.com/2022/12/28/63ac2812183aa.png                                                     | https://blog.zhheo.com/rss.xml           | net         |
| f2h2h1's blog      | https://f2h2h1.github.io       | 覆舟水是苍生泪，不到横流君不知                                   | https://f2h2h1.github.io/avatar.png                                                                    | https://f2h2h1.github.io/rss.xml         | net         |
| 精灵王             | https://jingling.im            | 专注于全栈开发技术分享和开源项目讨论                             | https://jingling.im/assets/jingling.svg                                                                | https://jingling.im/rss.xml              | net         |
| Guava’s Blog       | https://www.humbleguava.top    | Guava’s Blog                                                     |                                                                                                        | https://www.humbleguava.top/rss/feed.xml | friend      |
| LoveApple的主页    | https://loveapple.icu          | 一条喜欢苹果的水煮鱼                                             | https://loveapple.icu/img/machinist.jpg                                                                | https://loveapple.icu/rss.xml            | friend      |
| 龙场茶室           | https://blog.peterchen97.cn    | 一只练习时长六年半的 Web 开发练习生，这是他的一些杂文，欢迎交流~ | https://blog.peterchen97.cn/favicon.svg                                                                | https://blog.peterchen97.cn/rss.xml      | net         |
