## 织梦banner模块

作者:Yoby
时间:2018-3-3

### 简介
   在首页或者列表页,以及单页,都会遇到banner广告,织梦自带的广告管理,过于简单,一般banner必须要有标题,连接,图片,这三要素,一个位置就是一组banner.具体显示banner可以使用swiper插件或slick插

### 安装方式 

下载 <https://github.com/logoove/dede-banner>

 1 通过安装包,目录里xml文件就是,通过织梦插件管理即可安装.自动的
2. 手动安装,根据下面提供的表,导入到数据库,然后把所有文件复制到相应路径.最后在菜单添加个访问路径`http://域名/dede/yoby_ad_main.php`

####  数据表,位置表和广告数据表
~~~
CREATE TABLE `dede_yoby_adtype` (
  `id` smallint(6) unsigned NOT NULL AUTO_INCREMENT,
  `typename` varchar(50) DEFAULT NULL COMMENT '分类描述',
  PRIMARY KEY (`id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;

CREATE TABLE `dede_yoby_adlist` (
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT COMMENT '广告数据表',
  `tid` smallint(6) unsigned DEFAULT NULL COMMENT '分类id',
  `title` varchar(200) DEFAULT NULL COMMENT '主标题',
  `title1` varchar(200) DEFAULT NULL COMMENT '副标题',
  `description` varchar(400) DEFAULT NULL COMMENT '广告描述',
  `litpic` varchar(200) DEFAULT NULL COMMENT '图片',
  `url` varchar(200) DEFAULT NULL COMMENT '跳转地址',
  `isshow` tinyint(1) unsigned DEFAULT '1' COMMENT '是否显示',
  `sortrank` int(10) DEFAULT '0' COMMENT '排序',
  `sendtime` int(10) unsigned DEFAULT NULL COMMENT '创建时间',
  PRIMARY KEY (`id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;
~~~

### 文件路径,织梦目录下
~~~
./dede/yoby_ad_main.php
./dede/yoby_ad_list.php
./dede/templets/yoby_ad_main.htm
./dede/templets/yoby_ad_list.htm
./include/taglib/ad.lib.php
./include/Db.class.php
~~~

#### 标签使用说明:typeid:位置id,row:数据条数,orderby:排序字段,orderway:排序方式,desc/asc,titlelen:标题长度

~~~
{dede:ad typeid=1 row=5 orderby='id' orderway='asc' titlelen=20}

序号:[field:global.autoindex/]
id:[field:id/]
标题:[field:title/]
副标题:[field:title1/]
描述:[field:description/]
图片:[field:litpic/]
URL:[field:url/]
时间:[field:sendtime/]

{/dede:ad}
~~~

### 友情链接
swiper <http://3.swiper.com.cn/api/index.html>

slick <http://www.dowebok.com/84.html>