# 这一节我们来学习颜色,字体和图片
## 我们通过一个实例来学习:jfx_color_font_image<br>
<img width="535" height="519" alt="image" src="https://github.com/user-attachments/assets/451e099a-0761-47d3-b6f4-8403e533e35f" />

### 1,先来看Color类,我们发现它有很多构造方法<br>
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

### 2.接下来我们来学习一下Font类<br>
### Font类有2个构造方法<br>
<img width="1291" height="325" alt="image" src="https://github.com/user-attachments/assets/a7834abd-b70a-408a-a672-11fbf13f79c8" /> <br>




