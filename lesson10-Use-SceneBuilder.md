# 这一节我们来学习Scene Builder的使用
## 新建一个项目: jfx_scenebuilder_usage
<img width="546" height="579" alt="image" src="https://github.com/user-attachments/assets/7ada5eef-6124-41e2-9d91-d0a202a6dc94" /> <br>
### 1.点击resource里面的hello-view.fxml,然后点击Scene Builder,然后选择默认添加的组件点击右键Delete,就会变为这个样子<br>
<img width="1315" height="916" alt="image" src="https://github.com/user-attachments/assets/2b1c77bf-27bc-48be-843d-75b1a8e515b9" /><br>
### 2.然后我们可以把一个AnchorPane组件拖拽进来<br>
<img width="1222" height="869" alt="image" src="https://github.com/user-attachments/assets/67983564-ada6-4c64-8c39-ec000ce665bb" /><br>
### 3.然后我们切换到text模式,代码是这样子的<br>
<img width="1204" height="613" alt="image" src="https://github.com/user-attachments/assets/a3198284-44cc-41c9-93d2-4793f7479290" /> <br>
### 4.因为我们修改了fxml文件的内容,我们需要把Controller里面没有用的代码删除.先把它留空<br>
<img width="1094" height="456" alt="image" src="https://github.com/user-attachments/assets/dd9cc1a9-89bc-4534-bf31-07ea152d8fc8" /> <br>
#### 运行程序,是没有问题的<br>
<img width="429" height="346" alt="image" src="https://github.com/user-attachments/assets/305c219f-aa54-47c4-a980-2c6494fd1ce3" /><br>
### 5.拖拽一个按钮到AnchorPane中,右边就会有属性面板,可以设置他的属性还可以设置布局和按钮点击代码,我们可以在属性面板里面修改他的文本内容<br>
<img width="1487" height="879" alt="image" src="https://github.com/user-attachments/assets/85ecc7de-1841-4ef2-ad12-02ec1dbd4ca3" /><br>
### 6.如果需要修改按钮的位置,我们可以在布局面板里面调整,比如我们把按钮的layoutY设置小一点,它就会往上跑<br>
<img width="1502" height="837" alt="image" src="https://github.com/user-attachments/assets/a2d27d71-1cc6-40af-bca2-476c6034af25" /><br>
### 7.我们可以点击code面板,然后给按钮添加id<br>
<img width="1314" height="795" alt="image" src="https://github.com/user-attachments/assets/8acea2ba-a431-4b57-b0e0-7725d5697834" /> <br>
### 8.我们可以给按钮添加一个action,也就是点击事件出来函数<br>
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/cc7a6a7c-0430-48b5-bd03-24549e015785" /><br>
#### 注意,我们需要为AnchorPane设置Controller,然后我们需要在Controller里面手写控件的变量定义以及action的代码<br>
<img width="1419" height="643" alt="image" src="https://github.com/user-attachments/assets/5b565d63-bbe7-4190-b016-c14e0bf5346d" /> <br>
<img width="1178" height="756" alt="image" src="https://github.com/user-attachments/assets/22040996-9037-443c-9360-cf7c059dffdd" /><br>
#### 运行程序,效果如下:<br>
<img width="748" height="550" alt="image" src="https://github.com/user-attachments/assets/b2b6d753-9df6-4874-b889-2497f98f2910" /><br>
<img width="753" height="538" alt="image" src="https://github.com/user-attachments/assets/22b4d9a2-5322-42a9-9f03-ba415ee35908" /><br>
### 9.我们可以实现一个功能,就是给面板添加一个DatePicker组件,点击按钮,就把标签的文本改为我们DataPicker选择的日期<br>
<img width="1323" height="836" alt="image" src="https://github.com/user-attachments/assets/0775b819-c0a0-4f6c-afd7-89e2c54c0994" /> <br>
#### 运行程序,效果如下<br>
<img width="743" height="535" alt="image" src="https://github.com/user-attachments/assets/5c3ee798-8929-45df-87bc-7d8e7b758c8c" /><br>
<img width="753" height="536" alt="image" src="https://github.com/user-attachments/assets/27f52249-b82f-43c8-8481-0abfa07afcbc" /><br>
### 10.其实,我们可以给DatPicker添加一个action,把我们选择的日期设置到标签上面<br>
<img width="1635" height="792" alt="image" src="https://github.com/user-attachments/assets/d6c56bbf-92c9-4d0f-aaad-f4dd6cb1cca0" /><br>
<img width="1410" height="695" alt="image" src="https://github.com/user-attachments/assets/2e190523-06dc-408d-b87b-d089f290f39a" /><br>
<img width="1107" height="686" alt="image" src="https://github.com/user-attachments/assets/8530702b-b051-4969-9e1c-6eb544d97bed" /><br>
#### 运行程序,效果如下:
<img width="759" height="561" alt="image" src="https://github.com/user-attachments/assets/ae4bfd34-5dbc-4f17-ad13-b35af8f054f9" /> <br>
<img width="763" height="565" alt="image" src="https://github.com/user-attachments/assets/d4028397-8747-4cbf-9084-74afa520d30b" /> <br>
<img width="750" height="538" alt="image" src="https://github.com/user-attachments/assets/4ab06b8b-f595-47c5-8591-fc7cd7a5d791" /> <br>





















