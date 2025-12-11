# 这一节我们来学习颜色,字体和图片
## 我们通过一个实例来学习:jfx_color_font_image<br>
<img width="535" height="519" alt="image" src="https://github.com/user-attachments/assets/451e099a-0761-47d3-b6f4-8403e533e35f" />

### 1,先来看Color类,我们发现它有很多构造方法,参考网址:https://openjfx.io/javadoc/13/javafx.graphics/javafx/scene/paint/Color.html<br>
<img width="1117" height="655" alt="image" src="https://github.com/user-attachments/assets/05a095dd-ceed-4a02-9839-4b6f7e589b06" /> <br>
#### 实例代码如下<br>
```
package com.example.jfx_color_font_image;

import javafx.application.Application;
import javafx.fxml.FXMLLoader;
import javafx.scene.Scene;
import javafx.scene.layout.AnchorPane;
import javafx.scene.paint.Color;
import javafx.scene.shape.Circle;
import javafx.stage.Stage;

import java.io.IOException;

public class HelloApplication extends Application {
    @Override
    public void start(Stage stage) throws IOException {
        Circle circle = new Circle();
        circle.setCenterX(250);
        circle.setCenterY(250);
        circle.setRadius(100);
        //颜色有多种构造方法
//        circle.setFill(Color.web("#f66b09"));
//        circle.setFill(Color.rgb(100,180,250));
        circle.setFill(Color.DEEPPINK);
        //设置边框宽度
        circle.setStrokeWidth(5);
        //设置边框颜色
        circle.setStroke(Color.LIGHTGRAY);

        AnchorPane root = new AnchorPane();
        root.getChildren().add(circle);
        Scene s = new Scene(root,500,500);
        stage.setTitle("JavaFx Color_font_image");
        stage.setScene(s);
        stage.show();
    }

    public static void main(String[] args) {
        launch();
    }
}
```
#### 运行程序,效果如下<br>
<img width="635" height="667" alt="image" src="https://github.com/user-attachments/assets/0fa53e04-a235-4781-9906-8e1421bf6f2d" /> <br>

### 2.接下来我们来学习一下Font类,参考网址:https://openjfx.io/javadoc/13/javafx.graphics/javafx/scene/text/Font.html<br>
### Font类有2个构造方法<br>
<img width="1291" height="325" alt="image" src="https://github.com/user-attachments/assets/a7834abd-b70a-408a-a672-11fbf13f79c8" /> <br>
### 然后它有很多方法<br>
```
Method Summary
All MethodsStatic MethodsInstance MethodsConcrete Methods
Modifier and Type	Method	Description
boolean	equals​(Object obj)	
Indicates whether some other object is "equal to" this one.
static Font	font​(double size)	
Searches for an appropriate font based on the default font family name and given font size.
static Font	font​(String family)	
Searches for an appropriate font based on the given font family name and default font size.
static Font	font​(String family, double size)	
Searches for an appropriate font based on the font family name and size.
static Font	font​(String family, FontPosture posture, double size)	
Searches for an appropriate font based on the font family name and posture style.
static Font	font​(String family, FontWeight weight, double size)	
Searches for an appropriate font based on the font family name and weight style.
static Font	font​(String family, FontWeight weight, FontPosture posture, double size)	
Searches for an appropriate font based on the font family name and weight and posture style.
static Font	getDefault()	
Gets the default font which will be from the family "System", and typically the style "Regular", and be of a size consistent with the user's desktop environment, to the extent that can be determined.
static List<String>	getFamilies()	
Gets all the font families installed on the user's system, including any application fonts or SDK fonts.
String	getFamily()	
Returns the family of this font.
static List<String>	getFontNames()	
Gets the names of all fonts that are installed on the users system, including any application fonts and SDK fonts.
static List<String>	getFontNames​(String family)	
Gets the names of all fonts in the specified font family that are installed on the users system, including any application fonts and SDK fonts.
String	getName()	
The full font name.
double	getSize()	
The point size for this font.
String	getStyle()	
The font specified string describing the style within the font family.
int	hashCode()	
Returns a hash code for this Font object.
static Font	loadFont​(InputStream in, double size)	
Loads a font resource from the specified input stream.
static Font	loadFont​(String urlStr, double size)	
Loads a font resource from the specified URL.
static Font[]	loadFonts​(InputStream in, double size)	
Loads font resources from the specified input stream.
static Font[]	loadFonts​(String urlStr, double size)	
Loads font resources from the specified URL.
String	toString()	
Converts this Font object to a String representation.
Methods inherited from class java.lang.Object
clone, finalize, getClass, notify, notifyAll, wait, wait, wait
```

### 我们也通过一个小例子来学习,还是这个项目,我们新建另外一个文件:HelloApplicationFont.java<br>
#### 需要注意,如果你想改变字体,使用Font.font("字体文件名称",字体大小)这个方法是获取不到系统字体的,最好把一个需要使用的字体放到resources/fonts/文件夹里面,然后
#### 使用Font.loadFont(getClass().getResource("/fonts/字体文件.ttf").toString(),字体大小)来获取.代码如下:<br>
```
package com.example.jfx_color_font_image;

import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Label;
import javafx.scene.layout.AnchorPane;
import javafx.scene.paint.Color;
import javafx.scene.shape.Circle;
import javafx.scene.text.Font;
import javafx.scene.text.FontWeight;
import javafx.stage.Stage;

import java.io.FileInputStream;
import java.io.IOException;

public class HelloApplicationFont extends Application {
    @Override
    public void start(Stage stage) throws IOException {
        Label lbl = new Label("你好,我好,大家好");
        lbl.setLayoutX(180);
        lbl.setLayoutY(250);
        //这种不太灵活
//      Font font = Font.loadFont(new FileInputStream("src/main/resources/STXINGKA.TTF"),20);
        //这个比较灵活
        Font font = Font.loadFont(
                this.getClass().getResource("/fonts/STXINGKA.TTF").toString(),30);
        lbl.setFont(font);
        AnchorPane root = new AnchorPane();
        root.getChildren().add(lbl);
        Scene s = new Scene(root,500,500);
        stage.setTitle("JavaFx Color_font_image");
        stage.setScene(s);
        stage.show();
    }

    public static void main(String[] args) {
        launch();
    }
}
```
#### 运行程序效果如下<br>
<img width="1261" height="755" alt="image" src="https://github.com/user-attachments/assets/b870b6f8-88f2-43f9-8e59-f356864fc2cf" /> <br>








