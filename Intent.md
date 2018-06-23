## Intent是什么？
    
    Intent的中文意思是“意图，目的”的意思，可以理解为不同目标组件之间通信的“媒介”或者“信使”。
    
## Intent由什么组成？

    Intent在由以下几个部分组成：
    
    动作（action），数据（data），分类（Category），类型（Type），组件（Component），和扩展信息（Extra）。

    
## Activity 之间 Intent 传值  
       养成习惯使用Bundle封装数据
       Intent在界面之间的传输，自身是可以携带数据传输的，但是其携带数据传输的大小，是有一定限制的！
       所以传输比较大的数据时候，可以通过Bundle去传输！ 

## putExtras 和 putExtra 的区别

        putExtras必须使用Bundle

#### 数据封装

        //第一个Activity发送数据
        Intent intent = new Intent(OneActivity.this，TwoActivity);  
        Bundle bundle = new Bundle();  
        //发送int数据类型
        bundle.putInt("intType", 1);
        //发送String数据类型
        bundle.putString("StringType", 1);
        //发送list<object>数据类型 
        DataBean    dataBean=new DataBean();
        ArrayList  items = new ArrayList<OrderDetail>();
        //设置假数据
        OrderDetail orderDetail=new OrderDetail();
        orderDetail.setAge(1);
        orderDetail.setName("2");
        items.add(orderDetail);
        dataBean.setData(items);
        bundle.putSerializable("dataBean",dataBean);
        
        intent.putExtras(bundle);  
        startActivity(intent)
#### 数据拆包
        //第二个Activity接收数据
        Bundle bundle = getIntent().getExtras();
        //获取int类型数据
        int ints = bundle.getInt("intType");  
        //获取String类型数据
        int Strings = bundle.getString("StringType");
        //获取List<Object>数据类型
        List<OrderDetail> mData=new ArrayList<>();
        DataBean dataBean= (DataBean) bundle.getSerializable("dataBean");
        List<OrderDetail> data=dataBean.getData();
        mData.addAll(data);

#### Object实体类 必须实现Serializable

    public class DataBean implements Serializable {
        private List<OrderDetail> data;

        public List<OrderDetail> getData() {
            return data;
        }

        public void setData(List<OrderDetail> data) {
            this.data = data;
        }
    }
    
#### List实体类 必须实现Serializable

    public class OrderDetail implements Serializable{
        private String name;
        private int age;

        public String getName() {
            return name;
        }

        public void setName(String name) {
            this.name = name;
        }

        public int getAge() {
            return age;
        }

        public void setAge(int age) {
            this.age = age;
        }
    }


