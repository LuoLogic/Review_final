# Android

## 1-3章

1. Android包括`操作系统`，`中间件`，`核心应用`
2. 平台架构：`Applications`,`Application Framework`,`Libraries`,`Android Runtime`,`Linux Kernel`:安全性，内存管理，进程管理

3. SDK常用命令
   * `adb`:与模拟器实例或安装设备通信;adb devices
   * `android`:［√］创建、删除和查看Android虚拟设备（AVD）。［√］创建和更新Android项目。［√］更新Android SDK，内容包括新平台、插件和文档
   * `emulator`:使用emulator命令可以控制模拟器，
   * `mksdcard`:mksdcard命令可以快速创建FAT32磁盘镜像

4. 对话框AlertDialog
5. Toast

6. 控制UI界面方式
    1. 使用xml布局文件(res/layout):setContentView(R.layout.main)
    2. 在代码中控制UI界面 FrameLayout  frameLayout=new FrameLayout(this); setContentView(frameLayout)
    3. xml和Java代码混合控制UI界面
    4. 开发自定义的view：所有的UI界面都是由`View`和`ViewGroup`及其子类构成

7. 线性布局
   1. 线性布局是将放入其中的组件按照垂直或水平方向来布局，也就是控制放入其中的组件横向或纵向排列。在线性布局中，每一行（针对垂直排列）或每一列（针对水平排列）中只能放一个组件，并且Android的线性布局不会换行，当组件排列到窗体的边缘后，后面的组件将不会被显示出来。
   2. 排列方式：`android:orientation`:可选值：`horizontal`和`vertival`
   3. 对齐方式：`android:gravity`：top、bottom、left、right、center_vertical、fill_vertical、center_horizontal、fill_horizontal、center、fill、clip_vertical和clip_horizontal
   4. 设置组件基本宽度:`android:layout_width`:`fill_parent`:和父容器相同,`match_parent`:一样,`wrap_parent`:宽度恰好包裹内容
   5. 设置组件基本高度:`android:layout_height`
   6. 指定id:`android:id`
   7. 设置背景：`android:background`
   8. `<LinearLayout>`

8. 表格布局
   1. `<TableLayout>`:每个`<TableRow>`表示一行
   2. 表格布局与常见的表格类似，以行、列的形式来管理放入其中的UI组件。表格布局使用`<TableLayout>`标记定义，在表格布局中，可以添加多个`<TableRow>`标记，每个`<TableRow>`标记占用一行。由于`<TableRow>`标记也是容器，所以还可在该标记中添加其他组件，每添加一个组件，表格就会增加一列。在表格布局中，列可以被隐藏，也可以被设置为伸展的，从而填充可利用的屏幕空间，还可以设置为强制收缩，直到表格匹配屏幕大小
   3. 本质上还是线性布局
   4. tablerow的layout_width属性，默认为`fill_parent`，设置成其他值也不会生效

9. 网格布局
   1. GridLayout
   2. 可以自己设置布局中组件的排列方式
   3. 可以自定义网格布局有多少行,多少列
   4. 可以直接设置组件位于某行某列
   5. 可以设置组件横跨几行或者几列
   6. `android:layout_rowCount`设置行
   7. `android:layout_columnCount`设置列
   8. `GridLayout:LayoutParams`:内部类控制子组件的布局

10. 帧布局
    1. `<FrameLayout>`
    2. 帧布局容器为每个加入的组件创建一个空白的区域（称为一帧），这些帧都会根据gravity属性执行自动对齐
    3. 默认情况下，帧布局是从FrameLayout的左上角（0,0）坐标点开始布局
    4. 如果一个FrameLayout里有多个子元素，多个组件层叠排序，后面的组件覆盖前面的组件。

11. 相对布局
    1. `<RelativeLayout>`
    2. `android:gravity` 用于设置布局管理器中各子组件的对齐方式
    3. `android:ignoreGravity` 用于指定哪个组件不受gravity属性的影响
    4. android:layout_below="@+id/textView1"
    5. 相对布局是指按照组件之间的相对位置来进行布局，如某个组件在另一个组件的左边、右边、上方或下方等。
    6. 相对布局的特点是可以让控件之间互相确定关系，这样可以保证在屏幕的局部范围内几个控件之间的关系不受外部影响
    7. `android:layout_above`,alignBottom,alignParentTop

12. 表格布局网格布局区别

13. `TextView`,

14. `EditText`,`android:password`,用android:inputType属性来限制

15. `<Button>`,指定圆角矩形的四个圆角的半径-`<corners>`,`<ImageButton>`:显示图片:`android:src`

16. `android:enabled`设置按钮可用

17. 设置view的点击事件监听
    1. 在布局文件中为控件设置onClick属性指定点击方法；
    2. 创建一个内部类实现OnClickListener接口并重写onClick()方法，之后需要为控件设置setOnClickListener(Listener listener)；
    3. 主类中实现OnclickListener接口，然后重写onClick()方法；
    4. 创建匿名内部类，即在为控件设置监听时直接创建一个OnClickListener实例，不为该实例指定名

18. 单选框`RadioButton`，radioGroup.getCheckedRadioButtonId()

19. 复选框`CheckBox`:android:checked,状态开关按钮`ToggleButton`,`Switch`

20. `ImageView`图像视图，SetImageBitmap(Bitmap bm)
21. AdapterView组件
    1. 抽象类,继承ViewGroup
    2. `setAdapter(Adapter)`

22. 显示列表的常用两种方法
    1. 直接使用ListView
    2. 让Activity集成ListActivity

23. ListViewxml属性
    1. `android:entries`

24. Adapter常用实现类
    1. ArrayAdapter
    2. SimpleAdapter
    3. BaseAdapter

25. Spinner-列表

26. SimpleAdapter构造函数
    1. public SimpleAdapter(Context context, List data, int resource,String[] from, int[] to);
    2. context：运行的上下文环境
    3. data：以List中放置Map对象来表示数据
    4. resource：数据索要绑定到的布局资源，是一个R.layout表示的布局资源，可以是系统提供的，也可以是自定义的.
    5. from：数据map中的key
    6. to：布局资源中要绑定数据的组件id,取R.id值，与from中的数据形成对应关

    ```java
    ListView listView=(ListView)findViewById(R.id.listView);

        //获取数据集合

        List<Person> personList=new ArrayList<>();
        Person person1=new Person("张峰","80");
        Person person2=new Person("周慧","90");
        Person person3=new Person("刘娜娜","100");
        personList.add(person1);
        personList.add(person2);
        personList.add(person3);

        List<HashMap<String,Object>> data=new ArrayList<>();
        for (Person person : personList) {
            HashMap<String,Object> item=new HashMap<>();
            item.put("name",person.getName());
            item.put("score",person.getScore());
            data.add(item);
        }


        SimpleAdapter adapter = new SimpleAdapter(this, data, R.layout.item, new String[]{"name","score"},new int[]{R.id.name,R.id.score});

        listView.setAdapter(adapter);
    ```

27. 设置监听按钮

    ```java
    Button login=(Button)findViewById(R.id.login); //通过ID获取布局文件中添加的按钮
    login.setOnClickListener(new OnClickListener() { //为按钮添加单击事件监听器
    @Override
    public void onClick(View v) {
    //编写要执行的动作代码
    }
    })；

    ```

    ```java
    ListView listView = (ListView)findViewById(R.id.lstCountry);
    String[] countries = {"China","English","Japainese"};
    List list =new ArrayList();
    for (int i=0; i < countries.length;i++) {
        Map map = new HashMap();
        map.put("countryname", countries[i]);
        map.put("index", i+1);
        list.add(map);
        }
        //map中的keyString[] from={"countryname","index"};
        //view中的组件int[] to ={android.R.id.text1,android.R.id.text2};
    SimpleAdapter adapter = new SimpleAdapter(this,list,android.R.layout.simple_
    list_item_2,from,to);
    listView.setAdapter(adapter);
    ```

## 第五章

1. View内部常用接口
   1. `View.OnClickListener`

2. 基于回调事件的处理
   1. 事件源与事件监听器是统一
   2. Java无法为某个对象动态地添加方法，只能继承GUI组件类，并重写该类的事件处理方法
   3. 几乎所有基于回调的事件处理方法都有一个boolean类型的返回值、该值用于标识该处理方式是否能完全处理该事件。`True`：表明该方法已完全处理该方法，该事件不会传播出去。`False`：表明该处理方法并未完全处理该事件，该事件会传播出去
   4. onKeyDown

3. Configuration类：专门用于描述手机设备上的配置信息，这些配置信息包括用户特定的配置项，也包括系统的动态设备配置
4. Activity栈(Stack)
5. 四个状态
   1. `活动`:当前的Activity，位于Activity栈顶，用户可见，并且可以获得焦点
   2. `暂停`：失去焦点的Activity，仍然可见，但是在内存低的情况下，不能被系统killed（杀死）
   3. `停止`：该Activity被其他Activity所覆盖，不可见，但是它仍然保存所有的状态和信息。当内存低的情况下，它将要被系统killed（杀死）
   4. `销毁`：该Activity结束，或Activity所在的Dalvik进程结束

6. 生命周期和回调方法
   1. `onCreate()`方法：在创建Activity时被回调。该方法是最常见的方法，在Eclipse中创建Android项目时，会自动创建一个Activity，在该Activity中，默认重写了onCreate(BundlesavedInstanceState)方法，用于对该Activity执行初始化,并使用`setContentView()`加载指定的布局文件

        ```java
        @Override
        public void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.main)
            }
        ```

   2. `onStart()`方法：启动Activity时被回调，也就是当一个Activity变为显示时被回调。
   3. `onRestart()`方法：重新启动Activity时被回调，该方法总是在onStart()方法以后执行,对用户即将可见时调用
   4. `onPause()`方法：暂停Activity时被回调。该方法需要被非常快速地执行，因为直到该方法执行完毕后，下一个Activity才能被恢复。在该方法中，通常用于持久保存数据。例如，当我们正在玩游戏时，突然来了一个电话，这时就可以在该方法中将游戏状态持久保存起来。
   5. `onResume()`方法：当Activity由暂停状态恢复为活动状态时调用。调用该方法后，该Activity位于Activity栈的栈顶。该方法总是在onPause()方法以后执行。将要与用户交互时调用
   6. `onStop()`方法：停止Activity时被回调。
   7. `onDestroy()`方法：销毁Activity时被回调
   8. 完整生命周期：`onCreate()`$\rightarrow$`onDestory()`
   9. 可见生命周期：`onStart()`$\rightarrow$`onStop()`，多次调用
   10. 前台生命周期：`onResume()`$\rightarrow$`onPause()`

7. 配置Activity：具体的配置方法是在`AndroidManifest.xml`中的\<application>\</application>标记中添加\<activity>\</activity>标记。\<activity>标记的基本格式如下：

    ``` xml
    <activity
    android:icon="@drawable/图标文件名"
    android:name=".MainActivity"
    android:label="说明性文字"
    android:theme="要应用的主题"
    …
    >
    …
    </activity>
    ```

8. 启动和关闭Activity
    1. `startActivity(Intent intent)`，`startActivity(Intent intent,int resquestCode)`

        ```java
        public void startActivity (Intent intent)
        ```

    2. `finish()`,`finish(int resquestCode)`

9. 系统内存不足：`onSaveInstanceState()`,临时保存数据

10. 多个Activity
    1. 传递数据传递数据通过**Intent**实现，可以将数据保存在**Bundle**对象中，通过`putExtras()`方法将携带的数据保存到Intent中

        ```java
        Intent intent=new Intent(MainActivity.this,RegisterActivity.class);
        Bundle bundle=new Bundle();
        //创建并实例化一个Bundle对象
        bundle.putCharSequence("user", user);
        //保存用户名
        bundle.putCharSequence("pwd", pwd);
        //保存密码
        bundle.putCharSequence("email", email);
        //保存E-mail地址
        intent.putExtras(bundle);
        //将Bundle对象添加到Intent对象中
        startActivity(intent); //启动新的Activity
        ```

    2. 返回上一步`startActivityForResult(intent,code)`方法来启动另一个Activity。

        ```java
        Button button=(Button)findViewById(R.id.back); //获取“返回上一步”按钮
        button.setOnClickListener(new OnClickListener() {
            @Override
            public void onClick(View v) {
                setResult(0x717,intent); //设置返回的结果码，并返回调用该Activity的Activity
                finish(); //关闭当前Activity
            }
        });
        ```

        ```java
        @Override
        protected void onActivityResult(int requestCode, int resultCode, Intent data) {
            super.onActivityResult(requestCode, resultCode, data);
            if(requestCode==CODE && resultCode==CODE){
                ((EditText)findViewById(R.id.pwd)).setText(""); //清空“密码”编辑框
                ((EditText)findViewById(R.id.repwd)).setText(""); //清空“确认密码”编辑框
            }
        }
        ```

    3. Fragment:重写onCreateView()

11. 四大组件:**Activity,Service,BroadCastReciver,ContentProvider**,

12. R.string,R.array,R.color
13. 无法通过R资源访问的保存在`assets`文件夹下
14. `res/values`存放字符串，整数，颜色，数组
15. `res/mipmap`存放Launcher图标文件
16. `res/drawable`存放位图文件
17. `res/color`存放不同状态下颜色列表的xml文件
18. Activity启动模式：`Standard`，`singleTop`,`singleTask`,`singleInstance`

## 第六章

1. Activity、Service和Broadcast Receiver这3种核心组件都需要使用Intent来进行激活

2. android系统提供了不同的Intent发送机制进行激活
   * Intent对象可以传递给`Context.startActivity()`或`Activity.startActivityForResult()`方法来启动Activity或者让已经存在的Activity去做其他任务。Intent对象也可以作为`Activity.setResult()`方法的参数，将信息返回给调用startActivityForResult()方法的Activity。
   * Intent对象可以传递给`Context.startService()`方法来初始化Service或者发送新指令到正在运行的Service。类似的，Intent对象可以传递`Context.bindService()`方法来建立调用组件和目标Service之间的链接。它可以有选择地初始化没有运行的服务。
   * Intent对象可以传递给`Context.sendBroadcast()`、`Context.sendOrderedBroadcast()`或`Context.sendStickyBroadcast()`等广播方法，使其被发送给所有感兴趣的BroadcastReceiver。

3. 组件名setComponent()设置，getComponent()读取

4. Intent打电话
   1. Activity

        ```java
            public class DialActivity extends Activity {
            @Override
                protected void onCreate(Bundle savedInstanceState) {
                    super.onCreate(savedInstanceState);
                    setContentView(R.layout.main); //设置页面布局
                    EditText numberTV = (EditText) findViewById(R.id.editText); //通过id值获得编辑框对象
                    final String number = numberTV.getText().toString(); //获得用户输入的电话号码
                    Button dial = (Button) findViewById(R.id.button); //通过id值获得按钮对象
                    dial.setOnClickListener(new View.OnClickListener() {
                        public void onClick(View v) {
                        Intent intent = new Intent(); /创建Intent对象
                        intent.setAction(Intent.ACTION_CALL); //为Intent设置动作
                        intent.setData(Uri.parse("tel:" + number)); //为Intent设置数据
                        startActivity(intent); //将Intent传递给Activity
                    }
                });
            }
        }

        ```

   2. AndroidManifest.xml

        ```xml
            <uses-permission android:name="android.permission.CALL_PHONE" />
        ```

5. Intent发短信
   1. activity

        ```java
            btnStart.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent=new Intent();
                intent.setAction(Intent.ACTION_SENDTO);
                intent.setData(Uri.parse("smsto:10086"));
                startActivity(intent);
            }
        });
        ```

   2. xml

        ```xml
            <uses-permission android:name="android.permission.SEND_SMS"></uses-permission>
            <uses-permission android:name="android.permission.CALL_PHONE"></uses-permission>
        ```

6. 显式Intent：Intent intent = new Intent(this,Activity.class)

7. 隐式Intent
   1. 系统会根据隐式意图中设置的动作（action）、类别（category）、数据（Uri和数据类型）找到最合适的组件

   2. `<action>`标签指明了当前Activity可以响应的动作为"com.xxx"
   3. `<category>`标签则包含了一些类别信息，只有当`<action>`和`<category>`中的内容同时匹配时，Activity才会被开启

   4. xml

        ```xml
            <category android:name="android.intent.category.DEFAULT"/>
        ```

8. action动作
   1. `ACTION_DIAL`使用提供的数字打电话
   2. `ACTION_CALL`使用提供的数字给某人打电话
   3. `ACITON_SEND`给某人发消息，接受者未指定
   4. `ACITON_SENDTO`给某人发消息，接受者指定

## 第七章

1. 事件处理机制
   1. 基于监听：`OnClickListener()`
   2. 基于回调:`OnKeyDown()`

2. 屏蔽后退键

    ```java
        @Overridepublic boolean onKeyDown(int keyCode, KeyEvent event) {
            if (keyCode == KeyEvent.KEYCODE_BACK) {
                return true; //屏蔽后退键
                }
                return super.onKeyDown(keyCode, event)
            }
    ```

3. 触摸事件
   1. `OnClickListener`和`OnLongClickListener`,短时间和长时间单击
   2. `onTouch`触摸事件

## 第八章

1. Drawable位于`res/drawable`
2. 菜单资源文件通常放置在res\menu目录
3. res下menu目录下
    1. 根元素：menu
    2. 子元素：item
    3. 动态加载方式
       1. 在activity中重写onCreateOptionsMenu()
       2. onOptionsItemSelected

4. 选项菜单:重写`onCreateOptionsMenu()`,创建用于解析菜单资源文件的`MenuInflater`对象

5. 在xml中使用资源

    ```xml
        <EditText
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textColor="@color/red"
        android:text="@string/hello" />
    ```

6. Java中访问资源：`R.drawable.<file_name>`

## 第九章

1. Paint类：代表画笔 例子绘制矩形

    ```java
        @Overrideprotected void onDraw(Canvas canvas) {
            super.onDraw(canvas);
            Paint paint = new Paint();
            paint.setColor(Color.RED);
            paint.setShadowLayer(2, 3, 3, Color.GRAY);
            Rect r = new Rect(40, 40, 200, 100);
            canvas.drawRect(r, paint)
    ```

2. Bitmap类：代表位图
   1. compress方法：压缩对象为指定格式并保存到指定的文件输出流
   2. createBitmap(int width, int height, Bitmap.Config config)

3. `BitmapFactory()`:该类为一个工具类，用于从不同的数据源来解析、创建Bitmap对象
   1. decodeFlie(String pathname):指定路径解析创建bitmap对象

        ```java
            String path="/sdcard/pictures/bccd/img01.jpg";
            Bitmap bm=BitmapFactory.decodeFile(path);
        ```

4. `drawCircle`:画○,`drawRect`：画矩形

5. `drawBitmap`

6. 添加特效
   1. 常用类android.graphics.Matrix
   2. 旋转图像：`setRotate()`,postRotate(),preRotate()
   3. 缩放图像：`setSacle()`
   4. 倾斜图像：`setSkew()`
   5. 代码

    ```java
        Paint paint = new Paint();
        paint.setAntiAlias(true);
        Bitmap bt_rabiit = BitmapFactory.decodeResource(this.getResources(), R.drawable.rabit);
        //绘制原图
        canvas.drawBitmap(bt_rabiit, 0, 0, paint);
        Matrix m = new Matrix();
        m.setSkew(0.5f, 0);
        canvas.drawBitmap(bt_rabiit, m, paint);
    ```

7. 动画
   1. 逐帧动画:`android:onshot`用于设置是否循环播放，Java代码中创建AnimationDrawable对象，调用addFrame()向动画中添加帧

        ```xml
            <animation-list xmlns:android="http://schemas.android.com/apk/res/android"
            android:oneshot="true|false"
            >
            <item android:drawable="@drawable/图片资源名1" android:duration="integer"
            />
            … <!-- 省略了部分<item></item>标记 -->
            <item android:drawable="@drawable/图片资源名n" android:duration="integer"
            />
            </animation-list>
        ```

   2. 补间动画

        ```xml
            <set xmlns:android="http://schemas.android.com/apk/res/android">
            <!-- 动画开始透明度 fromAlpha-->
            <!-- 动画结束透明度 toAlpha-->
            <!-- 动画持续时间 duration -->
            <alpha android:fromAlpha="0"
                   android:toAlpha="1"
                   android:duration="2000"/>
            </set>
        ```

   3. 缩放动画:定义一个以图片的中心为轴心点，将图片放大2倍的、持续时间为2秒钟的动画，可以使用下面的代码：

        ```xml
            <scale android:fromXScale="1"
            android:fromYScale="1"
            android:toXScale="2.0"
            android:toYScale="2.0"
            android:pivotX="50%"
            android:pivotY="50%"
            android:duration="2000">
        ```

   4. 平移动画：，定义一个让图片从（0,0）点到（300,300）点、持续时间为2秒钟的动画，可以使用下面的代码：

        ```xml
            <translate
            android:fromXDelta="0"
            android:toXDelta="300"
            android:fromYDelta="0"
            android:toYDelta="300"
            android:duration="2000">
            </translate>
        ```

## 第十一章

1. `ContentResolver`实现对`ContentProvider`

    ```java
        ContentResolver cr=getContentResolver();
    ```

2. 通常，每个类型的ContentProvider**仅有一个单独的实例**。但是该实例能与位于不同应用程序和进程的多个ContentResolver类对象通信。不同进程之间的通信由**ContentProvider**类和**ContentResolver**类处理。

3. 数据模型
   * Content Provider使用基于**数据库模型的简单表格**来提供其中的数据
   * 每条记录包含一个数值型的**\_ID**字段，用于在表格中唯一标识该记录
   * 查询返回一个`Cursor`对象

4. URI用法
   1. 每个Content Provider提供公共的URI（使用Uri类包装）来唯一标识其数据集。管理多个数据集（多个表格）的Content Provider为每个数据集提供了单独的URI。所有为provider提供的URI都以“`content://`”作为前缀，“content://”模式表示数据由Content Provider来管理
   2. 例如**content://com.mingrisoft.employeeprovider/dba/001**
      1. com....provider:URI的authority部分，用于标识该Content Provider。对于第三方应用，该部分应该是完整的类名（使用小写形式）来保证唯一性。在\<provider>元素的authorities属性中声明authority
      2. dba:：Content Provider的路径部分，用于决定哪类数据被请求
      3. 001:被请求的特定记录的ID值

5. 自定义ContentProvider
   1. 开发人员定义ContentProvider类的子类，以便使用ContentResolver和Cursor类来共享数据。原则上，这意味着需要实现ContentProvider类定义的6个抽象方法，其语法格式如下：

        ```java
            //用于初始化provider
            public boolean onCreate()
            //返回数据给调用者
            public Cursor query(Uri uri, String[] projection, String selection, String[] selectionArgs, String sortOrder)
            //插入新数据到Content Provider
            public Uri insert(Uri uri, ContentValues values)
            //更新Content Provider中已经存在的数据
            public int update(Uri uri, ContentValues values, String selection, String[] selectionArgs)
            //从Content Provider中删除
            public int delete(Uri uri, String selection, String[] selectionArgs)
            //返回Content Provider数据的MIME
            public String getType(Uri uri)
        ```

   2. 声明contentProvider

        ```xml
            <provider
            android:authorities="com.example.sqllitecontentprovider.PersonContentProvider"
            android:name="com.example.sqllitecontentprovider.PersonContentProvider"
            android:exported="true"
            ></provider>
        ```

## 第十二章

1. 在Android中，提供了两种创建线程的方法：一种是通过`Thread`类的构造方法创建线程对象，并重写`run()`方法实现；另一种是通过实现`Runnable`接口实现

    ```java
    Thread thread=new Thread(new Runnable(){
    //重写run()方法
        @Override
        public void run() {
        //要执行的操作
        }
    });
    ```

2. 开启线程**thread.start()**
3. 线程休眠**thread.sleep(long time)**
4. 中断线程**thread.interrupt()**

5. Handler机制主要包括四个关键对象，分别是：`Message`、`Handler`、`MessageQueue`、`Looper`

6. Looper:初始化：prepare(),获取和处理消息：loop()，quit:退出

7. Handler
   1. 每个Hanlder都关联了一个线程。
   2. 将message或Runnable应用`post()`或`sendMessage()`方法发送到MessageQueue中
   3. 在发送时可以指定延迟对象、发送时间、以及要携带的`Bundle`数据
   4. 当MessageQueue循环到该Message时，调用相应的Handler对象的`HandleMessage()`方法对其进行处理
   5. `handleMessage(Messagemsg)`：处理消息的方法。通常重写该方法来处理消息，在发送消息时，该方法会自动回调
   6. `post(Runnable r)`：立即发送Runnable对象，该Runnable对象最后将被封装成Message对象
   7. `sendMessage(Message msg)` 立即发送消息

## 第十三章

1. service服务类型
   1. `Started`
   2. `Bound`

2. service 重要方法：
   1. `onStartCommand()`
   2. `iBinder onBound()`子类必须要实现的方法，返回一个Ibinder对象，应用程序可通过该对象与Service组件进行通讯
   3. `onCreate()`:在该Service第一次被创建后将立即回调该方法
   4. `onDestroy()`在Service被关闭之前将回调该

3. 声明

    ```xml
        <service
        android:name=".MyService"
        android:enabled="true"
        android:exported="true"></service>
    ```

4. 生命周期
   1. `startService()`：服务会长期的在后台运行，并且服务的状态与开启者的状态没有关系
   2. `bindService()`：服务与开启者的状态有关，当调用者销毁了，服务也会被销毁

5. 在进行本地服务通信时，可以使用Service类提供的IBinder onBind(Intent intent)方法，该方法返回的IBinder对象会作为参数传递给ServiceConnection类中onServiceConnected(ComponentName name,IBinder service)方法，这样访问者就可以通过IBinder对象与Service进行通信

## 第十四章

1. 使用`HttpURLConnection`访问网络

    ```Java
        URL url = new URL("http://www.mingribook.com/");
        HttpURLConnection urlConnection = (HttpURLConnection) url.openConnection();
    ```

2. HttpClient
   1. 创建HttpClient对象
   2. 指定访问网络的方式，创建一个HttpPost对象或者HttpGet对象
   3. 如果需要发送请求参数，可调用HttpGet、HttpPost的setParams()方法
   4. 调用HttpClient对象的execute()方法访问网络
   5. 调用HttpResponse.getEntity()方法获取HttpEntity对象

3. okhttp 详情见老师的例子
4. WebView 是一个用来显示 Web 网页的控件，继承自 AbsoluteLayout。它就是一个微型浏览器，包含一个浏览器该有的基本功能，例如：滚动、缩放、前进、后退下一页、搜索、执行 Js等功能

5. 广播接收者`BroadcastReceiver`

6. 广播接收者创建与启动
   1. 定义一个继承BroadcastReceiver的类，并实现onReceive(Context context, Intent intent)方法

        ```java
            public class MyBroadcastReceiver extends BroadcastReceiver {
                @Override
                public void onReceive(Context context, Intent intent) {
                }
            }
        ```

7. 广播接收者注册
   1. `常驻型`广播和`非常驻`型广播

8. 常驻型广播注册,静态注册

    ```xml
        <receiver android:name="com.sample.broad.MyBroadcastReceiver">
        <intent-filter android:priority="20">
        <action android:name="android.provider.Telephony.SMS_RECEIVED"/>
        </intent-filter>
        </receive>
    ```

9. 非常驻广播注册，依赖注册广播的生命周期
   1. 动态注册：registerReceiver(receiver, intentFilte)
   2. unregisterReceiver(receiver)

        ```java
        MyBroadCastReceiver receiver = new MyBroadCastReceiver();
        //实例化过滤器并设置要过滤的广播
        String action = "android.provider.Telephony.SMS_RECEIVED";
        IntentFilter intentFilter = new IntentFilter(action);
        //注册广播
        registerReceiver(receiver, intentFilter);
        ```

10. 常用action
    1. `ACTION_TIME_CHANGED` 系统时间被改变
    2. `ACTION_DATE_CHANGED` 系统日期被改变
    3. `ACTION_BETTERY_CHANGED` 电池电量改变
    4. `ACTION_BETTERY_LOW` 电池电量低

11. 广播类型
    1. 标准`sendBroadcast(intent)`
    2. 有序`sendOrderedBroadcast(intent,null)`
12. 自定义广播
    1. 先定义一个广播接收器（继承`BroadcastReceiver`）
    2. 需要实现`onReceive()`方法
    3. 在`AndroidManifest.xml`注册
    4. 使用`receiver`元素来定义
    5. 使用`intent-filter`来定义其antion。当为有序广播时，使用`android:priority`来定义优先级别

## 编程题代码

1. 网上下载图片显示

    ```java

    public class MainActivity extends AppCompatActivity {

        ImageView imageView;
        Button btnClient;
        //图片地址
        String path = "http://img61.ddimg.cn/digital/product/83/4/1901178304_ii_cover.jpg";
        String path1 = "http://10.17.52.135:8080/Ajax/access";
        Handler handler = new Handler() {
            @Override
            public void handleMessage(Message msg) {
                //处理网络响应的状态
                if (msg.what == 100) {
                    imageView.setImageBitmap((Bitmap) msg.obj);
                } else {
                    Toast.makeText(MainActivity.this
                                ,msg.obj.toString()
                                ,Toast.LENGTH_LONG).show();
                }
            }
        };
        @Override
        protected void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_main);

            btnClient = findViewById(R.id.btnClient);
            imageView =findViewById(R.id.imageView);

            btnClient.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View v) {
                    new Thread(new Runnable() {
                        @Override
                        public void run() {
                            //创建HttpClient对象
                            HttpClient client = new DefaultHttpClient();
                            //创建HttpGet或者HttpPost对象
                            HttpGet httpGet = new HttpGet(path);
                            //httpGet.setURI();
                            try {
                                //调用httpClient的execute方法访问网络
                                HttpResponse response = client.execute(httpGet);
                                //通过HttpResponse对象的getEntity()获取实体对象
                                int  code = response.getStatusLine().getStatusCode();
                                if (code==200) {
                                    //获取响应对象的实体内容
                                    HttpEntity  entity = response.getEntity();
                                    //获取图片的二进制流
                                    InputStream in = entity.getContent();
                                    //通过BitmapFactory的方法，创建新的位图对象
                                    Bitmap bitmap = BitmapFactory.decodeStream(in);
                                    Message msg = new Message();
                                    msg.what = 100;
                                    msg.obj= bitmap;
                                    //发送消息
                                    handler.sendMessage(msg);
                                } else {
                                    //访问异常时的处理
                                    Message msg = new Message();
                                    msg.what = 101;
                                    msg.obj = "web访问出错:" + code;
                                    //发送消息
                                    handler.sendMessage(msg);
                                }

                            } catch (Exception ex) {
                                //发生异常时的处理
                                Message msg = new Message();
                                msg.what = 110;
                                msg.obj = "Exception: " + ex.getMessage()  ;
                                //发送消息
                                handler.sendMessage(msg);
                                ex.printStackTrace();

                            }

                        }
                    }).start();

                    }
                });
            }
        }

    ```
