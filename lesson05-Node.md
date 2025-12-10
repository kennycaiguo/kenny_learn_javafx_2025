# 我们来学习Node类
## 注意: Node是一个抽象类,如果要学习他的方法,需要使用他的子类,比如所有的可视化控件,如按钮,ImageView....
## 这里我们来学习他的常用属性<br>
<img width="481" height="213" alt="image" src="https://github.com/user-attachments/assets/4a5ac5e3-ebb9-4f94-9e07-9e64f46ab896" /> <br>
### 我们还是不使用fxml,自己手写代码,先设置位置,api是setLayoutX和setLayoutY<br>
<img width="1339" height="713" alt="image" src="https://github.com/user-attachments/assets/81ba504c-b8ba-4916-b607-b5bfb4fde968" /> <br>
### 运行程序,效果如下<br>
<img width="494" height="416" alt="image" src="https://github.com/user-attachments/assets/20a67b6c-e753-4310-97a6-0c458f727345" /> <br>
### 然后,我们可以给他设置样式<br>
<img width="1383" height="794" alt="image" src="https://github.com/user-attachments/assets/8755bccb-2764-4ea3-bfc3-2f308df739cb" /> <br>
### 运行程序,效果如下<br>
<img width="505" height="414" alt="image" src="https://github.com/user-attachments/assets/e3fc19fb-b078-42f0-b453-29c7bace4e86" /><br>
### 然后我们来设置他的宽高,代码如下<br>
```
package com.example.jax_node_study;

import javafx.application.Application;
import javafx.fxml.FXMLLoader;
import javafx.scene.Scene;
import javafx.scene.control.Label;
import javafx.scene.layout.AnchorPane;
import javafx.stage.Stage;

import java.io.IOException;

public class HelloApplication extends Application {
    @Override
    public void start(Stage stage) throws IOException {
          stage.setTitle("Node properties");
          Label lbl = new Label("Hello,JavaFx");
          lbl.setLayoutX(150);
          lbl.setLayoutY(50);
          //标签默认的背景的透明的,设置宽高效果不明显,我们可以先给他设置一个背景色和边框,设宽点
          lbl.setStyle("-fx-background-color: deeppink;-fx-border-color: blue;" +
                  "-fx-border-width:3px");
          //设置宽高
          lbl.setPrefWidth(200);
          lbl.setPrefHeight(200);
          AnchorPane pane = new AnchorPane();
          pane.getChildren().add(lbl);
          Scene s = new Scene(pane,400,300);
          stage.setScene(s);
          stage.show();
    }

    public static void main(String[] args) {
        launch();
    }
}
```
### 运行程序,效果如下<br>
<img width="505" height="408" alt="image" src="https://github.com/user-attachments/assets/68e19997-81d4-4493-b25c-ee2c618feba0" /> <br>
### 还可以设置文本居中<br>
```
package com.example.jax_node_study;

import javafx.application.Application;
import javafx.fxml.FXMLLoader;
import javafx.geometry.Pos;
import javafx.scene.Scene;
import javafx.scene.control.Label;
import javafx.scene.layout.AnchorPane;
import javafx.stage.Stage;

import java.io.IOException;

public class HelloApplication extends Application {
    @Override
    public void start(Stage stage) throws IOException {
//        FXMLLoader fxmlLoader = new FXMLLoader(HelloApplication.class.getResource("hello-view.fxml"));
//        Scene scene = new Scene(fxmlLoader.load(), 320, 240);
//        stage.setTitle("Hello!");
//        stage.setScene(scene);
//        stage.show();
          stage.setTitle("Node properties");
          Label lbl = new Label("Hello,JavaFx");
          lbl.setLayoutX(150);
          lbl.setLayoutY(50);
          //标签默认的背景的透明的,设置宽高效果不明显,我们可以先给他设置一个背景色和边框,设宽点
          lbl.setStyle("-fx-background-color: deeppink;-fx-border-color: blue;" +
                  "-fx-border-width:3px");
          //设置宽高
          lbl.setPrefWidth(200);
          lbl.setPrefHeight(200);
          //设置标签文本居中
          lbl.setAlignment(Pos.CENTER);
          AnchorPane pane = new AnchorPane();
          pane.getChildren().add(lbl);
          Scene s = new Scene(pane,400,300);
          stage.setScene(s);
          stage.show();
    }

    public static void main(String[] args) {
        launch();
    }
}
```
### 效果:<br>
<img width="495" height="419" alt="image" src="https://github.com/user-attachments/assets/81f0d741-6f2a-458f-8807-f85f80804d3b" /> <br>
### 可以用label.setVisible(false)隐藏控件,这里就不演示了<br>
### 可以设置标签的不透明度,比如这里设置为半透明<br>
<img width="1178" height="793" alt="image" src="https://github.com/user-attachments/assets/67e70f56-b902-402a-8915-79044be5d7a0" /> <br>
### 效果如下:<br>
<img width="501" height="415" alt="image" src="https://github.com/user-attachments/assets/e79bc438-9cbf-4b87-bf15-89b983fc05fe" /> <br>
### 可以设置x方向和y方向的平移<br>
<img width="1085" height="777" alt="image" src="https://github.com/user-attachments/assets/17a9aabf-23a7-43b6-a25f-42b764778bf4" /> <br>
### 效果如下: <br>
<img width="496" height="405" alt="image" src="https://github.com/user-attachments/assets/3ee4000a-2b0f-47e8-9b4a-72068a9711de" /> <br>
### 可以设置旋转<br>
<img width="1169" height="718" alt="image" src="https://github.com/user-attachments/assets/0ad73576-3dde-4fa7-bcf6-aa4f2585865c" /> <br>
### 效果: <br>
<img width="493" height="415" alt="image" src="https://github.com/user-attachments/assets/f0457545-678b-4dac-ac8d-b028a3cae6fe" /> <br>
### 设置x方向和y方向的缩放<br>
<img width="1092" height="751" alt="image" src="https://github.com/user-attachments/assets/58292192-c664-410d-a290-4f6a7d493887" /> <br>
### 缩放效果如下<br>
<img width="499" height="412" alt="image" src="https://github.com/user-attachments/assets/9b95fa4c-c5d7-4064-bcc3-54954bd98d99" /> <br>
### 还有parent,scene和id我们以后用到再学习<br>













