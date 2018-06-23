## Intent是什么？
    
    Intent的中文意思是“意图，目的”的意思，可以理解为不同目标组件之间通信的“媒介”或者“信使”。
    
## Intent由什么组成？

    Intent在由以下几个部分组成：
    
    动作（action），数据（data），分类（Category），类型（Type），组件（Component），和扩展信息（Extra）。

## 什么是目标组件？

    目标组件一般要通过Intent来声明自己的条件，一般通过组件中的<intent-filter>元素来过滤。

## Intent通过什么寻找目标组件？ 

    Intent在寻找目标组件的时候有两种方法：第一，通过组件名称直接指定；第二，通过Intent Filter过滤指定。

## 组件名称   组件方法

    Activity  startActivity()  startActivityForResult()    
    
    Service  startService()  bindService()    
    
    Broadcasts  sendBroadcast()  sendOrderedBroadcast()  sendStickyBroadcast()  
    
## Activity 之间 Intent 传值  养成习惯使用Bundle封装数据

#### 数据封装

        //第一个Activity发送数据
        Intent intent = new Intent(OneActivity.this，TwoActivity);  
        Bundle bundle = new Bundle();  
        bundle.putInt("int", 1);  
        bundle.putString("String", 1);  
        intent.putExtras(bundle);  
        startActivity(intent)
#### 数据拆包
        //第二个Activity接收数据
        Bundle bundle = getIntent().getExtras();  
        int ints = bundle.getInt("int");  
        int Strings = bundle.getString("String");  




