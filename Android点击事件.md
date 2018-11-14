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
 
       public void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_main);
        
            btn = findViewById(R.id.btn);
            
            btn.setOnClickListener(this);
     }
     
      
    @Override
    public void onClick(View v) {
        Toast.makeText(MainActivity.this,"用Activity实现OnClickListener接口,点击事件",Toast.LENGTH_LONG).show();
    }
}
```






