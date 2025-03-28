# 智能图像裁剪器-

智能图像裁剪器/
├── main.py # 程序入口
├── styles/ # 样式资源
│ └── material.qss # Material Design样式表
├── core/ # 核心业务模块
│ ├── image_model.py # 大图数据模型
│ ├── CropConfigManager.py #裁剪参数管理
│ └── file_manager.py #文件操作控制
├── ui/ # 界面模块
│ ├── main_window.py # 主窗口入口
│ ├── widgets.py # 可视化组件
│ ├── CropAdjust_Pane.py # 裁剪调整界面
│ └── ThumbnailListView.py #缩略图列表组件
├── controller/ # 控制层
│ └── main_controller.py # 主控制器
│   ├── utils/
│ ├── thread_pool.py # 线程池管理
│ └── image_utils.py # OpenCV工具函数
└── resources/ # 图形资源
└── icons/ # SVG图标库

根据以上框架，帮我用python和pyside6用MVC模式写一个程序，将这个程序的界面与业务逻辑分开，需求如下：

1. 程序界面设计
   - 用户界面应包含一个主窗口，主窗口中包含一个工具栏和一个主内容区域。
   - 工具栏应包含至少三个按钮，用于执行不同的操作。
   - 主内容区域应包含一个文本编辑器，用于显示和编辑文本。

2. 业务逻辑
   - 程序应能够读取和写入文本文件。
   - 程序应能够执行基本的文本编辑操作，如复制、粘贴、删除等。
   - 程序应能够通过工具栏按钮触发这些文本编辑操作。

3. MVC模式
   - 模型（Model）：负责数据的存储和操作。在这个例子中，模型将负责读取和写入文本文件。
   - 视图（View）：负责界面的展示。在这个例子中，视图将负责显示文本编辑器的界面。
   - 控制器（Controller）：负责处理用户输入并更新模型和视图。在这个例子中，控制器将负责处理工具栏按钮的点击事件并更新模型和视图。

4. 其他要求
   - 程序应有良好的错误处理和用户反馈机制。
   - 程序界面应美观、易用。
   - 程序应能够处理大型文本文件。
1、我需要在程序中打开资源管理器，选择文件夹中的一个或多个小图拼接的大图导入到程序的大图预览界面；
2、在程序的大图预览界面选中一个或多个需要裁剪的大图，鼠标点击预裁剪按钮，程序执行批量预裁剪动作；
3、程序执行批量预裁剪动作，程序将多个不同尺寸的小图拼接的长图片通过程序自动识别，将识别到的所有小图都预裁剪后预览显示到小图缩略图平铺预览窗口待选择；
4、在待选择区域里选择需要的小图并能够单独重新调整每个小图的裁剪边缘；
5、将需要裁剪的小图都调整和选择后，点击裁剪按钮，程序将裁剪出来的小图保存在当前裁剪长图片名称命名的文件夹下，以当前裁剪长图片名称+自动编号的命名保存；
6、我需要这个程序能够有可视化界面操作，主界面为水平布局，左侧面板为图片导入图片、移除图片按钮、预裁剪按钮与导入大图预览图界面；中间为预裁剪后小图缩略图平铺预览窗口，小图的缩略图大小可通过预裁剪界面工具栏调整，工具栏上有小图全选、反选按钮，默认全选，鼠标在缩略图上时在缩略图侧边显示调整边界按钮，点击调整按钮弹出该小图的边界调整界面，通过鼠标拖动图片上的选框来调整小图边界，小图的边界调整界面右侧包含一个工具栏，工具栏内有图片边界选框的多个预设比例和自动边界选项；主界面右侧上部分为自动识别边界的参数调整界面，下部分为小图元数据信息，主界面的下方为信息栏，显示自动识别进度和报错信息等内容；
7、在ui/widgets.py中集成组件‌：
IconButton，可缩放图像标签，裁剪区域绘制器，错误吐司，参数编辑器小部件，元数据显示，增强的列表项小部件，预设纵横比选择器，处理覆盖。
#在ui/widgets.py中集成组件‌：
SmartSpinBox(QSpinBox), IconButton(QPushButton), ScalableImageLabel(QLabel), SeparatorWidget(QWidget), EnhancedListWidgetItem(QListWidgetItem), CropAreaPainter(QWidget), ErrorToast(QLabel), ProcessingOverlay(QWidget), QProgressIndicator(QWidget)
8、ui/ThumbnailListView.py中集成组件‌：ThumbnailListView(QListWidget)#缩略图列表组件
9、在core/CropConfigManager.py中集成组件‌：CropConfigManager
10、在utils/thread_pool.py中集成组件：ImageProcessingThread(QObject)
11、在utils/context_menu.py中集成组件‌：ContextMenuBuilder
12、在utils/plugin_loader.py中集成组件‌：PluginLoader(QObject)
