# 我们真的不能在其他线程更新UI嘛？

``````
public class MainActivity extends AppCompatActivity {
    private TextView textView;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        textView = (TextView) findViewById(R.id.tv_main);
        new Thread(new Runnable() {
            @Override
            public void run() {
                textView.setText("更新完成");
            }
        }).start();
    }

}
``````

咦，当我们运行上面这行代码的时候，UI界面居然被成功更新，而且没有抛出异常。
当我们在上面代码中让线程休眠几秒钟，我们的线程又抛出了异常。这到底是为什么呢？


# 深入源码

当我们在非UI线程更新后，会打印一段

``````
android.view.ViewRootImpl$CalledFromWrongThreadException: Only the original thread that created a view hierarchy can touch its views.
``````
也就是说，我们的ViewRootImpl（一个隐藏类）中抛出了异常。
根据一层层的深入，我们可以发现源码中有一个checkThread()的方法，
这个方法就是用来判断我们的线程是不是在主线程。

``````
void checkThread() {  
       if (mThread != Thread.currentThread()) {  
           throw new CalledFromWrongThreadException(  
                   "Only the original thread that created a view hierarchy can touch its views.");  
       }  
   } 
``````

原来，我们的安卓就是通过这样一个方法来局限我们的。
咦，那么问题来了，为什么我们上面那种情况不会报错呢？
这就说明，当我们在onCreate的时候我们去调用这个更新UI界面操作的时候，
源码还没有去检测我们的线程。
这就和我们activity的生命周期有关系了，
其实是因为我们的ViewRootImpl是在onResume中去初始化的。
