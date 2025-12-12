# 这一节我们来学习fxml布局文件的使用
## 创建一个javafx项目,起名:jfx_fxml
<img width="565" height="608" alt="image" src="https://github.com/user-attachments/assets/9eaf83e5-1779-4e97-847d-d2e2cf7d286d" /> <br>
### 默认idea会帮我们创建一个hello-view.fxml文件和两个类,一个应用程序类,一个是控制器类<br>
### 我们把它默认的代码注释了,我们编写自己的代码,我们先改造hello-view.fxml文件,内容如下: <br>
```
<?xml version="1.0" encoding="UTF-8"?>

<?import javafx.geometry.Insets?>
<?import javafx.scene.control.Label?>
<?import javafx.scene.control.Button?>
<?import javafx.scene.layout.AnchorPane?>
<?import javafx.scene.text.Font?>
<AnchorPane
        xmlns:fx="http://javafx.com/fxml"
        prefHeight="400.0" prefWidth="600.0"
        fx:controller="com.kenny.jfx_fxml.HelloController">
    <children>
       <Label fx:id="txt" text="Hello JavaFX" layoutX="150" layoutY="200">
           <font>
               <Font size="30" />
           </font>
       </Label>
        <Button fx:id="btn" text="向上移动"
                layoutX="150" layoutY="260"
                onAction="#onBtnClick"></Button>
    </children>
</AnchorPane>
```

### 然后我们来改造Controller.java的代码: <br>
```
package com.kenny.jfx_fxml;

import javafx.fxml.FXML;
import javafx.scene.control.Label;

public class HelloController {
    @FXML
    private Label txt;

    @FXML
    protected void onBtnClick() {
        txt.setLayoutY(txt.getLayoutY()-10);
        System.out.println(txt.getLayoutY());
    }
}
```

### 然后再适当修改一下HelloApplication.java的代码
```
package com.kenny.jfx_fxml;

import javafx.application.Application;
import javafx.fxml.FXMLLoader;
import javafx.scene.Scene;
import javafx.scene.layout.Pane;
import javafx.stage.Stage;

import java.io.IOException;

public class HelloApplication extends Application {
    @Override
    public void start(Stage stage) throws IOException {
        Pane root = FXMLLoader.load(getClass().getResource("hello-view.fxml"));
        Scene scene = new Scene(root,600,400);
        stage.setTitle("Hello!");
        stage.setScene(scene);
        stage.show();
    }

    public static void main(String[] args) {
        launch();
    }
}
```
#### 运行程序,效果如下: <br>
<img width="1356" height="844" alt="image" src="https://github.com/user-attachments/assets/dfc85346-d86d-49f6-a995-602e587cde1b" /> <br>
## 注意:我们可以利用idea来帮我们安装Scene Builder插件,这样子就可以想.net开发一样使用拖拽的方式来设计界面了<br>
<img width="1468" height="790" alt="image" src="https://github.com/user-attachments/assets/b0a9e484-713f-487c-86bc-14c90babe426" /> <br>

