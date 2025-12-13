# 我们来学习Controller
## 新一个项目: jfx_controller_demo<br>
<img width="522" height="503" alt="image" src="https://github.com/user-attachments/assets/fe371e9a-3b83-40c9-a75d-8f2b1447bddf" /><br>
## 打开hello-view.fxml,把VBox改为AnchorPane<br>
<img width="1390" height="674" alt="image" src="https://github.com/user-attachments/assets/4e7fd1ce-ac45-4c1d-ab61-696faac88fcc" /><br>
## 然后我们打开Scene Builder,调整一下按钮和标签的位置(注意:这里因为没有给标签设置文本,所以他默认不可见,我们可以在左边找到它)<br>
<img width="1398" height="663" alt="image" src="https://github.com/user-attachments/assets/4e5efaa6-f68f-4bab-b454-15c5c7f965c8" /><br>
### 运行程序,此时是没有然后问题的<br>
<img width="744" height="530" alt="image" src="https://github.com/user-attachments/assets/e8b8629a-2ab3-4662-9ec2-7d89b5e8736f" /><br>
## Controller里面有一个initialize方法我们正这里写一些代码来测试一下(可以把一些比较复杂的,无法在fxml里面写的代码写在这里),这个方法会自动执行<br>
<img width="1380" height="686" alt="image" src="https://github.com/user-attachments/assets/54888ad3-90dc-4bde-b51a-54e24d7c62b2" /><br>
### 运行程序,效果如下:<br>
<img width="1420" height="838" alt="image" src="https://github.com/user-attachments/assets/2594e010-7e2e-42e1-a605-64b1af5cc693" /> <br>
## 具体这个initialize方法怎么用,我们可以把按钮和标签删除,然后添加一个TableView控件,
<img width="1316" height="691" alt="image" src="https://github.com/user-attachments/assets/04a3d163-a4fe-4379-9784-2466b2c1e2c7" /> <br>
### 注意需要给TableView和他的Column分别设置id<br>
<img width="1042" height="313" alt="image" src="https://github.com/user-attachments/assets/072fb519-d570-49e2-b957-bc4e8a28a5a0" /><br>
## 我们需要在应用程序一启动,就给TabelView添加数据,此时就只能够使用initialize方法里面的代码来完成功能了,在这之前,我们需要新建一个Person类<br>
<img width="1389" height="640" alt="image" src="https://github.com/user-attachments/assets/24263e31-ad86-4a4e-b472-7fab7cabc34c" /><br>
## 然后我们在initialize方法里面给TableView弹出数据,代码有点复杂<br>
```
package com.kenny.jfx_controller_demo;

import javafx.collections.FXCollections;
import javafx.collections.ObservableList;
import javafx.fxml.FXML;
import javafx.scene.control.Label;
import javafx.scene.control.TableColumn;
import javafx.scene.control.TableView;
import javafx.scene.control.cell.PropertyValueFactory;

public class HelloController {
    @FXML
    private TableView<Person> tbView;

    @FXML
    private TableColumn<Person,String> name;

    @FXML
    private TableColumn<Person,Integer> age;

    public void initialize(){
        ObservableList<Person> cellData = FXCollections.observableArrayList();
        name.setCellValueFactory(new PropertyValueFactory<Person,String>("name"));
        age.setCellValueFactory(new PropertyValueFactory<Person,Integer>("age"));
        cellData.add(new Person("Jackline",18));
        cellData.add(new Person("Mary",19));
        cellData.add(new Person("Tracy",17));
        cellData.add(new Person("Mark",18));
        cellData.add(new Person("Lulu",18));
        tbView.setItems(cellData);
    }
}
```
### 运行程序,效果如下:<br>
<img width="751" height="542" alt="image" src="https://github.com/user-attachments/assets/8eb53b6a-b6b2-459a-87a6-fcfd7b402160" /><br>






