# 官方资料入口与解读边界

以下是研究起点，不是本次已验证证据。遇到对应场景时打开核对。不要一次读取无关来源。

| 场景 | 官方入口 | 使用要点 |
| --- | --- | --- |
| URL 结构 | https://developer.mozilla.org/en-US/docs/Learn_web_development/Howto/Web_mechanics/What_is_a_URL | 协议、主机、路径、查询和片段；片段一般不随 HTTP 请求发给服务端 |
| 示例域名 | https://www.iana.org/help/example-domains | example.com / .org / .net 用于文档演示，track.example.com 不能当作实际广告服务 |
| Google UTM | https://support.google.com/analytics/answer/10917952 | source 来源、medium 媒介、campaign 活动、id 活动编号、term 付费关键词、content 区分素材/链接位置；解释值的命名和报表使用，不保证页面已接入采集 |
| Google 广告点击 ID | https://support.google.com/google-ads/answer/9744275 | GCLID 与自动标记、广告跟踪、归因和数据关联；不是所有点击 ID 的统一规范 |
| GitHub 网站用途 | https://docs.github.com/en/get-started/start-your-journey/about-github-and-git | 代码托管、版本、协作；仓库页面与部署站点分开。路径需结合实际资源解释 |
| Apple 跟踪授权 | https://developer.apple.com/documentation/apptrackingtransparency | 若普通页只返回 JS 壳，可尝试官方 Markdown：https://developer.apple.com/tutorials/data/documentation/apptrackingtransparency.md；用于授权边界，具体 IDFA 获取另查对应官方接口 |

百度、美团、微信、抖音、淘宝等平台的路径和参数，按当前精确域名与业务查官方资料；不预置“看见某字段就认定某用途”的全局映射。共享域名下的商家页、用户站点和平台自营入口区分开。

## 业务讲解示意

输入：`https://shop.example.com/products/shoes?utm_source=newsletter&utm_medium=email&utm_campaign=autumn_launch&utm_content=hero_button`

- 网站身份：示例域名，不能说是已核实的真实电商；路径展示了一个商品页的示意写法。
- 整体用途：示意商品地址携带邮件活动标签；运营借此把访问按来源、媒介、活动和位置分类，前提是目标站点已正确接入相关分析。
- `utm_content=hero_button`：参数用于区分素材或链接位置；当前英文标签可以理解为顶部主视觉区按钮，但具体对应哪一按钮由运营命名约定。示意做法是顶部填 hero_button、底部填 footer_button，在报表中比较表现。两处填同一值就难以区分。
- 不应说：这个商品真实存在、已经收到邮件流量、按钮已经产生转化，或这些参数自动开启了统计。

## 没有协议时怎么办

`event=7`：可观察到事件代码为 7；不能从其他平台的代码表套用成注册或支付。说明谁使用事件代码、为什么要映射，并查本平台枚举。

`amount=100`：有数值 100；缺少单位、币种、实付/应付口径时，不能解释为收入 100 元。

`source=google`：不要当作 utm_source 的等价标准。先查当前平台对 source 的定义。

`callback=https%3A...`：先解码看接收地址，区分它所属平台、入口路径和字段，再判断候选通知方向。配置地址不等于调用记录。
