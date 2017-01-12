# 目录
[需求分析]
(#1-需求分析)

[总体设计]
(#2-总体设计)

[功能设计]
(#3-功能设计)

[数据库设计]
(#4-数据库设计)

[关键技术]
(#5-关键技术)

[作品亮点]
(#6-作品亮点)

# 1 需求分析
近几年，以信息化为代表的科技进步以及现代商业模式的创新，推动了旅游业的转型升级。尤其是，2013 年国家旅游局提出了“智慧旅游”这一创新性概念，强调旅游信息的“互连互通”、“分析预测”、“主动推送”、“透彻感知”，鼓励充分运用互联网技术、空间信息技术、传感器技术，以及移动开发技术来解决旅游资源信息化过程中遇到的一系列问题。所有问题中，所关注的问题归纳起来，无外乎以下几个方面：1、旅游资源的信息获取，如景点信息、配套设施的查找、定位，顺畅使用；2、旅途安全，出门在外安全是一切的保障，在遭遇紧急情况时需要能迅速获得援助,有突发自然灾害时能第一时间得到告警；3、信息分享，旅游是件快乐的事情，旅客期望分享旅途中的见闻，结交新的朋友。     	
 
因此，研究设计一套服务于旅客、方便快捷的智慧型APP行业软件具有重要的现实意义，能为旅客提供基于位置的景区信息服务，完善的好友交互以及完善的人员安全保障，提升旅客在景区的旅游体验。	

同时，研究一款针对特定旅游景区的后台GIS系统也是必不可少的。GIS景区管理系统是可以让景区管理者更方便、快捷、实用的管理景区，以及对旅客安全的保障和负责。       
# 2 总体设计
## 2.1 总体架构设计
 ![1](https://cloud.githubusercontent.com/assets/19277908/21892282/021328d6-d911-11e6-9785-5cd018a43b8e.png)   
                                               2.1 总体架构设计图     
					       
	总体架构包括以下五个部分：   
（1）展现层：APP行业软件，与服务器脱离，提出请求返回结果，消化结果呈现，为.exe或.apk文件。APP和管理软件也有一定的逻辑处理。     
（2）服务层：采用WCF服务，提供通讯作用，调用业务层。    
（3）业务层：实现具体服务的实现，实现逻辑操作，不与具体数据库关联。       
（4）持久层：采用EF技术，实现数据库操作，包括数据库实体、EF框架、数据库访问帮助类。       
（5）数据库：采用SQL Server数据库进行数据的持久化存储。     
## 2.2 服务架构设计   
服务部分包括了客户端APP所要求的所有服务需求，服务接口设计与具体实现如下：	
 ![2](https://cloud.githubusercontent.com/assets/19277908/21892285/0299fad2-d911-11e6-995c-cbe98ddaa899.png)    
                                                2.2服务接口图          
 ![3](https://cloud.githubusercontent.com/assets/19277908/21892286/02d578d2-d911-11e6-8e1b-28b1bc1e312f.png)       
                                                2.3服务类图      
除此之外，服务部分还有其他数据实体类、数据操作层等，在此不一一列出。         
## 2.3 移动端APP软件架构设计   
移动端APP软件采用C/S结构，采用Xamarin.Android界面构造技术与大量第三方库，达到为用户提供丰富的用户体验，良好的交互方式的目的；利用ArcGIS RunTime SDK 为用户提供强大的GIS专业功能（包括地图展示、实时查询等功能）；将通过各种标准的网络协议实现访问请求，其中出于接口化、标准化的目的，将众多的服务器端操作封装成WCF网络服务，供客户端网络调用，Xamarin.Android UI作为结果呈现层予以表达。软件架构设计如图所示：       	
  ![4](https://cloud.githubusercontent.com/assets/19277908/21892287/02d70db4-d911-11e6-85df-b2a1500e470b.png)       
  ![5](https://cloud.githubusercontent.com/assets/19277908/21892288/02d754ea-d911-11e6-92be-0a3e0d5ac505.png)
                                                2.4 APP软件架构设计图       
	除此之外，移动端还有其他数据实体类、数据操作层等，在此不一一列出。        
# 3 功能设计   
功能设计包括七个大模块，如图所示：  	   
 ![6](https://cloud.githubusercontent.com/assets/19277908/21892290/02d8f746-d911-11e6-8fa1-91c976731416.png)       
## 3.1 功能设计图
（1）地图导航 
	用户在地图上实现空间定位。    
（2）一键呼救     
  ![7](https://cloud.githubusercontent.com/assets/19277908/21892289/02d873d4-d911-11e6-8787-4eda24eb0b81.png)    
	用户在APP中设置好紧急情况电话、短信联系人，在遇到危险时，可立即向好友发送预设呼救短信、向服务器发送当前位置并且拨打一个呼救电话。让用户在紧急情况下迅速完成呼救，为救援者留在尽量多的信息，实现旅客之间的相互救助。    
（3）用户管理    
  ![8](https://cloud.githubusercontent.com/assets/19277908/21892580/7875fc50-d912-11e6-8a44-f658c6370f1a.png)  
	包括注册、登录、修改个人信息、找回密码等功能。实现基本的账号管理功能。   
（4）安全同行    
  ![9](https://cloud.githubusercontent.com/assets/19277908/21892577/7870fc1e-d912-11e6-9c7c-d63c8eb88e24.png)    
	包括用户实时上传位置、查看好友位置与当天行迹等功能。借此可以得到所有用户的移动路径，为可能开展的搜救工作作记录，让搜救的准确性、及时性、成功率得到提升。   
    ![10](https://cloud.githubusercontent.com/assets/19277908/21892579/787515ce-d912-11e6-9cb4-c75abb706ef8.png)     
	多个用户组成群组，用于一次旅行，群组成员可以查询群组内所有用户的位置。方便一次旅行的统一管理与相互帮助。    
（5）旅行足迹    
    ![11](https://cloud.githubusercontent.com/assets/19277908/21892578/7873cc64-d912-11e6-8483-48f046c582bb.png)
	旅客可以将旅途的见闻以文字、图片的形式发布到个人的空间中，形成自己的旅游日志、影集，进行好友间的分享，同时查看好友的足迹。实现旅客之间的交友功能。     
（7）好友管理
    ![12](https://cloud.githubusercontent.com/assets/19277908/21892581/7888e612-d912-11e6-82cc-efe884289431.png)     
	包括查找用户、添加好友、查看好友信息、授权好友管理等功能。借此可以实现旅客之间的互动，相互照应，让旅行变得更加安全放心。     
（8）即时通讯     
    ![13](https://cloud.githubusercontent.com/assets/19277908/21892582/78bc31fc-d912-11e6-867b-b2c5b548bb17.png)      
	用户之间的申请、验证、聊天功能。实现类似QQ的通讯功能。     
# 4 数据库设计       
包括APP软件客户端所需所有数据，数据结构如图所示：	       
 ![14](https://cloud.githubusercontent.com/assets/19277908/21892583/78bc4b92-d912-11e6-863f-7c182362487d.png)        
                                           4.1 服务器数据库数据结构图      
	除此之外，移动端也有本地数据库，存储部分离线数据，采用SQLite数据库。        
# 5 关键技术
（1）GIS移动开发技术         
	ARCGIS Runtime SDK for xamarin(beta)：ARCGIS Runtime SDK针对Xamarin平台的SDK。在本项目中，利用ARCGIS Runtime SDK完成地图显示、定位、查询好友当前位置、查询好友当天行迹、查看群组内所有成员位置、查看旅行足迹的地理轨迹等功能。     
（2）互联网技术     
	互联网技术是在计算机技术的基础上开发建立的一种信息技术。在本项目中，通过互联网技术实现网络通讯，对服务器服务进行访问，实现数据的提交与获取。   
（3）WCF服务      
	Windows Communication Foundation是由微软开发的一系列支持数据通信的应用程序框架。在本项目中，发布的服务为WCF服务。同时通过IIS发布网站，在网站中发布照片，移动端通过正确的网址即可访问到照片。     
（4）ORM+linq to sql       
	ORM指对象关系映射，是一种程序技术，用于实现面向对象编程语言里不同类型系统的数据之间的转换。	     
	SQL Server 是Microsoft 公司推出的关系型数据库管理系统。在本项目中，采用SQL Server作为服务器数据库。利用EF实现ORM技术，采用linq to sql完成对数据库的操作。    
	SQLite是一款轻型的数据库，是遵守ACID的关系型数据库管理系统。在本项目中，移动端采用SQLite作为手机数据库，通过github开源项目实现ORM，通过linq to sql进行数据库的操作。链接：https://github.com/praeclarum/sqlite-net    
（5）即时通讯技术    
	利用Openfire服务器与Matrix库实现即时通讯。     
	Openfire是开源的、基于可拓展通讯和表示协议(XMPP)、采用Java编程语言开发的实时协作服务器，利用Web进行管理。在本项目中，利用Openfire服务器实现IM，实现移动端用户通讯、验证消息、系统消息推送等功能。    
	Matrix是第三方商业库，调用Matrix向Openfire服务器发送消息、接收消息，进行即时通讯。链接：http://www.ag-software.net/matrix-xmpp-sdk/download/     
（6）二维码扫描技术     
	利用github开源项目ZXing，实现二维码的生成和读取。链接：https://github.com/zxing/zxing     
# 6 作品亮点   
（1）不仅充分考虑旅客信息获取与分享的需求，还充分挖掘旅客定位信息的价值，实现了旅客自我定位、互助救援、一键呼救、失联寻踪等诸多安全保障功能，极具专业特色，且实用价值高。     
   ![15](https://cloud.githubusercontent.com/assets/19277908/21892604/9f683aa8-d912-11e6-87b0-74dd501caa62.png)     
（2）充分运用即时通讯与短信推送功能，主动推送资讯，如紧急事态通知、日常咨询通知等，为旅客及时提供有价值的信息。     
   ![16](https://cloud.githubusercontent.com/assets/19277908/21892605/9fd9cf24-d912-11e6-8503-d1bfa0830348.png)     
（3）在旅游App中，融入社交功能，可以分享旅游日志、影集。     
   ![17](https://cloud.githubusercontent.com/assets/19277908/21892607/a017e566-d912-11e6-9dd1-850e7f606813.png)    
