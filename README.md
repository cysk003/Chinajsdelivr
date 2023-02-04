
# 项目介绍
## 前言
#### jsdelivr 项目是2021年12月20日下午因为一些原因jsdelivr已经失去了国内的IPC备案那么导致了 网宿关闭了jsdelivr的 的国内加速 然后切换了 Fastly 在jsDelivr被吊销ICP许可证四个月后的4月28日开始被DNS污染，导致国内访问解析更加困难，现在jsdelivr的情况好不少，但是没有国内节点还是有点慢....大面积红的高ping战士

## jsdelivr国内测试
www.itdog.cn  测试

<img src="https://image.zzko.cn/images/1/2022/10/17/1666015238634d6006005c2.png" alt="1666015234788.png" title="1666015234788.png" />

效果非常不理想 

单ip测试

<img src="https://image.zzko.cn/images/1/2022/10/17/1666015315634d6053e22f7.png" alt="1666015312225.png" title="1666015312225.png" />

自选的时候测试

<img src="https://image.zzko.cn/images/1/2022/10/17/1666015195634d5fdb7cfa6.png" alt="1666015193365.png" title="1666015193365.png" /> 

情况也是如此

<img src="https://image.zzko.cn/images/1/2022/10/09/16653260106342dbbab13a9.png" alt="1665326012497.png" title="1665326012497.png" />
比如说
https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/
直接改成
https://jsd.cdn.zzko.cn/npm/font-awesome@4.7.0/

我的源都在海外目前只有中国香港所以说只要他可以链接的上就可以 某一些jsdelivr节点挂了也没啥问题 我们有智能的流量调度系统会进行健康检查 会主动临时屏蔽有些ip出现的50x 错误 无法访问 等非正常状态码
那么为什么还有优化？
答案很简单 Fastly 节点越多，对于我的源站来说 可以用的结果也大 更加可以分段回源

### 项目概述
在2021年12月21晚上上线的 jsd.eagleyao.com Version 1.0 使用了三台香港LH配合加速
# 项目介绍
## 前言
#### jsdelivr 项目是2021年12月20日下午因为一些原因jsdelivr已经失去了国内的IPC备案那么导致了 网宿关闭了jsdelivr的 的国内加速 然后切换了 Fastly 在jsDelivr被吊销ICP许可证四个月后的4月28日开始被DNS污染，导致国内访问解析更加困难，现在jsdelivr的情况好不少，但是没有国内节点还是有点慢....大面积红的高ping战士

## jsdelivr国内测试
www.itdog.cn  测试

<img src="https://zzko.cn/images/1/2022/10/17/1666015238634d6006005c2.png" alt="1666015234788.png" title="1666015234788.png" />

效果非常不理想 

单ip测试

<img src="https://zzko.cn/images/1/2022/10/17/1666015315634d6053e22f7.png" alt="1666015312225.png" title="1666015312225.png" />

自选的时候测试

<img src="https://zzko.cn/images/1/2022/10/17/1666015195634d5fdb7cfa6.png" alt="1666015193365.png" title="1666015193365.png" /> 

情况也是如此

<img src="https://zzko.cn/images/1/2022/10/09/16653260106342dbbab13a9.png" alt="1665326012497.png" title="1665326012497.png" />
比如说
https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/
直接改成
https://jsd.cdn.zzko.cn/npm/font-awesome@4.7.0/

我的源都在海外目前只有中国香港所以说只要他可以链接的上就可以 某一些jsdelivr节点挂了也没啥问题 我们有智能的流量调度系统会进行健康检查 会主动临时屏蔽有些ip出现的50x 错误 无法访问 等非正常状态码
那么为什么还有优化？
答案很简单 Fastly 节点越多，对于我的源站来说 可以用的结果也大 更加可以分段回源



2022年12月17日
小部分用户反馈访问github某js出现了腾讯007验证，并且无法过验证
目前已经更换为 fastly.jsdelivr.net现阶段回源方式不在使用cdn.jsdelivr.net，海外不受影响
CDN侧设置
<img src="https://image.zzko.cn/images/1/2022/10/17/1666014350634d5c8ead678.png" alt="1666014348071.png" title="1666014348071.png" />

加速架构
用户--CDN---我源站---Fastly--fastly.jsdelivr.net 源站
   
   CDN后发送的域名一律是fastly.jsdelivr.net 世纪互联的融合CDN也是这个策略配置

不要闲着去攻击不然我真的会栓 Q 的 还有好几个是 30Mpbs 的服务器 宽带太小没有加 这些都是在 200Mpbs 以上的的 IP。。。。


测试情况

www.itdog.cn  测试情况

有缓存的情况下

<img src="https://image.zzko.cn/images/1/2022/10/09/16653260606342dbec8e69e.png" alt="1665326059211.png" title="1665326059211.png" />

关闭缓存的情况下

<img src="https://image.zzko.cn/images/1/2022/10/09/16653260926342dc0ccde32.png" alt="1665326091621.png" title="1665326091621.png" />

整体来说性能无差异，但是考虑到正常情况下还是增加了一定缓存 还得到了极大提升 

在4.0版本中 直接全绿
![image](https://user-images.githubusercontent.com/86733666/196892699-08ff55bb-a007-48c6-8cfc-4ccf4c6b7bc3.png)

关于最近大量的香港地区回国产生较高延迟测 
近期 尝试将部分流量灰度转移到azure 国际站号上的jp和日本节点

我们将持续优化中国境内外访问速度

目前使用了
腾讯云

在此声明，良好的运营环境离不开大家的共同努力，不做要求是为了让大家更好的体验，也不存在需要授权许可这一说法，想的是为了你们更快的上线业务，只希望大家合理使用，遵守相关法律法规，

## 使用DNS的建议
### 境内
此外建议使用运营商默认的DNS可以细分到省

公共DNS:腾讯云，阿里云，百度云,华为云

专业DNS:腾讯云，阿里云

DoH Dot Doq Dot:腾讯云

不推荐 114

### 境外

公共DNS: Google ，CloudFlare  ,Microsoft Amazon

不建议使用:opendns PS:动不动拦截镜像站说欺诈

境内用户使用境外DNS会被分到境外节点 可能影响使用体验 
建议参考这里设置对您合适的DNS 获取最佳体验

https://dnsdaquan.com/



一些请求头问题介绍

<img src="https://image.zzko.cn/images/1/2022/10/09/16653261766342dc607dbe7.png" alt="1665326175535.png" title="1665326175535.png" />

在请求头中

ayao: https://www.ayao.ltd

是我的个人主页 想让知道这个负责人的网站 

china-jsdelivr: The jsdelivr mirror station is a public CDN acceleration plan for . It has an effective ICP filing application permit issued by the Chinese government, use Tencent Cloud CDN or Microsoft Azure CDN  or Baidu Cloud CDN  or wangsu Cloud  or jinshan Cloud CDN to provide domestic accelerated services  I believe you can see this sentence. I hope you don't attack the website, personal website maintenance funds are limited The good Internet atmosphere is inseparable from everyones joint efforts.

大体意思就是说
jsdelivr镜像是的公共CDN加速计划。 它具有中国政府颁发的有效的ICP申请许可，使用腾讯云全球内容分发系统 或者世纪互联全球内容分发系统或者 网宿云全球内容分发系统或者金山云全球内容分发系统   or Microsoft Azure CDN  提供国内加速服务，我相信您可以看到这句话。 我希望您不要攻击网站，个人网站维护资金有限，良好的互联网氛围与每个人的共同努力都不分开。

（google机翻）




是项目介绍 介绍了这个项目的具体原因。

GitHub: https://github.com/54ayao/Chinajsdelivr/

项目地址

static-resources: https://www.zzko.cn

是静态域名专属域名

server: ayao

copyright: ayao

维护人标示

<img src="https://image.zzko.cn/images/1/2022/10/09/16653262046342dc7c1034f.png" alt="1665326203448.png" title="1665326203448.png" />

速度测试
还是不错的


不要去CC我 目前没有过多限制请求 （每秒单ip是500Qps  一分钟 1000QPS 单ip）超过1000拉黑呗，什么网站可以让用户每分钟超过1000Qps每分钟的请求？ 这个简单粗暴，但已缓存的资源不影响你，只是被系统暂时停止获取新的资源了，我也相信不会触碰到某些人利益吧。。。公益行为，本来就艰难... 我也希望灰黑产业的大佬别搞我把静态资源随便引用到自己违法违规站点！,就相当于我为违法违规站提供服务，您搞违法的事情，就不要带上我了谢谢，大家都是中国人，中国人别为难中国人，谢谢，我不想成为下一个jsdelivr！！！！CDN侧会保存访问日志，但源站不保留任何人的访问日志！

最近发现了很多Blog主，使用或者是写文章 在这里感谢各个Blog主的认可与支持
当然可以把该项目合法合规的网站， 无需友情链接哦


访问github 推荐使用
https://kgithub.com tan90哥的




## 项目支持
### 我们使用的服务
<a href="https://cloud.tencent.com" id="Qcloud" target="_blank"><img src="https://image.zzko.cn/images/1/2022/10/09/16653262306342dc96dd067.png" width="200" height="55"></a>
<a href="https://cloud.tencent.com" id="Qcloud" target="_blank"><img src="https://image.zzko.cn/images/1/2022/10/09/16653275066342e1929d4fb.png" width="200" height="55"></a>
<a href="https://www.azure.com" id="azure" target="_blank"><img src="https://image.zzko.cn/images/1/2022/10/09/16653263096342dce5c65e8.png">
<a href="https://www1.hi.cn" id="azure" target="_blank"><img src="https://www1.hi.cn/img/logo.svg" width="80" height="50"></a>

### 特别鸣谢
  
<a href="https://cloud.tencent.com" id="Qcloud" target="_blank"><img src="https://image.zzko.cn/images/1/2022/10/09/16653262306342dc96dd067.png" width="200" height="55"></a>
<a href="https://www.azure.com" id="azure" target="_blank"><img src="https://image.zzko.cn/images/1/2022/10/09/16653263096342dce5c65e8.png">
<a href="https://www1.hi.cn" id="azure" target="_blank"><img src="https://www1.hi.cn/img/logo.svg" width="80" height="50"></a>

### 微信赞赏码
  
<img src="https://image.zzko.cn/images/1/2022/10/09/16653271146342e00ac2a46.png?wx" alt="1665327123523.png" title="1665327123523.png" />
   
   ###  QQpay
   202835956
   
   ###PayPal 
   还没想好用户名
   
   ### alipay 支付宝
   发送到:admin@eebbk.top
   

  ### 赞助列表（每周更新一次）
  
<div class="md-typeset__scrollwrap"><div class="md-typeset__table"><table>
<thead>
<tr>
<th align="center">序号</th>
<th align="center">昵称/网站</th>
<th align="center">日期</th>
<th align="center">捐赠方式</th>
<th align="center">金额</th>
  <th align="center">留言/备注</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">1</td>
<td align="center"><a title="腾讯云" href="https://qcloud.com">腾讯云</a></td>
<td align="center">2021/12-长期</td>
<td align="center">源站和CDN</td>
<td align="center">-</td>
  <td align="center">-</td>
</tr>
     <tr>
     <td align="center">2</td>
<td align="center">DCDN</td>
<td align="center">2021/12-长期</td>
<td align="center">源站</td>
<td align="center">-</td>
  <td align="center">地址暂不公开</td>
</tr>


   <tr>
<td align="center">3</td>
<td align="center"><a title="azure" href="https://www.azure.com">azure</a></td>
<td align="center">2022/10/25-2023/10/25</td>
<td align="center">vm/CDN</td>
<td align="center">-</td>
  <td align="center">学生计划</td>
     </tr> 

</tbody>
</table></div></div>

### 优秀站点（每月更新一次）
  
<div class="md-typeset__scrollwrap"><div class="md-typeset__table"><table>
<thead>
<tr>
<th align="center">序号</th>
<th align="center">网站名/网站</th>
<th align="center">站长</th>
</tr>
</thead>
<tbody>
   
<tr>
<td align="center">1</td>
<td align="center"><a title="FatDong" href="https://md7.top">学技术，永不止步</a></td>
<td align="center">MrDeng</td>
</tr>
   
<tr>
<td align="center">2</td>
<td align="center"><a title="勿埋我心" href="https://www.skyqian.com/">勿埋我心</a></td>
<td align="center">勿埋我心</td>
</tr>
   
<tr>
<td align="center">3</td>
<td align="center"><a title="舒夏博客" href="https://blog.sxbai.com/">舒夏博客
</a></td>
<td align="center">舒夏</td>
</tr>
   
<tr>
<td align="center">4</td>
<td align="center"><a title="LX Music" href="https://docs.lxmusic.folltoshe.com/">LX Music
</a></td>
<td align="center">LX Music</td>
</tr>
   
   <tr>
<td align="center">5</td>
<td align="center"><a title="正安在线" href="https://www.gzza.com/">正安在线
</a></td>
<td align="center">正安在线</td>
</tr>
   
   <tr>
<td align="center">6</td>
<td align="center"><a title="xaoxuu" href="https://xaoxuu.com/">xaoxuu
</a></td>
<td align="center">xaoxuu</td>
</tr>
   
   <tr>
<td align="center">7</td>
<td align="center"><a title="xpoet" href="https://picx.xpoet.cn/#/upload">picx
</a></td>
<td align="center">xpoet</td>
</tr>
   
   <tr>
<td align="center">8</td>
<td align="center"><a title="Ling Chen" href="https://biuling.top/">鸟酱的咖啡馆
</a></td>
<td align="center">Ling Chen</td>
</tr>
   
<td align="center">9</td>
<td align="center"><a title="LX Music" href="https://www.rmoe.top/">柳铃
</a></td>
<td align="center">柳铃</td>
</tr>
   
   <tr>
<td align="center">10</td>
<td align="center"><a title="莫莫" href="https://blog.mocn.top/">莫莫
</a></td>
<td align="center">莫莫</td>
</tr>
   
   <tr>
<td align="center">11</td>
<td align="center"><a title="l0w1nd‘s" href="https://blog.itleaf.xyz/">fl0w1nd‘s blog
</a></td>
<td align="center">fl0w1nd‘s</td>
</tr>
   
<tr>
<td align="center">12</td>
<td align="center"><a title="who" href="https://blog.crnmsl.ml">男人至死都是少年
</a></td>
<td align="center">who</td>
</tr>
   

   <tr>
<td align="center">13</td>
<td align="center"><a title="懒得勤快" href="https://masuit.com/">懒得勤快
</a></td>
<td align="center">懒得勤快</td>
</tr>
   

<tr>
<td align="center">14</td>
<td align="center"><a title="14" href="https://klpbbs.com/">苦力怕MC论坛
</a></td>
<td align="center">懒苦力怕BBS</td>
</tr>
   
<tr>
<td align="center">15</td>
<td align="center"><a title="15" href="https://masuit.com/">何孙涛の博客
</a></td>
<td align="center">何孙涛</td>
</tr>
   
   <tr>
<td align="center">16</td>
<td align="center"><a title=cayzlh" href="https://www.cayzlh.com">cayzlh博客
</a></td>
<td align="center">cayzlh</td>
</tr>
   
    <tr>
<td align="center">17</td>
<td align="center"><a title="17 " href="https://www.mcd7.top/">春夏之梦MC服务器
</a></td>
<td align="center">春夏之梦工作室</td>
</tr>
   
    <tr>
<td align="center">18</td>
<td align="center"><a title="blmcpia" href="https://www.blmcpia.com/">blmcpia MC论坛
</a></td>
<td align="center">blmcpia</td>
</tr>
     <tr>
<td align="center">19</td>
<td align="center"><a title="Liynw" href="https://blog.liynw.top/">Liynwの 博客儿
</a></td>
<td align="center">liynw</td>
</tr>
   
   <tr>
<td align="center">20</td>
<td align="center"><a title="akilar" href="https://akilar.top/">akilarの 博客
</a></td>
<td align="center">akilar</td>
</tr>
   
      <tr>
<td align="center">21</td>
<td align="center"><a title="akilar" href="https://trackerslist.com/#/zh">XIU2/TrackersListCollection
</a></td>
<td align="center">TrackersListCollection</td>
</tr>
        
   <tr>
<td align="center">22</td>
<td align="center"><a title="akilar" href="https://cqlkc.top/">cqlkc的博客
</a></td>
<td align="center">cqlkC</td>
</tr>  
   
   <tr>
<td align="center">23</td>
<td align="center"><a title="akilar" href="https://www.j8.market/">J8.Market
</a></td>
<td align="center">Mr.Deng</td>
 
  </tr> 
</tbody>
</table></div></div>

懒得更新了，过几个月再说

只是为了预留个位置。
涉嫌灰黑产的话请发mail，不受理大流量下载。长时间占用下载等等这些没事。我的政策已经够宽了。只求不要违规，我也在这里面强调了很多次。否则到头来和github还有jsdelivr下场一样


 我在强调一遍 禁止违规！！！
 
 
 机场！！！我他妈说的就是你 别逼我我告诉你啊 好几个机场你用nm的国内加速,你是不是没m 看不懂中文？ 还是说你不是中国人看不明白？ 你要是说自己不是中国人 麻烦交250退出一下中国国籍 你加入哪里我不管你，但是你现在是中国人看不懂中文我就要骂你了哈  我第一次在2023-02-01 要求整改完毕 但是没在github更新就算了 我希望在2023-02-10日完成整改，
 
主题:jsd镜像站举报 
收件人:202835956@qq.com
抄送: 54ayao@gmail.com,admin@eebbk.top,ayao@eebbk.top,940376430@qq.com
内容:
举报网站
举报页面
贴图证据f12（）

审核无误之后，将在两个工作日之内屏蔽该网站
如果网站没挂马的话，整改后解除，若一个域名违规超过三次不会在解除

  
  

by:ayao

home:https://www.ayao.ltd

blog:https://blog.ayao.ltd
