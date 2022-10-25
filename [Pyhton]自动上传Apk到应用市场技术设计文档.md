## **双端：设计方案需包含双端**

须在一个设计文档内同时包含iOS、Android双端的方案，并尽可能双端对齐

存在细节差异时，（小差异）在文档内的章节内分别描述，或（较大的差异）两个子文档中分别介绍

（当前只包含Android端）





## **修订历史**

| 版本 | 修订日期   | 修订者    | 修订内容            |
| :--- | :--------- | :-------- | :------------------ |
| 1.0  | 2021-11-29 | xiaoan.lu | Create              |
| 1.1  | 2021-11-30 | xiaoan.lu | GooglePlay 上传流程 |



## **前言**



###  **1.目的**

原App发布流程较为繁杂且缺乏灵活性，为简化并自动化流程，开发自动上传至发布草稿箱的发布脚本，优化持续性版本发布流程。

|              | 步骤一                                               | 步骤二                                                | 步骤三                                              |
| :----------- | :--------------------------------------------------- | :---------------------------------------------------- | :-------------------------------------------------- |
| **原流程**   | UAT通过后，将Release包上传到GoogleDrive存储空间      | 上传成功后，通知发布经理                              | 发布经理从存储空间取Release包，手动发布到应用商店中 |
| **目标流程** | Local验证UAT通过后，在Scarab打包平台直接调用发布脚本 | 发布脚本将新的Release包上传到发布经理的账号草稿箱保存 | 发布经理核验草稿箱内容后，输入权限信息直接发布      |





###  2.何种场景需要技术方案？

Local验证UAT通过后，预发布最新的Release包。

支持三大应用商店：

- Google Play
- HUAWEI
- Sunmi





###  3.技术方案注意事项

- 该发布脚本仅限内部人员使用，禁止大范围公开，切勿违反《Google Play Developer API 服务条款》，导致面临账号封停、应用下架等风险。

```
Do not use the APIs to offer a developer service or tool which creates, uploads, publishes, distributes or updates apps to the Google Play Store. 
```

- 商米可提供创建项目API，其余应用商店需基于已有项目发布，或手动创建新项目。





## **一、背景及目的**

*同前言-目的。*





## **二、业界主流方案对比**

手动配置发布转化为自动化发布，节省人力。

- [各应用市场渠道预研](https://confluence.shopee.io/pages/viewpage.action?pageId=805485258)





## **三、方案选型**



|          | Scarab打包平台                                               | Python发布脚本                                               |
| :------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| 实现功能 | 加入发布入口发布界面可配置渠道及相关信息一键同步至发布账号草稿箱 | 接入不同市场API实现上传、更新、覆盖等功能加入开关可打包时直接上传对应商店 |
| 其他功能 |                                                              | 抽象共同流程实现复用                                         |





## **四、逻辑架构设计**

*给出整体系统架构图，或者与当前方案相关的部分架构图，包括主要模块、数据流、上下文关系。*

*如果是部分变动，应使用文字描述或者图形标识突出有变化的地方。*





### 1.实现功能逻辑

| 步骤 | 内容                             | 备注                                                         |
| :--- | :------------------------------- | :----------------------------------------------------------- |
| 1    | Scarab平台进行打包成功           |                                                              |
| 2    | 点击发布按钮创建发布版本         | 点击权限                                                     |
| 3    | 发布页面用选择及输入参数         | 选择内容：平台（GooglePlay/HUAWEI/Sunmi/All）国家（ID/PH/VN/TH/SG/MY）发布包（可从打包平台选择）发布状态（灰度/全量/草稿）(锁定为草稿)输入内容：版本号发布申请人 |
| 4    | 点确认键同步至发布经理账号草稿箱 | 核验机制：确认为Release包确认通过LocalUAT确认版本正确确认国家正确 |
| 5    | 通知发布经理进行审核发布（可选） |                                                              |







## **五、核心逻辑详细设计**

*可包括：*

1. *功能详细说明*
2. *模块详细设计，技术难点设计*
3. *扩展性,兼容性设计*
4. *涉及到信息和数据安全风险，如数据泄露；*



### 1.GooglePlay 应用发布主流程

| 步骤 | 官方示意图                                                   | 详细内容                                                     | 备注                                                         |
| :--- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| 测试 | <img src="file:///F:/Users/luxiaoan/Desktop/2022%E6%AF%95%E4%B8%9A%E5%B0%B1%E4%B8%9A/%E7%A6%BB%E8%81%8C%E5%A4%87%E4%BB%BD/[ID][MY][PH][SG][VN][TH]%E8%87%AA%E5%8A%A8%E4%B8%8A%E4%BC%A0Apk%E5%88%B0%E5%BA%94%E7%94%A8%E5%B8%82%E5%9C%BA%E6%8A%80%E6%9C%AF%E8%AE%BE%E8%AE%A1%E6%96%87%E6%A1%A3%20-%20SeaMoney-Merchant%20Service%20Team%20-%20Shopee%20Confluence_files/image2021-11-30_12-17-41.png" alt="img"  /> | 提前发布您的应用程序进行内部测试：用于与内部测试人员共享应用程序，以发现问题并获得早期反馈。选择测试人员创建新版本(用于测试)审核并发布版本(用于测试) | 此步骤无需审核，可设置100名测试人员                          |
| 配置 | ![img](file:///F:/Users/luxiaoan/Desktop/2022%E6%AF%95%E4%B8%9A%E5%B0%B1%E4%B8%9A/%E7%A6%BB%E8%81%8C%E5%A4%87%E4%BB%BD/[ID][MY][PH][SG][VN][TH]%E8%87%AA%E5%8A%A8%E4%B8%8A%E4%BC%A0Apk%E5%88%B0%E5%BA%94%E7%94%A8%E5%B8%82%E5%9C%BA%E6%8A%80%E6%9C%AF%E8%AE%BE%E8%AE%A1%E6%96%87%E6%A1%A3%20-%20SeaMoney-Merchant%20Service%20Team%20-%20Shopee%20Confluence_files/image2021-11-30_12-18-1.png) | 提供有关您的应用的信息并设置您的商店详情：应用访问权限（是否有部分功能有进一步的权限限制）广告设置（是否内部包含广告或插入第三方广告）内容评分（是否接受专业评分机构对应用进行评分）目标用户（设置访问权限下的目标用户及广告投放的用户）新闻应用（是否是新闻内容相关的应用）COVID-19联系人追踪及状态应用程序数据安全（收集何种用户数据及设置公开数据部分） 选择一个应用类别并提供联系方式设置商品详情 | 让人们了解应用程序的内容，管理应用在 Google Play上的组织和呈现方式 |
| 发布 | ![img](file:///F:/Users/luxiaoan/Desktop/2022%E6%AF%95%E4%B8%9A%E5%B0%B1%E4%B8%9A/%E7%A6%BB%E8%81%8C%E5%A4%87%E4%BB%BD/[ID][MY][PH][SG][VN][TH]%E8%87%AA%E5%8A%A8%E4%B8%8A%E4%BC%A0Apk%E5%88%B0%E5%BA%94%E7%94%A8%E5%B8%82%E5%9C%BA%E6%8A%80%E6%9C%AF%E8%AE%BE%E8%AE%A1%E6%96%87%E6%A1%A3%20-%20SeaMoney-Merchant%20Service%20Team%20-%20Shopee%20Confluence_files/image2021-11-30_12-18-39.png)![img](file:///F:/Users/luxiaoan/Desktop/2022%E6%AF%95%E4%B8%9A%E5%B0%B1%E4%B8%9A/%E7%A6%BB%E8%81%8C%E5%A4%87%E4%BB%BD/[ID][MY][PH][SG][VN][TH]%E8%87%AA%E5%8A%A8%E4%B8%8A%E4%BC%A0Apk%E5%88%B0%E5%BA%94%E7%94%A8%E5%B8%82%E5%9C%BA%E6%8A%80%E6%9C%AF%E8%AE%BE%E8%AE%A1%E6%96%87%E6%A1%A3%20-%20SeaMoney-Merchant%20Service%20Team%20-%20Shopee%20Confluence_files/image2021-11-30_12-19-22.png)![img](file:///F:/Users/luxiaoan/Desktop/2022%E6%AF%95%E4%B8%9A%E5%B0%B1%E4%B8%9A/%E7%A6%BB%E8%81%8C%E5%A4%87%E4%BB%BD/[ID][MY][PH][SG][VN][TH]%E8%87%AA%E5%8A%A8%E4%B8%8A%E4%BC%A0Apk%E5%88%B0%E5%BA%94%E7%94%A8%E5%B8%82%E5%9C%BA%E6%8A%80%E6%9C%AF%E8%AE%BE%E8%AE%A1%E6%96%87%E6%A1%A3%20-%20SeaMoney-Merchant%20Service%20Team%20-%20Shopee%20Confluence_files/image2021-11-30_12-20-6.png)![img](file:///F:/Users/luxiaoan/Desktop/2022%E6%AF%95%E4%B8%9A%E5%B0%B1%E4%B8%9A/%E7%A6%BB%E8%81%8C%E5%A4%87%E4%BB%BD/[ID][MY][PH][SG][VN][TH]%E8%87%AA%E5%8A%A8%E4%B8%8A%E4%BC%A0Apk%E5%88%B0%E5%BA%94%E7%94%A8%E5%B8%82%E5%9C%BA%E6%8A%80%E6%9C%AF%E8%AE%BE%E8%AE%A1%E6%96%87%E6%A1%A3%20-%20SeaMoney-Merchant%20Service%20Team%20-%20Shopee%20Confluence_files/image2021-11-30_12-20-24.png) | 配置的更多的测试人员来测试您的应用：初始测试设置设置封闭式测试轨道选择国家和地区选择测试人员创建并推出新版本创建新版本审核并发布版本 允许任何人注册并在GooglePlay上测试您的应用：初始开放任务设置设置开放式测试轨道选择国家和地区创建并推出新版本创建新版本审核并发布版本 通过预注册提高您的应用程序热度：初始预注册任务设置 上传 app bundle 或 APK选择国家和地区添加可选的预注册奖励 在 Google Play 上发布您的应用：初始发布任务设置选择国家和地区创建并推出新版本创建新版本审核并发布版本 | 通过封闭式测试，可以让更多的测试人员测试应用。可以使用电子邮件或 Google 论坛控制访问用户量。   通过开放式测试，任何人都可以在 Google Play 上加入测试。用户可以提供反馈，而不会影响公开评分。   通过预注册，可以在发布之前发布商品详情，以提高用户关注度。当发布时，任何预先注册的用户都会收到下载您的应用程序的通知。   将应用发布到发布轨道，将您的应用发布给 Google Play上的真实用户。 |



[GooglePlay Console - Dashboard](https://play.google.com/console/u/0/developers)





### 2.Google Play Developer Publishing API 工作流程

介绍使用 Google Play Developer Publishing API 的 **Edits 方法**修改应用。

| 步骤         | 接口                                                         | 接口介绍                                     | 备注                                                         |
| :----------- | :----------------------------------------------------------- | :------------------------------------------- | :----------------------------------------------------------- |
| 指定修改应用 | [Edits: Insert](https://developers.google.com/android-publisher/api-ref/rest/v3/edits/insert) | 指定要修改的应用，从而创建新修改。           | 此操作会创建指定应用的新修改。系统会从相应应用的已部署版本中复制应用的初始设置（APK、商品详情、扩展文件等）。 |
| 上传新APK    | [Edits.apks: upload](https://developers.google.com/android-publisher/api-ref/rest/v3/edits.apks/upload) | 上传新 APK。                                 | 此操作会将 APK 置于某个存储区域中，以便将其分配给本修改或后续修改中的某个轨道。 |
| 分配轨道     | [Edits.tracks: update](https://developers.google.com/android-publisher/api-ref/rest/v3/edits.tracks/update)[Edits.tracks: patch](https://developers.google.com/android-publisher/api-ref/rest/v3/edits.tracks/patch) | 将 APK 分配到轨道。更改现有 APK 的轨道分配。 | 轨道分类：测试轨道，例如 `"alpha"` 和 `"beta"`内部测试轨道：`"internal"`正式版轨道：`"production"` |
| 修改应用详情 | [Edits.listings: update](https://developers.google.com/android-publisher/api-ref/rest/v3/edits.listings/update)[Edits.listings: patch](https://developers.google.com/android-publisher/api-ref/rest/v3/edits.listings/patch) | 创建新的本地化应用详情。修改现有应用详情。   |                                                              |
| 修改拓展文件 | [Edits.expansionfiles resource](https://developers.google.com/android-publisher/api-ref/rest/v3/edits.expansionfiles) | 添加或修改扩展文件。                         |                                                              |
| 提交修改     | [Edits: commit](https://developers.google.com/android-publisher/api-ref/rest/v3/edits/commit) | edits 资源中指定的所有更改都会“发布”。       | 需通过验证，与通过 Play 管理中心进行更改时一样，这些更改可能数小时后才能生效。 |



**注意：**

1. 首次创建修改时，该修改是当前部署的应用状态的副本。
2. 只能使用该 API 更改现有应用（已上传至少一个 APK）。
3. 如需发布应用，您必须使用 Play 管理中心。无法使用该 API 将应用状态从“已发布”更改为“未发布”，或填写发布应用所需的法律同意书。
4. 提交修改之前，可更改当前修改或舍弃修改，都不会影响应用当前版本，不影响用户体验。
5. 每位用户一次只能打开一个修改。如果您创建新修改，则已经打开的任何现有修改就会失效。
6. 如果您的修改正在处理，而此时有人通过 Google Play 管理中心对相应应用进行更改，则您的修改将被舍弃，而通过 Play 管理中心进行的更改将会生效。



[GooglePlay Developer API - Edits](https://developers.google.com/android-publisher/api-ref/rest)





### 3.GooglePlay 草稿版本发布流程

本需求仅对草稿版本进行实现，具体修改在[Edits.tracks: update](https://developers.google.com/android-publisher/api-ref/rest/v3/edits.tracks/update)接口中的`“status”`区别，以草稿版本为例，在请求正文中，传递包含您想创建的草稿版本的 [Edits.tracks resource](https://developers.google.com/android-publisher/api-ref/rest/v3/edits.tracks)：

```
`{``"releases"``: [{`` ``"name"``: ``"My draft release"``,`` ``"versionCodes"``: [``"88"``],`` ``"status"``: ``"draft"``}]``}`
```

发布版本状态共有以下几种：

| 发布版本         | 状态码                                        | 状态详情                                                     |
| :--------------- | :-------------------------------------------- | :----------------------------------------------------------- |
| 直接发布         | `"status": "completed"`                       | 提交更改几个小时后线上生效                                   |
| 分阶段发布       | `"userFraction": 0.05,"status": "inProgress"` | 设置接收该版本的用户所占的比例，此处为5%，可查看数据情况随时更改接受用户比例 |
| 暂停分阶段发布   | `"status": "halted"`                          | 以后决定恢复已暂停的版本，只需将其状态重新设为 `"inProgress"` 即可。 |
| 完成分阶段发布   | `"status": "completed"`                       | 对自己分阶段发布的版本感到满意，并想要向所有用户发布相应版本 |
| **草稿版本发布** | `**"status": "draft"**`                       | **提交更改后，可通过 Google Play 管理中心或 API 检查相应草稿版本并进行发布** |

草稿版本流程：

| 接口                                                         | 接口介绍                                                     | 备注                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| [Edits: Insert](https://developers.google.com/android-publisher/api-ref/rest/v3/edits/insert) | 开启新的修改                                                 | 具体参见 2.Google Play Developer Publishing API 工作流程     |
| [Edits.apks: upload](https://developers.google.com/android-publisher/api-ref/rest/v3/edits.apks/upload) | 上传待发布APK                                                | 在该方法的请求正文中传递 APK，针对上传的 APK 返回一个版本代码；将 APK 分配到某个版本时，可使用该版本代码来引用相应的 APK |
| [Edits.tracks: update](https://developers.google.com/android-publisher/api-ref/rest/v3/edits.tracks/update) | 在发布轨道请求正文中，传递包含您想创建的草稿版本的 [Edits.tracks resource](https://developers.google.com/android-publisher/api-ref/rest/v3/edits.tracks) | `{ "releases": [{   "name": "My draft release",   "versionCodes": ["88"],   "status": "draft"  "releaseNotes": [    {"language": "en-US", "text": "Describe what's new in this release."}   ] }]}` |
| [Edits: commit](https://developers.google.com/android-publisher/api-ref/rest/v3/edits/commit) | 提交更改                                                     | 可以通过 Google Play 管理中心或 API 检查相应草稿版本并进行发布 |

`"releaseNotes"` 字段：指定版本说明，在相应版本中指定版本说明来向用户重点介绍相关的新变化。



[GooglePlay Developer API - draft](https://developers.google.com/android-publisher/tracks)





### 4.GooglePlay 发布草稿版本接口

| Method                                                       | Function                    | Path parameters                                              | Query parameters                                             | Request body                              | Response body                                 | HTTP reques                                                  |
| :----------------------------------------------------------- | :-------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :---------------------------------------- | :-------------------------------------------- | :----------------------------------------------------------- |
| [Edits: Insert](https://developers.google.com/android-publisher/api-ref/rest/v3/edits/insert) | 为应用创建一个新的编辑      | packageNamestring应用包名                                    | /                                                            | 请求体包含一个 AppEdit 实例               | 请求成功，返回体包含一个新创建的 AppEdit 实例 | POST `https://androidpublisher.googleapis.com/androidpublisher/v3/applications/**{packageName}**/edits` |
| [Edits.apks: upload](https://developers.google.com/android-publisher/api-ref/rest/v3/edits.apks/upload) | 上传 APK 并添加到当前编辑中 | packageNamestring应用包名editIdstring编辑标识符              | /                                                            | 请求体包含一个 ApksUploadRequestBody 实例 | 请求成功，返回体包含一个 Apk 实例             | 上传 URI，用于媒体上传请求： POST `https://androidpublisher.googleapis.com/upload/androidpublisher/v3/applications/**{packageName}**/edits/**{editId}**/apks`元数据 URI，仅用于元数据请求： POST `https://androidpublisher.googleapis.com/androidpublisher/v3/applications/**{packageName}**/edits/**{editId}**/apks` |
| [Edits.tracks: update](https://developers.google.com/android-publisher/api-ref/rest/v3/edits.tracks/update) | 更新编辑轨道                | packageNamestring应用包名editIdstring编辑标识符trackstring轨道标识符 | /                                                            | 请求体包含一个 Track 实例                 | 请求成功，返回体包含一个 Track 实例           | PUT `https://androidpublisher.googleapis.com/androidpublisher/v3/applications/**{packageName}**/edits/**{editId}**/tracks/**{track****}**` |
| [Edits: commit](https://developers.google.com/android-publisher/api-ref/rest/v3/edits/commit) | 提交应用的编辑              | packageNamestring应用包名editIdstring编辑标识符              | changesNotSentForReviewboolean表示此编辑在通过 Google Play 管理中心 UI 明确发送以供审核之前不会进行审核。 这些更改将添加到尚未发送以供审核的任何其他更改 | 请求题必须为空                            | 请求成功，返回体包含一个新创建的 AppEdit 实例 | POST `https://androidpublisher.googleapis.com/androidpublisher/v3/applications/**{packageName}**/edits/**{editId}**:commit` |

**Tips：**

- 以上接口均需要OAuth服务账户授权
- URL 使用 gRPC 转码语法



[GooglePlay Developer API](https://developers.google.com/android-publisher/api-ref/rest)





### 5.GooglePlay 发布草稿版本接口实例

| Resource         | Description                       | Fileds                                                       | JSON Representation                                          |
| :--------------- | :-------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| AppEdit          | 应用程序编辑，EditsService资源    | idstring仅输出， 编辑的标识符，可以在后续的 API 调用中使用expiryTimeSecondsstring仅输出，该编辑过期失效时间 (as seconds since Epoch) | ```{`` ``"id"``: string,`` ``"expiryTimeSeconds"``: string``}` |
| Apk              | APK 相关信息， ApksService 的资源 | versionCodeintegermanifest文件中指定的 APK 的版本代码binaryobject ([ApkBinary](https://developers.google.com/android-publisher/api-ref/rest/v3/edits.apks#ApkBinary))此 APK 的二进制payload的信息 | `{`` ``"versionCode"``: integer,`` ``"binary"``: {``  ``object (ApkBinary)`` ``}``}` |
| ApkBinary        | 表示 APK 的二进制payload          | sha1stringAPK payload的 sha1 哈希值，编码为十六进制字符串并匹配 sha1sum 命令的输出sha256stringAPK payload的 sha256 哈希值，编码为十六进制字符串并匹配 sha256sum 命令的输出 | `{`` ``"sha1"``: string,`` ``"sha256"``: string``}`          |
| Track            | 轨道配置， TracksService 的资源   | trackstring轨道标识符releases[]object (Release)在读取请求中，表示轨道中的所有活动版本。 在更新请求中，代表所需的更改 | `{`` ``"track"``: string,`` ``"releases"``: [``  ``{``   ``object (Release)``  ``}`` ``]``}` |
| Release          | 轨道内的发布内容                  | namestring版本名称，不需要是唯一的。 如果未设置，名称将从 APK 的 versionName 生成。 如果版本包含多个 APK，则按日期生成versionCodes[]string (int64 format)发行版中所有 APK 的版本代码。 必须包含要从以前的版本中保留的版本代码releaseNotes[]object (LocalizedText)此版本中新增功能的描述statusenum (Status)发布状态userFractionnumber有资格分阶段发布的用户比例。 0 < 分数 < 1。只能在状态为“inProgress”或“halted”时设置countryTargetingobject (CountryTargeting)将发布限制在特定的国家/地区inAppUpdatePriorityinteger版本的应用内更新优先级，该版本中所有新添加的 APK 都将被优先考虑。 可以取 [0, 5] 范围内的值，其中 5 为最高优先级， 默认为 0。一旦发布发布，inAppUpdatePriority 将无法更新。 请参阅 [https://developer.android.com/guide/playcore/in-app-updates](https://developer.android.com/guide/playcore/in-app-updates。) | `{`` ``"name"``: string,`` ``"versionCodes"``: [``  ``string`` ``],`` ``"releaseNotes"``: [``  ``{``   ``object (LocalizedText)``  ``}`` ``],`` ``"status"``: ``enum` `(Status),`` ``"userFraction"``: number,`` ``"countryTargeting"``: {``  ``object (CountryTargeting)`` ``},`` ``"inAppUpdatePriority"``: integer``}` |
| LocalizedText    | 发行说明规范，即语言和文本        | languagestring语言本地化代码（BCP-47 语言标签；例如，奥地利德语的“de-AT”）textstring给定语言的文本 | `{`` ``"language"``: string,`` ``"text"``: string``}`        |
| Status           | 发布状态                          | EnumsstatusUnspecified - 未指定状态draftinProgresshaltedcompleted | 详见 3.GooglePlay 草稿版本发布流程                           |
| CountryTargeting | 国家/地区定位规范                 | countries[]string要定位的国家/地区，指定为两个字母的 [CLDR](https://unicode.org/cldr/charts/latest/supplemental/territory_containment_un_m_49.html) 代码。includeRestOfWorldboolean包括“世界其他地区”以及明确针对的国家/地区。 | `{`` ``"countries"``: [``  ``string`` ``],`` ``"includeRestOfWorld"``: ``boolean``}` |



[GooglePlay Developer API](https://developers.google.com/android-publisher/api-ref/rest)





## **六、接口设计**



### 1.Scarab-Python 接口设计

| 接口名称       | 接口功能                | 请求体参数             | 返回体参数       |
| :------------- | :---------------------- | :--------------------- | :--------------- |
| publish_check  | 发布新Apk权限及信息核验 | 参考四、1.实现功能逻辑 | 状态码及状态信息 |
| publish_detail | 发布新Apk具体参数       | 同上                   | 状态码及状态信息 |





### 2.Python-GooglePlay 接口设计

参考五、4.GooglePlay 发布草稿版本接口。


 