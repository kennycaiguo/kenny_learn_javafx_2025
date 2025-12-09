# 这一节我们来学习javafx应用程序中的场景类Scene
## 我们通过一个案例来学习
<img width="504" height="438" alt="image" src="https://github.com/user-attachments/assets/c64a4b9b-f286-4a0e-97f7-5705fe57cf6c" /> <br>
### 1>我们先不使用fxml,把它idea生成的代码注释了,我们来手写代码,我们重写HelloApplication类的start方法 <br>
```
package com.example.jfx_scend;

import javafx.application.Application;
import javafx.fxml.FXMLLoader;
import javafx.scene.Group;
import javafx.scene.Scene;
import javafx.scene.paint.Color;
import javafx.scene.shape.Circle;
import javafx.scene.text.Font;
import javafx.scene.text.Text;
import javafx.stage.Stage;

import java.io.IOException;

public class HelloApplication extends Application {
    @Override
    public void start(Stage stage) throws IOException {
          //先不使用fxml
//        FXMLLoader fxmlLoader = new FXMLLoader(HelloApplication.class.getResource("hello-view.fxml"));
//        Scene scene = new Scene(fxmlLoader.load(), 320, 240);
//        stage.setTitle("Hello!");
//        stage.setScene(scene);
//        stage.show();
          //自己手写代码
          Group root = new Group();
          Scene s = new Scene(root,300,200);
          s.setFill(Color.LIGHTGRAY);
          Circle c = new Circle(60,40,30,Color.GREEN);
          Text text = new Text(10,90,"Javafx Scene");
          text.setFill(Color.DARKORANGE);

          Font font = new Font(20);
          text.setFont(font);
          root.getChildren().add(c);
          root.getChildren().add(text);
          stage.setScene(s);
          stage.show();
    }

    public static void main(String[] args) {
        launch();
    }
}
```
## 运行程序效果如下 <br>
<img width="377" height="292" alt="image" src="https://github.com/user-attachments/assets/83793c4d-e059-4514-a60d-87d09978f9b7" /> <br>
### 可以看到,控件必须先添加到场景中,然后再调用stage.setSecene(scene)方法设置场景到窗口中 <br>

## 然后,我们可以开发一个非常有意思的小案例,就是点击按钮换场景,我们需要编写一个crateScene方法来创建自定义场景,然后再创建一个changeScene方法来给窗口切换场景<br>
```
package com.example.jfx_scend;

import javafx.application.Application;
import javafx.fxml.FXMLLoader;
import javafx.scene.Group;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.paint.Color;
import javafx.scene.shape.Circle;
import javafx.scene.text.Font;
import javafx.scene.text.Text;
import javafx.stage.Stage;

import java.io.IOException;

public class HelloApplication extends Application {
    private void changeScene(Stage stage,Scene s){
        stage.setScene(s);
    }

    private Scene createScene(Color clr,String txt,Font f,Button btn) {
        Group root = new Group();
        Scene s = new Scene(root,300,200);
        s.setFill(Color.LIGHTGRAY);
        Circle c = new Circle(60,40,30,clr);
        Text text = new Text(10,90,txt);
        text.setFill(Color.PURPLE);
        Font font = new Font(20);
        text.setFont(font);
        root.getChildren().add(c);
        root.getChildren().add(text);
        if(btn!=null){
            root.getChildren().add(btn);
        }
        return s;
    }

    @Override
    public void start(Stage stage) throws IOException {
//        FXMLLoader fxmlLoader = new FXMLLoader(HelloApplication.class.getResource("hello-view.fxml"));
//        Scene scene = new Scene(fxmlLoader.load(), 320, 240);
//        stage.setTitle("Hello!");
//        stage.setScene(scene);
//        stage.show();
          Button btn = new Button("换场景");
          btn.setLayoutX(10);
          btn.setLayoutY(120);
          Scene s = createScene(Color.DARKORANGE,"JavaFx Scene1",new Font(20),btn);
          btn.setOnAction(e->{
              Button btn2 = new Button("换场景2");
              btn2.setLayoutX(10);
              btn2.setLayoutY(120);
              Scene s2 = createScene(Color.DEEPPINK,"JavaFx Scene2",new Font(20),btn2);
              changeScene(stage,s2);
              btn2.setOnAction(e1->{
                  changeScene(stage,s);
              });
          });
          stage.setScene(s);
          stage.show();
    }

    public static void main(String[] args) {
        launch();
    }
}
```  
## 一运行程序,效果如下<br>
### 刚刚启动时显示第一个场景<br>
<img width="374" height="291" alt="image" src="https://github.com/user-attachments/assets/c53298fa-49e9-490e-a5fc-9b5a5adde6b4" /> <br>
### 点击按钮,就会切换到场景2 <br>
<img width="375" height="285" alt="image" src="https://github.com/user-attachments/assets/2725e0c5-97ec-4aab-a862-c3d86f1f23c2" /> <br>
### 点击按钮,又会切换到场景1 <br>
<img width="376" height="287" alt="image" src="https://github.com/user-attachments/assets/d3f13243-04fd-4c6d-9c21-5cbf2a3f4477" /> <br>
### 一直点击就一直切换...
## 然后我们还可以给不同的场景设置不同的图片,我们先添加2张图片,注意:貌似不支持svg格式<br>
<img width="510" height="544" alt="image" src="https://github.com/user-attachments/assets/3dd9a372-bb33-4844-b8b9-e39c88e5436e" /> <br>
### 修改代码如下
```
package com.example.jfx_scend;

import javafx.application.Application;
import javafx.fxml.FXMLLoader;
import javafx.scene.Group;
import javafx.scene.ImageCursor;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.image.Image;
import javafx.scene.paint.Color;
import javafx.scene.shape.Circle;
import javafx.scene.text.Font;
import javafx.scene.text.Text;
import javafx.stage.Stage;

import java.io.IOException;

public class HelloApplication extends Application {
    private void changeScene(Stage stage,Scene s){
        stage.setScene(s);
    }

    private Scene createScene(Color clr,String txt,Font f,Button btn) {
        Group root = new Group();
        Scene s = new Scene(root,300,200);
        s.setFill(Color.LIGHTGRAY);
        Circle c = new Circle(60,40,30,clr);
        Text text = new Text(10,90,txt);
        text.setFill(Color.PURPLE);
        Font font = new Font(20);
        text.setFont(font);
        root.getChildren().add(c);
        root.getChildren().add(text);
        if(btn!=null){
            root.getChildren().add(btn);
        }
        return s;
    }

    @Override
    public void start(Stage stage) throws IOException {
//        FXMLLoader fxmlLoader = new FXMLLoader(HelloApplication.class.getResource("hello-view.fxml"));
//        Scene scene = new Scene(fxmlLoader.load(), 320, 240);
//        stage.setTitle("Hello!");
//        stage.setScene(scene);
//        stage.show();
          Button btn = new Button("换场景");
          btn.setLayoutX(10);
          btn.setLayoutY(120);
          Scene s = createScene(Color.DARKORANGE,"JavaFx Scene1",new Font(20),btn);
          //设置光标图标
          s.setCursor(new ImageCursor(new Image("cur1.png")));
          btn.setOnAction(e->{
              Button btn2 = new Button("换场景2");
              btn2.setLayoutX(10);
              btn2.setLayoutY(120);
              Scene s2 = createScene(Color.DEEPPINK,"JavaFx Scene2",new Font(20),btn2);
              //设置光标图标
              s2.setCursor(new ImageCursor(new Image("cur2.png")));
              changeScene(stage,s2);
              btn2.setOnAction(e1->{
                  changeScene(stage,s);
              });
          });
          stage.setScene(s);
          stage.show();
    }

    public static void main(String[] args) {
        launch();
    }
}
```
### 运行程序,效果如下<br>
<img width="395" height="295" alt="image" src="https://github.com/user-attachments/assets/dfc05068-f8e6-4ea1-8a4b-66ba1ff97a39" /> <br>
### 切换场景后,效果如下<br>
<img width="379" height="292" alt="image" src="https://github.com/user-attachments/assets/b3fcdf37-93c9-4b8b-b68a-762455a98969" /> <br>





