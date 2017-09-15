# Test1  ---移动开发入门的第一个小实验

    功能简介：
      *界面有两个按钮，点击时分别弹出提示对话框和登录对话框
     **其中登录对话框要求用户输入UserId和Password
    ***如果UserId和Password不是“abc”、“123”，则使用Toast提示错误，否则提示成功。

    通过前几个课堂练习熟练了自己对一个简单的Android文件的基本结构，这是这个实验完成的前提。

    设计重难点：
    在界面功能键上引入对话框，并增加字段匹配。

    接下来我来分享一下我的经验
    布局： *每一个有功能的布局都一定要添加id字段。
         **弹出的对话框是第二个xml文件，在Java文件中引用实现
        ***对话框中的按钮不是在布局中写的，而是通过方法（Java代码）添加
     
    代码示例

    ---对话框的创建 
       AlertDialog.Builder builder = new AlertDialog.Builder(MainActivity.this);//创建一个对话框
       String tip = "/** 对话框的文字 **/";
       builder.setMessage(tip).setTitle("/** 对话框题目 **/");
       builder.show(); 
  
    ---对话框里按钮的添加
       builder.setPositiveButton("登录", new DialogInterface.OnClickListener() {  //功能代码...  });
       builder.setNeutralButton("取消", null);
       builder.setNegativeButton("退出", new DialogInterface.OnClickListener() {  //功能代码...  });
   
    ---获取对话框中文本框的值
       因为对话框和主界面分别是两个布局的显示，所以要使用这一步，同时声明两个布局
       final View view = inflater.inflate(R.layout./** 对话框布局名 **/, null);
   
       EditText et1 = (EditText) view.findViewById(R.id./** 对应edittext的id **/);
       String In1 = et1.getText().toString();
   
    ---匹配字段确认
       if (In1.equals("abc") && In2.equals("123")) { //功能代码...  }
       这里要使用 equals()方法 ，而尽量不要使用 == 匹配。
  
    到这里，基本的功能代码就已经实现了，布局方面还是那句话，一千个读者就有一千的哈姆莱特，没个人的想法创意不同，尽量开发自己的想象来完成自己的界面。
    最后，我在和大家分享我在编码过程中遇见的问题：R文件报错  

    ----R文件报错，有很多种可能的错误原因
       * 首先你要检查代码，确认代码没有问题（拼写错误，逻辑错误等等）
      ** 其次你可以clean工程后在rebuild，
     *** 最后还可以新建一个R文件后编译一下再删掉（试过一次成功，但不知道原理）
    **** 还有一个方法是同步（重编译）

     祝大家编码愉快，及时总结~
   
