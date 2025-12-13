# JavaFx多线程编程
## 这一节我们暂时不使用fxml,新建一个项目,起名jfx-multi-thread,然后我们想当用户点击按钮时确定一个线程,来修改标签的文本,我们的代码如下(会有问题)<br>
```
package com.kenny.jfxmultithread;

import javafx.application.Application;
import javafx.fxml.FXMLLoader;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.layout.AnchorPane;
import javafx.stage.Stage;

import java.io.IOException;

public class HelloApplication extends Application {
    @Override
    public void start(Stage stage) throws IOException {
        Label l = new Label("姓名是?");
        l.setLayoutX(200);
        l.setLayoutY(350);
        Button btn = new Button("获取");
        btn.setLayoutX(200);
        btn.setLayoutY(400);
        btn.setOnAction(e->{
            Thread t = new Thread(()->{
                String value="Jackline";
                l.setText(value);
            });
            t.start();
        });
        AnchorPane root = new AnchorPane();
        root.getChildren().addAll(l,btn);
        Scene s = new Scene(root,500,500);
        stage.setTitle("jfx multi-thread");
        stage.setResizable(false);
        stage.setScene(s);
        stage.show();
    }

    public static void main(String[] args) {
        launch();
    }
}
```

### 运行程序,一点击按钮,就会报错<br>
<img width="1637" height="952" alt="image" src="https://github.com/user-attachments/assets/282596d1-0468-40f6-8665-631dfffa35c9" /> <br>
## 解决办法就是调用Platform.runlater()函数,我们修改代码如下<br>
```
package com.kenny.jfxmultithread;

import javafx.application.Application;
import javafx.application.Platform;
import javafx.fxml.FXMLLoader;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.layout.AnchorPane;
import javafx.stage.Stage;

import java.io.IOException;

public class HelloApplication extends Application {
    @Override
    public void start(Stage stage) throws IOException {
        Label l = new Label("姓名是?");
        l.setLayoutX(200);
        l.setLayoutY(350);
        Button btn = new Button("获取");
        btn.setLayoutX(200);
        btn.setLayoutY(400);
        btn.setOnAction(e->{
            Thread t = new Thread(()->{
                String value="Jackline";
                Platform.runLater(()->{
                   l.setText(value);
                });
            });
            t.start();
        });
        AnchorPane root = new AnchorPane();
        root.getChildren().addAll(l,btn);
        Scene s = new Scene(root,500,500);
        stage.setTitle("jfx multi-thread");
        stage.setResizable(false);
        stage.setScene(s);
        stage.show();
    }

    public static void main(String[] args) {
        launch();
    }
}
```
### 运行代码,此时就不会有问题,它其实就是把线程放到一个对了里面,当Application线程空闲的时候再调用这个线程来执行<br>
<img width="640" height="683" alt="image" src="https://github.com/user-attachments/assets/bb3b40e5-0823-4254-8f55-052d75becffb" /> <br>

## 我们可以把上面的代码修改一下,让线程加载一幅网络图片,代码如下<br>
```
package com.kenny.jfxmultithread;

import javafx.application.Application;
import javafx.application.Platform;
import javafx.beans.value.ChangeListener;
import javafx.beans.value.ObservableValue;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.image.Image;
import javafx.scene.image.ImageView;
import javafx.scene.layout.AnchorPane;
import javafx.stage.Stage;

import java.io.IOException;

public class HelloApplication1 extends Application {
    @Override
    public void start(Stage stage) throws IOException {
        ImageView iv = new ImageView();
        iv.setLayoutX(100);
        iv.setLayoutY(20);
        Label l = new Label("");
        l.setLayoutX(200);
        l.setLayoutY(350);
        Button btn = new Button("获取图片");
        btn.setLayoutX(200);
        btn.setLayoutY(400);
        btn.setOnAction(e->{
            Thread t = new Thread(()->{
               Image img = new Image("https://raw.githubusercontent.com/kennycaiguo/nicepics/refs/heads/main/cartoon/ctsg1.jpg",true);
               img.progressProperty().addListener(new ChangeListener<Number>() {
                   @Override
                   public void changed(ObservableValue<? extends Number> observable, Number oldVal, Number newVal) {
                      int progress = (int)(newVal.doubleValue()*100);
                      l.setText("图片加载了"+progress+"%");
                   }
               });
               iv.setImage(img);
            });
            t.setName("线程1");
            t.start();
        });
        AnchorPane root = new AnchorPane();
        root.getChildren().addAll(l,btn,iv);
        Scene s = new Scene(root,500,500);
        stage.setTitle("jfx multi-thread");
        stage.setResizable(false);
        stage.setScene(s);
        stage.show();
    }

    public static void main(String[] args) {
        launch();
    }
}
```

### 运行程序,效果如下:<br>
<img width="636" height="669" alt="image" src="https://github.com/user-attachments/assets/7c90a1fa-da9a-4204-af59-50ec6e39593e" /><br>
### 点击按钮,就可以显示进度以及图片<br>
<img width="620" height="659" alt="image" src="https://github.com/user-attachments/assets/51d71f9e-5f14-4ab6-abe9-96b014aa3d61" /> <br>



