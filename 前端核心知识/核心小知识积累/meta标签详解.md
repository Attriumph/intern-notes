# meta标签

## 1.What is meta？
 W3school原文：
> The <meta> tag provides metadata about the HTML document. Metadata will not be displayed on the page, but will be machine parsable.
  Meta elements are typically used to specify page description, keywords, author of the document, last modified, and other metadata.
  The metadata can be used by browsers (how to display content or reload page), search engines (keywords), or other web services.

  总结几点：
  * meat标签提供HTML的元数据（元数据可以理解为物品/事件参数）
  * meat数据不在web显示，但是machine parsable

## 2.属性
Attribute | Value	|Description
-----|-----|-----|
charset|	character_set
content|	text|	Gives the value associated with the http-equiv or name attribute
http-equiv|	content-type default-style  refresh	|Provides an HTTP header for the information/value of the content attribute
name|	application-name <br> author <br>description <br>generator<br> keywords <br>viewport|	Specifies a name for the metadata

## 3.例子

Example 1 - Define keywords for search engines:

        <meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript">
Example 2 - Define a description of your web page:


        <meta name="description" content="Free Web tutorials on HTML and CSS">

Example 3 - Refresh document every 30 seconds:

        <meta http-equiv="refresh" content="30">
Example 4 - Setting the viewport to make your website look good on all devices:

        <meta name="viewport" content="width=device-width, initial-scale=1.0">
## 4.重点理解http-equiv属性

**HTTP服务器通过此属性收集HTTP协议的响应头报文
，此属性的HTTP协议的响应头报文的值应使用content属性描述**

http-equiv示例

        <meta http-equiv="content-type" content="text/html; charset=utf-8" />

告诉浏览器等设备，文件为html文件，且使用了utf8编码
（html5中直接使用charset属性即可）

## 5.Meta Property标签的应用
使用Open Graph Protocol好处：
* 能够正确的分享您的内容到SNS网站
* 帮助您的内容更有效的在SNS网络中传播

Meta Property标签的应用
* 按照您网页的类型，在<head>中添加入meta标签,并填上相应的内容
* 在一个页面上有多个需要标识出的内容
 重复meta标签，将认为og:type 标签是每一段内容的起始处，例如：

      <meta property="og:type" content="video"/>
      <meta property="og:title" content="学习meta"/>
