# JavaFx事件驱动编程
## 先来学习一些基本知识
### 1.事件类<br>
<img width="1029" height="638" alt="image" src="https://github.com/user-attachments/assets/684a1c40-daec-47b6-b367-f45e61ae5b47" /> <br>
#### 层级关系<br>
<img width="893" height="242" alt="image" src="https://github.com/user-attachments/assets/6d392d90-0b0f-46f4-94dc-361531ec77d4" /> <br>
### 2.事件处理器<br>
```
Handler这个单词就是处理器的意思,意思就是事件的处理它全包了。

(一) ActionEvent类事件：

ActionEvent事件注册：.setOnAction(处理器对象);

0.最原始的写法：
（1）、本类实现接口：

/*1*/class MyEventHandler implements EventHandler<ActionEvent>{
		@Override
		public void handle(ActionEvent e){
			//事件的逻辑......
		}
	}
/*2*/MyEventHandler myEventHandler=new MyEventHandler();
/*3*/Button myButton=new Button("我的按钮");
/*4*/myButton.setOnAction(myEventHandler);
java运行
（2）、外部类实现接口（实例）：

public class Controller extends Application /*implements EventHandler<ActionEvent> */{
    private Button mButton=new Button("点我切换文本");
    public static Label mLabel=new Label("你好");//静态成员方便外部类直接访问
    public static boolean flag=true;
    @Override
    public void start(Stage primaryStage) throws Exception {
        mButton.setOnAction(new MyEventHandler());

        HBox mPane=new HBox(mButton,mLabel);
        Scene mScene=new Scene(mPane,300,100);

        primaryStage.setTitle("切换文本");
        primaryStage.setScene(mScene);
        primaryStage.show();
    }
    /*************************************************************/
    public static void main(String[] args) {
        launch(args);
    }

}
//外部类实现接口
class MyEventHandler implements EventHandler<ActionEvent>{
    @Override
    public void handle(ActionEvent event) {
        if (Controller.flag){
            Controller.mLabel.setText("你好");
            Controller.flag=false;
        }
        else{
            Controller.mLabel.setText("再见");
            Controller.flag=true;
        }
    }
}
java运行

1.一级化简： 简单内部类

/*1*/class MyEventHandler implements EventHandler<ActionEvent>{
		@Override
		public void handle(ActionEvent e){
			//事件的逻辑......
		}
	}
/*2*/Button myButton=new Button("我的按钮");
/*3*/myButton.setOnAction(new MyEventHandler);
java运行
二级化简： 匿名内部类
简记：直接 new 一个（事件处理器）接口

/*1*/Button myButton=new Button("我的按钮");
/*2*/myButton.setOnAction(new EventHandler<ActionEvent>{
		@Override
		public void handle(ActionEvent e){
			//事件的逻辑......
		}
	});
java运行
三级化简：推荐！！！ lambda表达式
简记：只需要参数
关于为什么只需要参数，你可以这样想：类只用一次就扔了，接口的类型ActionEvent也是和注册函数setOnAction的Action对应，函数名也没什么用（因为不需要在其他地方调用）。所以，真正有用的就是函数的参数

/*1*/Button myButton=new Button("我的按钮");
/*2*/myButton.setOnAction(e->{
			//事件的逻辑......
		}
	});
java运行
(二) InputEvent类事件：
我们用的是它的子类：MouseEvent —— KeyEvent
==>注意：所以的场景Scene和节点Note都可以注册鼠标键盘事件！<==
1.鼠标事件MouseEvent：
注册函数：
setOnMouse +
______________Pressed(e->{…}) ：按下
______________Released(e->{…}) ：松开
______________Clicked(e->{…}) ：按下并松开（点击）

______________Entered(e->{…}) ：进入
______________Exited(e->{…}) ：离开

______________Moved(e->{…}) ：移动
______________Dragged(e->{…}) ：拖动

类内函数：
get +
______Button() :返回MouseButton（被单击的鼠标按键）
______ClickCount() :返回int(单击次数)

______X() ：返回double（当前控件中的X）
______Y()

______SceneX() ：返回double。场景的X
___________Y() ：
______ScreenX() ：返回double。屏幕X
___________ Y() :
is +
______AltDown() ：是否按下Alt键
______ControlDown() ： Ctrl键
______ShiftDown() ：Shift键

2.键盘KeyEvent：
注册函数：
setOnKey +
____________Pressed(e->{…}) ：按下
____________Released(e->{…}) ：松开
____________Typed(e->{…}) ：敲击

类内函数：
get +
______Character() :返回String（按键字符，试试就懂）
______Code() :返回KeyCode(按键编码)
______Text() ：返回String（按键编码说明）

KeyCode	说明字符串
F1~F12	从F1到F12的函数键
A~Z	同上
CONTROL	Ctrl键
…全大写…	…此次省略（你都懂的）…
is +
______AltDown() ：是否按下Alt键
______ControlDown() ： Ctrl键
______ShiftDown() ：Shift键

示例：

Scene myScene =new Scene();
myScene.setOnMousePressed(e->{
	//事件逻辑
});
javascript运行
Text myText =new Text();
myText.setOnMousePressed(e->{
	//事件逻辑
});
```
### JavaFX 常见事件类型<br>
<img width="1183" height="858" alt="image" src="https://github.com/user-attachments/assets/a8b1d58f-e9cb-4ad4-8365-6f9b3ceb9b37" />
<img width="1071" height="384" alt="image" src="https://github.com/user-attachments/assets/5ce524c5-849b-4a20-b9d0-7c382f62b1ef" /> 
<br>
### ActionEvents（动作事件）
在JavaFX中，ActionEvent 是一个表示用户触发动作的事件，比如点击按钮、选择菜单项或按下键盘上的特定键。<br>
#### 案例演示:按钮点击事件处理<br>

```
package com.binge.javafxdemo.event;

import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Alert;
import javafx.scene.control.Button;
import javafx.scene.control.ButtonType;
import javafx.scene.layout.StackPane;
import javafx.stage.Stage;

import java.util.Optional;

public class ActionEventExample extends Application {

    @Override
    public void start(Stage primaryStage) {
        Button btn = new Button();
        btn.setText("点击按钮");

        // 设置动作事件处理器
        btn.setOnAction(event -> {
            System.out.println("按钮被点击");
            Alert alert = new Alert(Alert.AlertType.INFORMATION);
            alert.setTitle("点击按钮事件");
            alert.setHeaderText(null);
            alert.setContentText("按钮被点击了！");
            alert.show();
        });

        StackPane root = new StackPane();
        root.getChildren().add(btn);

        Scene scene = new Scene(root, 300, 250);

        primaryStage.setTitle("按钮点击事件示例");
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
```
### FocusEvent（焦点事件）
在JavaFX中，FocusEvent 是一个表示组件焦点变化的事件。焦点事件用于通知应用程序用户界面(UI)中的组件何时获得或失去焦点。JavaFX提供了几种焦点事件类型，它们都继承自 FocusEvent 类。

FocusEvent 的事件类型:

FOCUS_GAINED: 当一个组件获得焦点时触发。
FOCUS_LOST: 当一个组件失去焦点时触发。
FOCUSED: 当一个组件获得焦点时触发，无论焦点是进入还是离开。
UNFOCUSED: 当一个组件失去焦点时触发，无论焦点是进入还是离开。
#### 案例演示,获取和失去焦点事件
```
package com.binge.javafxdemo.event;

import javafx.application.Application;
import javafx.geometry.Pos;
import javafx.scene.Scene;
import javafx.scene.control.TextField;
import javafx.scene.layout.HBox;
import javafx.scene.layout.StackPane;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

public class FocusEventExample extends Application {

    @Override
    public void start(Stage primaryStage) {
        TextField textField = new TextField();
        textField.setMaxWidth(100);
        TextField textField2 = new TextField();
        textField2.setMaxWidth(100);
        textField.setPromptText("输入姓名");
        textField2.setPromptText("输入邮箱");

        // 设置焦点事件处理器
        textField.focusedProperty().addListener((obs, wasFocused, isNowFocused) -> {
            if (isNowFocused) {
                System.out.println("获取焦点");
            } else {
                System.out.println("失去焦点");
            }
        });

        VBox root = new VBox();
        root.getChildren().add(textField);
        root.getChildren().add(textField2);

        Scene scene = new Scene(root, 300, 250);

        primaryStage.setTitle("焦点事件示例");
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
```
### SelectionEvent（选择事件）
在JavaFX中，SelectionEvent 是一个抽象类，它表示一个选择操作的事件，一般用于列表或表格以响应用户的选择操作。

#### 案例演示1,ListView 选择事件
```
package com.binge.javafxdemo.event;

import javafx.application.Application;
import javafx.collections.FXCollections;
import javafx.collections.ObservableList;
import javafx.scene.Scene;
import javafx.scene.control.ListView;
import javafx.scene.layout.StackPane;
import javafx.stage.Stage;

public class ListViewSelectionEventExample extends Application {

    @Override
    public void start(Stage primaryStage) {
        ObservableList<String> items = FXCollections.observableArrayList(
                "Item 1", "Item 2", "Item 3", "Item 4"
        );

        ListView<String> listView = new ListView<>(items);
        listView.setPrefSize(200, 200);

        // 设置选择事件处理器
        listView.getSelectionModel().selectedItemProperty().addListener((obs, oldSelection, newSelection) -> {
            if (newSelection != null) {
                System.out.println("Selected item: " + newSelection);
            }
        });

        StackPane root = new StackPane();
        root.getChildren().add(listView);

        Scene scene = new Scene(root, 300, 250);

        primaryStage.setTitle("Selection Event Example");
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}

```
#### 案例演示2,TableView 选择事件
```
package com.binge.javafxdemo.event;

import javafx.application.Application;
import javafx.collections.FXCollections;
import javafx.collections.ObservableList;
import javafx.scene.Scene;
import javafx.scene.control.TableColumn;
import javafx.scene.control.TableView;
import javafx.scene.control.cell.PropertyValueFactory;
import javafx.scene.layout.StackPane;
import javafx.stage.Stage;

public class TableViewSelectionExample extends Application {
    public static class Fruit {
        private int id;
        private String name;
        private String color;

        public Fruit(int id, String name, String color) {
            this.id = id;
            this.name = name;
            this.color = color;
        }

        public int getId() {
            return id;
        }

        public String getName() {
            return name;
        }

        public String getColor() {
            return color;
        }

        @Override
        public String toString() {
            return "Fruit{" +
                    "id=" + id +
                    ", name='" + name + '\'' +
                    ", color='" + color + '\'' +
                    '}';
        }
    }

    @Override
    public void start(Stage primaryStage) {
        ObservableList<Fruit> items = FXCollections.observableArrayList(
                new Fruit(1,"苹果", "红色"),
                new Fruit(2,"香蕉", "黄色"),
                new Fruit(3,"草莓", "红色"),
                new Fruit(4,"樱桃", "棕色")
        );

        TableView<Fruit> tableView = new TableView<>();
        TableColumn<Fruit, Integer> idColumn = new TableColumn<>("编号");
        idColumn.setCellValueFactory(new PropertyValueFactory<>("id"));
        TableColumn<Fruit, String> nameColumn = new TableColumn<>("名称");
        nameColumn.setCellValueFactory(new PropertyValueFactory<>("name"));
        TableColumn<Fruit, String> colorColumn = new TableColumn<>("颜色");
        colorColumn.setCellValueFactory(new PropertyValueFactory<>("color"));

        tableView.getColumns().addAll(idColumn, nameColumn, colorColumn);
        tableView.setItems(items);

        // 设置选择事件处理器
        tableView.getSelectionModel().selectedItemProperty().addListener((obs, oldItem, newItem) -> {
            if (newItem != null) {
                System.out.println("Selected fruit: " + newItem);
            }
        });

        StackPane root = new StackPane();
        root.getChildren().add(tableView);

        Scene scene = new Scene(root, 400, 300);

        primaryStage.setTitle("TableView Selection Event Example");
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
```
## 我们用一个案例来学习,jfx_event_demo<br>
<img width="519" height="526" alt="image" src="https://github.com/user-attachments/assets/1b02128f-208d-4f67-92da-f1c55c31059b" /> <br>
#### 这里我们实现一个简单的功能,就是点击按钮标签会往上移动,代码如下(HelloApplication.java)<br>
```
package com.example.jfx_event_demo;
import javafx.application.Application;
import javafx.collections.FXCollections;
import javafx.collections.ObservableList;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.control.TableColumn;
import javafx.scene.control.TableView;
import javafx.scene.control.cell.PropertyValueFactory;
import javafx.scene.layout.AnchorPane;
import javafx.scene.layout.StackPane;
import javafx.stage.Stage;

public class HelloApplication extends Application {

    @Override
    public void start(Stage stage) {
        AnchorPane root = new AnchorPane();
        Scene scene = new Scene(root, 500, 500);
        Label lbl = new Label("Hello JFX!!!");
        lbl.setLayoutX(200);
        lbl.setLayoutY(200);
        Button btn = new Button("向上移动");
        btn.setLayoutX(200);
        btn.setLayoutY(250);
        //点击按钮,标签往上移动
        btn.setOnAction(e->{
            lbl.setLayoutY(lbl.getLayoutY()-10);
        });
        root.getChildren().addAll(lbl,btn);
        stage.setTitle("JFX Event Example");
        stage.setScene(scene);
        stage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
```
#### 效果<br>
<img width="619" height="657" alt="image" src="https://github.com/user-attachments/assets/66c73d72-a7b5-4d00-acdc-93d8cf945887" />
<img width="628" height="636" alt="image" src="https://github.com/user-attachments/assets/ef1649d1-e46b-4d77-b6c6-5f720df8b866" />
<img width="636" height="661" alt="image" src="https://github.com/user-attachments/assets/acfbb8cd-1f7f-4242-8bfa-8ef44d452866" /> <br>
### 然后我们还可以设置键盘事件,这里可以个stage设置这个键盘弹起事件,代码如下<br>
```
package com.example.jfx_event_demo;
import javafx.application.Application;
import javafx.collections.FXCollections;
import javafx.collections.ObservableList;
import javafx.event.EventHandler;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.control.TableColumn;
import javafx.scene.control.TableView;
import javafx.scene.control.cell.PropertyValueFactory;
import javafx.scene.input.KeyCode;
import javafx.scene.input.KeyEvent;
import javafx.scene.layout.AnchorPane;
import javafx.scene.layout.StackPane;
import javafx.stage.Stage;

public class HelloApplication extends Application {

    @Override
    public void start(Stage stage) {
        AnchorPane root = new AnchorPane();
        Scene scene = new Scene(root, 500, 500);
        Label lbl = new Label("Hello JFX!!!");
        lbl.setLayoutX(200);
        lbl.setLayoutY(200);
        Button btn = new Button("向上移动");
        btn.setLayoutX(200);
        btn.setLayoutY(250);
        //点击按钮,标签往上移动
        btn.setOnAction(e->{
            lbl.setLayoutY(lbl.getLayoutY()-10);
        });
        root.getChildren().addAll(lbl,btn);
        //给场景设置键盘弹起事件,用↑,↓,←,→方向键控制标签的移动
        scene.setOnKeyReleased(e->{
            KeyCode code = e.getCode();
            if(code.equals(KeyCode.DOWN)){
                lbl.setLayoutY(lbl.getLayoutY()+10);
            } else if(code.equals(KeyCode.LEFT)){
                lbl.setLayoutX(lbl.getLayoutX()-10);
            } else if(code.equals(KeyCode.RIGHT)){
                lbl.setLayoutX(lbl.getLayoutX()+10);
            } else if(code.equals(KeyCode.UP)){
                lbl.setLayoutY(lbl.getLayoutY()-10);
            }
        });
        stage.setTitle("JFX Event Example");
        stage.setScene(scene);
        stage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
```
#### 效果,上下左右按键分别控制标签的上下左右移动
## 然后我们可以来实现一些拖拽事件,我们实现的功能是在场景中放一个文本框,当然用户把一个文本文件拖拽进入文本框,就会显示文件的内容,需要两个事件,onDragOver和onDragDropped<br>
### 这里我用了2种写法来封装读取文件内容的函数代码如下<br>
```
package com.example.jfx_event_demo;
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.control.TextArea;
import javafx.scene.control.TextField;
import javafx.scene.input.Dragboard;
import javafx.scene.input.KeyCode;
import javafx.scene.input.TransferMode;
import javafx.scene.layout.AnchorPane;
import javafx.stage.Stage;

import java.io.BufferedReader;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;

public class HelloApplicationDrag extends Application {
    private String getFileContent(String path) throws IOException {
        String line = "";
        String content = "";
        BufferedReader reader = new BufferedReader(new FileReader(path));
        while ((line = reader.readLine()) != null)
        {
            System.out.println(line);
            content += line + "\n";

        }
        return content;
    }
    private void setFileContent(String path,TextArea area) throws IOException {
        String line = "";
        BufferedReader reader = new BufferedReader(new FileReader(path));
        while ((line = reader.readLine()) != null)
        {
            System.out.println(line);
            area.appendText(line+"\n");
        }
    }
    @Override
    public void start(Stage stage) {
        AnchorPane root = new AnchorPane();
        Scene scene = new Scene(root, 500, 500);
        TextArea area = new TextArea();
        area.setMaxWidth(450);
        area.setMaxHeight(350);
        area.setLayoutX(20);
        area.setLayoutY(20);
        //响应拖拽事件,响应处理2个事件onDragOver和onDragDropped
        area.setOnDragOver(e->{
            e.acceptTransferModes(TransferMode.ANY);
        });

        area.setOnDragDropped(e->{
            //获取拖板
            Dragboard board = e.getDragboard();
            //看看里面有没有文件
            if(board.hasFiles()){
                //如果拖板里面有文件,获取文件的绝对路径
                String path = board.getFiles().get(0).getAbsolutePath();
                try {
//                    setFileContent(path,area); //方法1
                     area.setText(getFileContent(path)); //方法2
                } catch (IOException ex) {
                    ex.printStackTrace();
                }
            }
        });
        root.getChildren().add(area);
        stage.setTitle("JFX Drag Event Example");
        stage.setScene(scene);
        stage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
```
### 运行程序,把一个文本文件拖拽进入文本域,就会显示文本的内容<br>






