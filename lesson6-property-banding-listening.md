# 控件的属性绑定和属性监听,主要使用实现了Property接口的类,参考网址: https://openjfx.io/javadoc/13/javafx.base/javafx/beans/property/Property.html
## 这个接口有几个方法<br>
<img width="1825" height="402" alt="image" src="https://github.com/user-attachments/assets/e96521df-df17-4168-8219-9c5416ba3f0c" /> <br>
## 注意:这个接口继承自Observable接口和一些其他接口,下面有一些继承的方法<br>
<img width="1264" height="512" alt="image" src="https://github.com/user-attachments/assets/a2d3c6e8-577e-4a37-89ce-76137342b6b1" /> <br>
## 我们通过一个案例来学习: jfx_property_binding_listening,我们在场景在添加一个圆,黑色边框,填充白色,代码如下<br>
```
package com.example.jfx_property_binding_listening;

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
        circle.setStroke(Color.BLACK);
        circle.setFill(Color.WHITE);
        AnchorPane root = new AnchorPane();
        root.getChildren().add(circle);
        Scene s = new Scene(root,500,500);
        stage.setTitle("Property Binding!");
        stage.setScene(s);
        stage.show();
    }

    public static void main(String[] args) {
        launch();
    }
}
```
### 运行程序,效果如下<br>
<img width="619" height="656" alt="image" src="https://github.com/user-attachments/assets/df545adc-9832-4712-89aa-87e963bd509c" /> <br>
### 此时你改变窗口的大小,圆是不会有任何变化的,它还是在原来的地方<br>
<img width="1122" height="804" alt="image" src="https://github.com/user-attachments/assets/66cb27c7-aa78-4789-9f93-c232a88836e2" /> <br>
## 我们可以使用属性绑定的方法来使得它可以根据窗口的变化而变化.代码如下:<br>
<img width="1282" height="847" alt="image" src="https://github.com/user-attachments/assets/70ef4726-6157-4368-880c-f17658991035" /> <br>
### 此时无论你怎么改变窗口的大小,圆始终在窗口的中心位置<br>
<img width="947" height="665" alt="image" src="https://github.com/user-attachments/assets/457714d8-cb58-4fe5-92ed-68f3ada6abbc" /> <br>
<img width="601" height="670" alt="image" src="https://github.com/user-attachments/assets/4f78827e-1dfc-4768-92de-c49f40ead110" /> <br>
<img width="595" height="445" alt="image" src="https://github.com/user-attachments/assets/cfb3e927-59ef-4ad2-91d3-1eccb238b6ef" /> <br>
<img width="330" height="440" alt="image" src="https://github.com/user-attachments/assets/895f55cf-2829-49da-9592-0572a945f1f5" /> <br>
## 下面我们来学习如何设置属性监听器,代码如下<br>
```
package com.example.jfx_property_binding_listening;

import javafx.application.Application;
import javafx.beans.value.ChangeListener;
import javafx.beans.value.ObservableValue;
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
        circle.setStroke(Color.BLACK);
        circle.setFill(Color.WHITE);
        AnchorPane root = new AnchorPane();
        root.getChildren().add(circle);
        Scene s = new Scene(root,500,500);
        //属性绑定,将圆心始终绑定到场景中心
        circle.centerXProperty().bind(s.widthProperty().divide(2));
        circle.centerYProperty().bind(s.heightProperty().divide(2));
        //设置属性监听器
        circle.centerXProperty().addListener(new ChangeListener<Number>() {
            @Override
            public void changed(ObservableValue<? extends Number> observable, Number oldVal, Number newVal) {
                System.out.println("X old pos:"+oldVal+",X new Pos:"+newVal);
            }
        });
        circle.centerYProperty().addListener(new ChangeListener<Number>() {
            @Override
            public void changed(ObservableValue<? extends Number> observable, Number oldVal, Number newVal) {
                System.out.println("Y old pos:"+oldVal+",Y new Pos:"+newVal);
            }
        });
        stage.setTitle("Property Binding!");
        stage.setScene(s);
        stage.show();
    }

    public static void main(String[] args) {
        launch();
    }
}
```
### 运行程序,效果如下:<br>
<img width="1561" height="966" alt="image" src="https://github.com/user-attachments/assets/21b8a9fe-5e74-4cbd-a0b7-e320d704a3a6" /> <br>
### 注意:如果不进行属性绑定,后面的监听器是无法监听到改变的.<br>




