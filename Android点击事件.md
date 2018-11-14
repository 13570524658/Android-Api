# Android点击事件

# 匿名内部类

```
public class MainActivity extends AppCompatActivity {

 private Button btn;
 
       public void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_main);
        
            btn = findViewById(R.id.btn);
            
            btn.setOnClickListener(new OnClickListener() {
            
            @Override
            public void onClick(View v) {
                // TODO Auto-generated method stub
                 Toast.makeText(MainActivity.this,"匿名内部类,点击事件",Toast.LENGTH_LONG).show();
              }
           });
     }     
}

```
# 定义内部类，实现OnClickListener接口

```
public class MainActivity extends AppCompatActivity {

 private Button btn;
 
       public void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_main);
        
            btn = findViewById(R.id.btn);
            
            btn.setOnClickListener(new MyListener());
      }
      
    class MyListener implements View.OnClickListener{

        @Override
        public void onClick(View v) {
            // TODO Auto-generated method stub
               Toast.makeText(MainActivity.this,"定义内部类，实现OnClickListene接口,点击事件",Toast.LENGTH_LONG).show();
        }
    }
}
```

# 定义的构造方法

```
public class MainActivity extends AppCompatActivity {

 private Button btn;
 
       public void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_main);
        
            btn = findViewById(R.id.btn);
            
            myListener();
     }
     
      
     //定义构造方法
        private void myListener() {
        // TODO Auto-generated method stub
        bt.setOnClickListener(new OnClickListener() {
            
            @Override
            public void onClick(View v) {
                // TODO Auto-generated method stub
       Toast.makeText(MainActivity.this,"定义构造方法",点击事件",Toast.LENGTH_LONG).show();
            }
        });
    }
}
```
# 用Activity实现OnClickListener接口

```
public class MainActivity extends AppCompatActivity implements View.OnClickListener{

 private Button btn;
 private Button btn1;
 
       public void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_main);
        
            btn = findViewById(R.id.btn);
            btn = findviewByid(R.id.btn1);
            
            btn.setOnClickListener(this);
            btn1.setOnClickListener(this);
     }
     
      
    @Override
    public void onClick(View v) {
        int id=v.getid();
        switch(id){
        
        case R.id.btn:
                Toast.makeText(MainActivity.this,"btn点击事件",Toast.LENGTH_LONG).show();
        break;
        
        case R.id.btn1:
                Toast.makeText(MainActivity.this,"btn1点击事件",Toast.LENGTH_LONG).show();
        break;
        
        default:
                Toast.makeText(MainActivity.this,"默认点击事件",Toast.LENGTH_LONG).show();
        break;
        }
        
       // Toast.makeText(MainActivity.this,"用Activity实现OnClickListener接口,点击事件",Toast.LENGTH_LONG).show();
    }
}
```

# 指定Button的onClick的属性

　　先在layout文件中指定onClick属性，然后到Activity中实现这个onButtonClick方法
  
  ```
      <Button
        android:id="@+id/btn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="click"
        android:text="btn点击事件" />
        
        <Button
        android:id="@+id/btn1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="click"
        android:text="btn1点击事件" />
  ```
  
  ```
  public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    public void click(View v) {
        
        int id=v.getid();
        
        switch(id){
        
        case R.id.btn:
                Toast.makeText(MainActivity.this,"btn点击事件",Toast.LENGTH_LONG).show();
        break;
        
        case R.id.btn1:
                Toast.makeText(MainActivity.this,"btn1点击事件",Toast.LENGTH_LONG).show();
        break;
        
        default:
                Toast.makeText(MainActivity.this,"默认点击事件",Toast.LENGTH_LONG).show();
        break;
        }
        // TODO Auto-generated method stub
        //Toast.makeText(MainActivity.this,"指定onClick属性方式,点击事件",Toast.LENGTH_LONG).show();
    }
}
  ```


