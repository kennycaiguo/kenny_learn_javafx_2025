# JavaFx中的Stage(也叫做舞台)类
## 他有很多属性,常用的属性有title,icon,x,y,width,height,resizable,StageStyle,Modality,event <br>
## 我们可以新建一个项目: jfx_stage来学习 <br>
<img width="1676" height="783" alt="image" src="https://github.com/user-attachments/assets/6d249553-f732-473c-90c1-b5decab8b64b" /> <br>
### 1>我们先不使用idea生成的代码,先自己来写一下,给应用程序设置标题和图标,注意设置图标的写法需要先获取icon集合然后再添加新的图片,用Image类构造,图片放在resources文件夹里面<br>
<img width="1641" height="632" alt="image" src="https://github.com/user-attachments/assets/cd309521-ee7d-4282-862f-3a16f8c57d1e" /> <br>
### 2>窗口默认是可以调整大小的,我们可以把它设置为不可调整 <br>
<img width="1618" height="793" alt="image" src="https://github.com/user-attachments/assets/7f5f5162-8de5-41b6-aa85-c6df3fe0acc2" /> <br>
#### 运行程序,发现最大化按钮变灰,把鼠标移动到窗口边上也不会有箭头,说明的确不可调整大小 <br>
<img width="1587" height="915" alt="image" src="https://github.com/user-attachments/assets/6b2e17d4-c301-40e5-b0e8-980a2784c812" /> <br>
### 3>可以设置窗口的宽度和高度 <br>
<img width="1199" height="688" alt="image" src="https://github.com/user-attachments/assets/3505900e-2f5e-4b68-82b3-26f5b18ec45d" /> <br>
#### 运行程序,窗口就变为我们设置的宽高<br>
<img width="493" height="488" alt="image" src="https://github.com/user-attachments/assets/4b6f56e0-eebb-487e-93ad-909d552eff4c" /> <br>
### 4>可以设置窗口的样式,有StageStyle.DECORATED,StageStyle.UNDECORATED ,StageStyle.TRANSPARENT和StageStyle.UTILITY,其中,StageStyle.UNDECORATED ,StageStyle.TRANSPARENT看不到窗口,默认是StageStyle.DECORATED<br>
<img width="1167" height="615" alt="image" src="https://github.com/user-attachments/assets/e3d2a118-185f-429a-8887-6ab7021f27b6" /> <br>
#### 如果想让StageStyle.UNDECORATED和StageStyle.TRANSPARENT的窗口显示,需要给他设置一个场景<br>
<img width="1087" height="672" alt="image" src="https://github.com/user-attachments/assets/9ae5c8e2-6a88-45d2-9518-b832b34fc9a0" /> <br>
#### 这种窗口非常丑,连个关闭按钮都没有<br>
<img width="1003" height="761" alt="image" src="https://github.com/user-attachments/assets/1a04ea18-71b8-47cf-ab94-687d00ffce5b" /> <br>
### 5>窗口的默认样式是NONE,可以使用stage.intiModality(...)来设置窗口样式.为了演示效果我们给窗口添加了一个按钮,点击这个按钮有创建一个窗口,如果我们不设置样式,默认是非模态的,也就是NONE,我们可以把它设置为
### APPLICATION_MODAL,这个是模态窗口,也就是新窗口弹出后原来的窗口点击不了,必须关闭新窗口,才能操作原来的窗口<br>
<img width="1169" height="649" alt="image" src="https://github.com/user-attachments/assets/8fd97d9a-aaf8-4e8a-b679-66bdaedde67b" /> <br>
#### 效果如下<br>
<img width="977" height="717" alt="image" src="https://github.com/user-attachments/assets/28815587-88ad-4313-af54-80456cdbb6b9" /> <br>
#### WINDOW_MODAL这种样式,我们需要给窗口设置所有者,否则他的模态不起作用,而且它只限制他的父窗口.不限制其他窗口<br>
<img width="1130" height="659" alt="image" src="https://github.com/user-attachments/assets/16de967f-4318-407e-be15-4a539de84abe" /> <br>
### 6>然后我们来学习一下窗口的event,我们给主窗体stage添加一个关闭按钮的事件处理
<img width="1425" height="736" alt="image" src="https://github.com/user-attachments/assets/31a246fb-5961-496b-8050-496f558266d5" /> <br>
#### 运行程序,效果如下 <br>
<img width="976" height="738" alt="image" src="https://github.com/user-attachments/assets/6dc1d5f5-59c9-4372-bcf7-ce49be2b8fad" /> <br>
#### 点击取消,不会关闭,点击ok关闭 <br>
<img width="992" height="750" alt="image" src="https://github.com/user-attachments/assets/edefd1c9-e728-41e4-876f-2ef481af515d" /> <br>
<img width="1258" height="834" alt="image" src="https://github.com/user-attachments/assets/8babd98d-4c22-42ad-817b-6c04f325abac" /> <br>









