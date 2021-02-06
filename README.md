# vue-5ch
![GitHub](https://img.shields.io/github/license/iconteral/UJShealthChecker)
## 这是个啥？
  
这是一个依赖[Vue Cli](https://cli.vuejs.org/zh/)的本地的仿[5ch讨论板](https://www2.5ch.net/5ch.html)式留言板，用于对发出的文本进行一定程度的排版，便于有需要的人使用。  
~~摸鱼产物，真的想不到为什么都2021了日本人还是在用这种老掉牙式ui的论坛~~

## 我该怎么安装？

1. 从GitHub……或者其他地方把**Releases里的最新版本的**文件包（文件名：vue-5ch-ver0.0.2.zip）整个下载下来。  
**不要点那个绿色的下载按钮，除非你知道这堆源码还缺什么运行环境。**
2. 安装[Node.js](http://nodejs.cn/)，一路next就行。
3. 运行里面的vue-5ch.bat文件，会自动弹出一个cmd窗口  
4. 如果一会cmd显示了  
``` DONE Compiled succesfully in XXms```  
就可以在浏览器里访问窗口里显示的**Local：http://localhost:XXXX/** 进行使用。~~如果显示的是别的的话我也不知道怎么办啊~~
5. 安装 **ＭＳ Ｐゴシック**， **MS PGothic**， **IPAMonaPGothic**， **方正兰亭黑**， **sans-serif** 一共五个字体。
6. Enjoy！

7. 关闭的话关闭那个cmd窗口就好。
## 推荐使用环境

Win10，Chrome浏览器。  
别的环境我~~很不负责地~~没测试，如果有问题请联系我  
  
*如果你是为了对AA进行截图，这里安利截图工具[ShareX](https://getsharex.com/)的滚动截图功能*

## 装完之后怎么用？

温馨提示： 
``` 
按下键盘的 **Home** 键能快速到达页面顶部，按下 **End** 键能快速到达页面底部  
```

页面的最底端有几个文本框和按钮，分别用于：  
- 标题框：随意填写。默认为```thread-default```。  
在按下右侧的**更改标题**按钮后，标题（那个红色的）将会被更改为框中的文字。同时下方的读取/储存名会被更新。  
不会被自动清空。
- 名称、时间、ID：随意填写。  
名称、时间、ID若不填写则会被设置为 ```（　´∀）・∀）,,ﾟД) 2020/12/26(土) 12:34:56 r0SeYa5A1```。  
不会被自动清空。
- 输入文本：随意填写。**不支持HTML，CSS，JS等文本格式。输入的文字=发出的文字。**  
按下右侧的**发送**按钮后将会**清空这个文本框**并向楼内增加一楼。  
会同时向该楼内增加名称、时间、ID框内写入的内容。  
在没有内容的时候按下按钮不会增加楼层。
- 要删除的楼层数：随意填写。  
按下右侧的**删除**按钮后会**清空这个文本框**并删除指定楼层数（1楼开始）的内容。  
当楼层数不存在时按下按钮不会进行删除。
- 读取/储存名：帖子的保存**索引名**，使用localStorage的相关方法储存/读取，视为**浏览器缓存**。  
当按下右侧的**导出帖子**按钮时，会将本地的对应```这个文本框中的内容```的索引名的帖子改成```当前页面中的内容```。  
当按下右侧的**导入帖子**按钮时，会将```当前页面中的内容```改成本地的对应```这个文本框中的内容```的索引名的帖子。  
**不是自动保存/读取功能。** 不会被自动清空。

  
~~我readme写的好乱啊~~

# Vue Cli运行指令

开发者向。

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
### 许可

![WTFPL](http://www.wtfpl.net/wp-content/uploads/2012/12/wtfpl-badge-1.png)

© 2020 WTFPL – Do What the Fuck You Want to Public License.
