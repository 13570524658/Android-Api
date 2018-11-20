# 更新UI的方法

``````
在安卓中，我们的主线程是不可以进行一些耗时的操作的。
因为当主线程超过五秒无响应后，我们的程序就会ANR。

``````

# runOnUiThread（）

``````
private void methodName() {
        new Thread(new Runnable() {
            @Override
            public void run() {
                //耗时操作
                try {
                    Thread.sleep(3000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                runOnUiThread(new Runnable() {
                    @Override
                    public void run() {
                      //更新界面
                        textView.setText("更新完成");
                    }
                });
            }
        }).start();
    }  
    
``````
# handler.post()

``````
private void methodName() {
        new Thread(new Runnable() {
            @Override
            public void run() {
                //耗时操作
                try {
                    Thread.sleep(3000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                handler.post(new Runnable() {
                    @Override
                    public void run() {
                        textView.setText("更新完成");
                    }
                });
            }
        }).start();
    }
    
``````

# View.post()
``````
 private void method3() {
        new Thread(new Runnable() {
            @Override
            public void run() {
                //耗时操作
                try {
                    Thread.sleep(3000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                textView.post(new Runnable() {
                    @Override
                    public void run() {
                        textView.setText("更新完成");
                    }
                });
            }
        }).start();
    }
``````
# AsyncTask
``````
 private AsyncTask a = new AsyncTask<String,Void,Boolean>(){

       @Override
       protected Boolean doInBackground(String... params) {
           //在后台执行耗时操作，其返回值将作为onPostExecute方法的参数
           return null;
       }

       @Override
       protected void onPreExecute() {
           //即将要执行耗时任务时回调，这里可以做一些初始化操作
           super.onPreExecute();
       }

       @Override
       protected void onPostExecute(Boolean aBoolean) {
        //异步任务执行完成后，也就是doInBackground（）方法完成后,其方法的返回结果就是这里的参数
           //运行再主线程中哦，更新更新
           super.onPostExecute(aBoolean);
       }

       @Override
       protected void onProgressUpdate(Void... values) {
           //由publishProgress内部调用，表示任务进度更新
           //更新更新
           super.onProgressUpdate(values);
       }
   };
``````

