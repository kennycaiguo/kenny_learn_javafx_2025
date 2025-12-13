# 这一节我们来学习在Application里面操作Controller
## 新建一个项目,起名:jfx-app_access_controller<br>
<img width="587" height="518" alt="image" src="https://github.com/user-attachments/assets/ee57caab-9d47-413a-ac06-6ba7fa9f6527" /> <br>
## idea里面有一个Scene Builder,但是不太好用,我们需要下载一个外部的: https://download2.gluonhq.com/scenebuilder/17.0.0/install/windows/SceneBuilder-17.0.0.msi<br>
## 安装好后,需要在idea里面配置使用外部的Scene Builder<br>
<img width="1231" height="904" alt="image" src="https://github.com/user-attachments/assets/0d8d8553-4dff-4489-af36-4ea473e76a7e" /> <br>
## 点击apply按钮后,点击ok按钮退出<br>
<img width="1226" height="904" alt="image" src="https://github.com/user-attachments/assets/4f7b51f5-cf04-4486-a15e-aa282e94662f" /> <br>
## 然后在hello-view.fxml上面点击右键->Open in SceneBuilder,就可以使用外部的SceneBuilder来编辑了<br>
<img width="625" height="1012" alt="image" src="https://github.com/user-attachments/assets/25c8ba94-c12a-4467-805e-6f0f2fffe8c2" /><br>
<img width="1920" height="1072" alt="image" src="https://github.com/user-attachments/assets/52f5387d-e047-44c8-845d-b2afe43ba16a" /> <br>
## 我们把按钮删除,然后添加一个圆,调整圆心的位置使得它在场景的中间<br>
<img width="1179" height="840" alt="image" src="https://github.com/user-attachments/assets/a502b922-e0e1-40ba-8aa8-ca7cf045f219" /> <br>
## 然后我们保存文件,运行程序,效果是这样子的<br>
<img width="751" height="529" alt="image" src="https://github.com/user-attachments/assets/004faa20-d5d4-4920-96d3-79e142760558" /> <br>
### 注意:此时如果我们关闭窗口的大小,圆的位置是不会改变的.<br>
<img width="1100" height="760" alt="image" src="https://github.com/user-attachments/assets/4652a3c3-b820-4dac-a85c-1b9ff5740012" /> <br>
## 此时我们就只能够在Application里面获取Controller来实现功能,我们需要先给圆添加一个id:circle,然后修改一下HelloController.java的代码,注意在控制器里面定义的变量的名称编写和圆的id一模一样<br>
```
package com.kenny.jfxapp_access_controller;

import javafx.fxml.FXML;
import javafx.scene.control.Label;
import javafx.scene.shape.Circle;

public class HelloController {
  @FXML
  private Circle circle;

  public Circle getCircle() {
    return circle;
  }

  public void setCircle(Circle circle) {
    this.circle = circle;
  }
}
```
## 运行程序,效果如下:
<img width="765" height="547" alt="image" src="https://github.com/user-attachments/assets/17d008c2-a558-4692-a40e-f94d8fc22f47" /><br>
### 修改窗口的宽度,效果如下:<br>
<img width="475" height="576" alt="image" src="https://github.com/user-attachments/assets/b61084eb-c59e-4b4b-862c-0c0b5fe7d6de" /><br>

### 修改窗口的高度度,效果如下:<br>
<img width="466" height="411" alt="image" src="https://github.com/user-attachments/assets/cdd83ec0-a159-48c7-b0ca-74f53ce25442" /><br>

## 其实我们也可以把绑定属性的代码放到HelloController中,添加一个circleBind(Scene scene)方法,一样可以达到这个效果:<br>
<img width="1271" height="678" alt="image" src="https://github.com/user-attachments/assets/f64a462c-2593-4f54-8a8b-42e0c54fde86" /><br>
### 然后修改运行Application的代码<br>
<img width="1200" height="686" alt="image" src="https://github.com/user-attachments/assets/5e658206-1acd-4b76-a808-ba0a1fbec849" /><br>
#### 效果是一样的<br>
<img width="881" height="651" alt="image" src="https://github.com/user-attachments/assets/5863a18c-8dda-46e3-8515-443854f7e94d" /><br>
<img width="543" height="733" alt="image" src="https://github.com/user-attachments/assets/b9810bc9-240f-43b3-ad78-f0347b009fdb" /><br>
<img width="529" height="411" alt="image" src="https://github.com/user-attachments/assets/c16d3473-4421-450a-a907-62052c91c9d8" /><br>











