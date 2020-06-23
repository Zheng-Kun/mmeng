# 网页设计大作业
> 网页仿照QQ音乐Web端门户网页制作

## 一、项目文件结构
### 页面文件（除入口页面，其余页面均存放在`pages`目录中）
- `pages/paly-list-detail.html` 为[歌单详情页(点击预览)](https://zheng-kun.github.io/mmeng/pages/play-list-detail.html )
- `pages/paly-list-list.html` 为[歌单列表页(点击预览)](https://zheng-kun.github.io/mmeng/pages/play-list-list.html )(点击首页也会跳转到这个页面)
- `pages/my-music.html` 为 [我的音乐(点击预览)](https://zheng-kun.github.io/mmeng/pages/my-music.html )
- `pages/ticket.html` 为 [票务商城页(点击预览)](https://zheng-kun.github.io/mmeng/pages/ticket.html)
- `pages/download.html` 为[客户端下载页(点击预览)](https://zheng-kun.github.io/mmeng/pages/download.html )

### 样式文件均放在 `styles` 目录中
- `common.css` 中为公共样式
- `header.css` 中为顶部导航栏样式
- `footer.css` 中为底部页脚样式
- 其余样式文件中存放对应同名页面的内容部分样式

### 图片文件
- `images` 目录中存放页面用到的各种图标文件
- `images/inLove` 目录中存放歌单列表页用到的专辑封面图
- `images/download` 目录中存放下载页用到的素材图片
- `images/ticket` 目录中存放票务页面用到的素材图片

## 二、布局设计
### 1. 公共部分
> 由于页头页脚，浮窗，还有一些按钮。链接的样式几乎在每个页面都会用到，因此把他们放在单独的文件中，方便引用
#### 整个页面的居中
 - 除客户端下载页比较特殊外，其他页面内的内容宽度均为`1200px`, 通过设置固定`1200px`的固定宽度，与外边距 `margin: 0 auto;` 使其居中展示
#### 头部导航
 - 第一行导航与第二行导航，将每个导航链接按钮通过`display: inline-block;`设置为行内块元素， 使其排列再一行中
 - 导航栏中的搜索框和用户头像，通过设置向右浮动，使其展示在父容器的最右侧`float: right;`
#### 页脚部分
 - "下载QQ音乐客户端"、"特色产品"、"合作链接" 三块均通过设置为行内块级元素`display: inline-block;`，使其展示在一行，
 - "下载QQ音乐客户端"和"特色产品"中的图标使用背景图片实现.
   1. `background-image:url()`设置背景图片
   2. 因为一个背景图片中有很多小图标，我们通过`background-position: [x]px [y]px;`确定每个图标的位置（在鼠标hover时，设置新的`background-position`）以设置新的图片作为背景，达到hover时图标变色的效果，（整个项目中几乎所有图标，包括下载页中的文字图片，都是用这种方式设置，之后不再赘述）
#### 下载浮窗
 - 通过 `position: fixed; top: 164px;right: 40px;` 使其固定在窗口的固定位置
### 2. 歌单列表页
 - 标题的居中和歌单分类导航的居中均通过`text-align: center;`实现
 - 列表中的卡片设置为行内块级，并设置固定宽度，边距，使四个卡片的宽度和边距加起来等于1200px
 - 封面通过背景图片实现，在背景图片的div里面放一个半透明背景的div作为蒙层（display设置为none影藏蒙层，当鼠标hover时display设置为block展示蒙层），蒙层中的小心心设置为绝对定位，top和left都设置为50%，然后将心心图标的上边距和左边距设置为负的图标宽高的一半，实现图标的居中。
### 3. 我的音乐页面
 - 导航列表的导航还是通过设置"inline-block"行内块级元素实现
 - 头像和用户名的居中均通过`text-align: center`实现
 - 歌曲列表通过无序列表实现，每个li都是一行，对li中的各个元素设置宽度，使其加起来等于列表的宽度
 - "歌曲"列稍微复杂一些，当鼠标hover在改行的时候，将操作按钮的display设置为block实现hover时展示操作按钮，当鼠标hover时同时也将歌曲名容器的最大宽度变小，给后面的操作按钮流出空间
 - 通过`:nth-child(2n-1)`这个伪类选择器选择到奇数行，并改变奇数行的背景颜色
 - 通过`white-space: nowrap; overflow: hidden;text-overflow: ellipsis;` 这三个样式，当容器内的文本溢出容器时自动展示省略号
### 4. 歌单详情页
 - "歌单详情页"中歌曲列表的实现与"我的音乐"页面的列表相同
 - 歌单信息（包括歌单封面与封面右侧的信息和按钮部分），对封面设置了向左浮动，以使封面和其右侧的内容并列，在封面和信息的父容器做了清除浮动，以防止父容器的高度塌陷，比封面小
 - 四个操作按钮通过div实现，使用"inline-block"使其并列展示，四个按钮的父元素设置了绝对定位使按钮展示在父容器的底部
### 5. 客户端下载页
 - 顶部banner设置`position: fixed`使其固定在窗口顶部，不随页面滚动
 - 对html和body元素均设置宽高100%， 使其大小等于页面窗口的宽高，然后对boy中的5个class="full-screen"的元素设置宽高100%，达到每个容器的大小都正好等于浏览器窗口的大小的效果
 - 每屏的内容基本都通过决定定位去设置内容的位置
 - 在出现手机屏幕素材的时候，手机框和手机屏幕的内容为两个图片素材，我们先通过绝对定位使这两个素材展示在对应的位置，然后通过`transform: rotate(7.5deg)`旋转屏幕内容，使其正好嵌在边框素材内

