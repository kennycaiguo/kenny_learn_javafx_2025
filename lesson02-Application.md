## javafx应用程序中的Application类 <br>
### 1.我们的程序的类都必须集成javafx.application.Application
<img width="1175" height="746" alt="image" src="https://github.com/user-attachments/assets/39866f25-8f19-4369-98d6-952dee4d1b0c" /> <br>
### 2.我们的应用程序必须实现jfx Application的start接口
<img width="1298" height="752" alt="image" src="https://github.com/user-attachments/assets/a4b56c51-271f-4376-a717-bb728a47a64a" /> <br>
### 3.当应用程序需要在main方法里面都有Application的lauch方法,这个方法默认会调用init方法,start方法和stop方法.注意:Application并不会强制你实现init和stop方法,但是必须实现start方法  <br>
### 4.我们可以添加一个init方法,看看它是否会被调用 <br>
<img width="1174" height="706" alt="image" src="https://github.com/user-attachments/assets/0c16e86b-a660-4593-96ef-dc67006bd8af" /> <br>
#### 运行程序,效果如下 <br>
<img width="1648" height="873" alt="image" src="https://github.com/user-attachments/assets/9ec1b294-4622-449b-9a7c-1caa6fead8f9" /> <br>
#### init方法的确被调用了 <br>
### 5.我们也添加一个stop方法,看看它会不会被调用 <br>
<img width="1084" height="559" alt="image" src="https://github.com/user-attachments/assets/e6b85f94-bb1a-4a9b-8c6a-4c6188d90ca6" /><br>
#### 运行程序,init方法调用了,stop方法还没有调用<br>
<img width="1672" height="925" alt="image" src="https://github.com/user-attachments/assets/da242ac5-a600-4453-a99e-fb908e879c1c" /><br>
#### 退出程序,发现此时stop方法被调用了<br>
<img width="1575" height="872" alt="image" src="https://github.com/user-attachments/assets/96986404-68b4-4824-9afd-1f3ab9e7988c" /><br>
### 6.Application类下的getHostServices()方法，该方法返回一个HostServices实例，该实例的showDocument()方法可以指定一个网站地址或者URI
#### 从而以系统默认的浏览器打开该URI。geDocumentBase()返回一个String类型的当前文档所在的路径。 <br>
#### 我们修改运行start方法的代码如下<br>
<img width="1221" height="591" alt="image" src="https://github.com/user-attachments/assets/5e1fb903-cb30-4521-9185-e03d4d82fc95" /><br>
#### 运行程序,发现它会打开Google网站<br>
<img width="1330" height="691" alt="image" src="https://github.com/user-attachments/assets/8434fd08-3ca1-4598-8459-5e40d6820d2a" /> <br>
#### 然后在控制台输出应用程序的路径<br>
<img width="1389" height="623" alt="image" src="https://github.com/user-attachments/assets/acf4c9a8-35e5-4c1a-85e2-096bd3994428" /> <br>
#### 我们发现,此时应用程序不会自动退出,需要我们手动结束<br>
<img width="1400" height="717" alt="image" src="https://github.com/user-attachments/assets/06a68b82-60c4-4e5b-9daa-7693e2c5f052" /> <br>
#### 点击结束按钮,应用程序退出,此时stop方法没有被调用 <br>
<img width="1330" height="409" alt="image" src="https://github.com/user-attachments/assets/4bc24e00-b37b-41b0-99b0-a77ed754afb7" />
#### 注意:线程方面，执行main()方法时是主线程，当调用init()方法时是JavaFX-Launcher线程，当调用start()方法时是JavaFX Application Thread线程，当调用stop()方法时依然是JavaFX Application Thread线程<br>
 <br>
 <br>
 <br>
