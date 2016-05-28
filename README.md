# CheckBox-RadioButton

android 49 lesson
1.CheckBox复选框：允许选择一个或多个选项,复选框的点击相应事件通过配置activity_main.xml中的 android:onClick 属性来完成.
2.CheckBox实例：在res->layout—>activity_main.xml中：
  <?xml version="1.0" encoding="utf-8"?>
  <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
      xmlns:tools="http://schemas.android.com/tools"
      android:layout_width="match_parent"
      android:layout_height="match_parent"
      android:paddingBottom="@dimen/activity_vertical_margin"
      android:paddingLeft="@dimen/activity_horizontal_margin"
      android:paddingRight="@dimen/activity_horizontal_margin"
      android:paddingTop="@dimen/activity_vertical_margin"
      tools:context="com.example.mackerlee.android_49.MainActivity">
  
      <CheckBox
          android:id="@+id/city_bj"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"
          android:text="北京"
          //--设置CheckBox的响应事件
          android:onClick="onCheckboxClicked"/>
      <CheckBox
          android:id="@+id/city_sh"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"
          android:layout_below="@id/city_bj"
          android:text="上海"
          android:onClick="onCheckboxClicked"/>
      <CheckBox
          android:id="@+id/city_gz"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"
          android:layout_below="@id/city_sh"
          android:text="广州"
          android:onClick="onCheckboxClicked"/>
  
  </RelativeLayout>

  在app->java->包名->MainActivity.java中
  package com.example.mackerlee.android_49;

  import android.support.v7.app.AppCompatActivity;
  import android.os.Bundle;
  import android.view.View;
  import android.widget.CheckBox;
  
  /**
   * CheckBox组件的使用
   */
  public class MainActivity extends AppCompatActivity {
  
      private CheckBox cb_bj,cb_sh,cb_gz;
      @Override
      protected void onCreate(Bundle savedInstanceState) {
          super.onCreate(savedInstanceState);
          setContentView(R.layout.activity_main);
          cb_bj = (CheckBox)findViewById(R.id.city_bj);
          cb_sh = (CheckBox)findViewById(R.id.city_sh);
          cb_gz = (CheckBox)findViewById(R.id.city_gz);
  
      }
  
      public void onCheckboxClicked(View view) {
        //--类型转换，然后判断是否被选中
        boolean checked = ((CheckBox) view).isChecked();
        //--根据组件ID判断
        switch(view.getId()) {
            //--根据选中不同的组件判断不同的功能
            case R.id.city_bj:
                if (checked){
                    Toast.makeText(this,((CheckBox) view).getText().toString(),Toast.LENGTH_LONG).show();
                }else{
                    Toast.makeText(this,"已取消"+((CheckBox) view).getText().toString(),Toast.LENGTH_LONG).show();
                }
                break;
            case R.id.city_sh:
                if (checked){
                    Toast.makeText(this,((CheckBox) view).getText().toString(),Toast.LENGTH_LONG).show();
                }else{
                    Toast.makeText(this,"已取消"+((CheckBox) view).getText().toString(),Toast.LENGTH_LONG).show();
                }
                break;
            case R.id.city_gz:
                if (checked){
                    Toast.makeText(this,((CheckBox) view).getText().toString(),Toast.LENGTH_LONG).show();
                }else{
                    Toast.makeText(this,"已取消"+((CheckBox) view).getText().toString(),Toast.LENGTH_LONG).show();
                 }
                break;
        }
    }
  
  }

android 50-51 lesson
1.RadioButton:单选按钮，只能选择一个选项并响应.由于一组单选按钮之间是互斥关系，因此必须将一组相关的单选按钮用RadioGroup内把他               们分组在一起,通过分组在一起可以选择系统确保只能有一个单选按钮.
2.RadioButton实例：在res->layout->radiobutton_activity_main.xml中：
  <?xml version="1.0" encoding="utf-8"?>
  <?xml version="1.0" encoding="utf-8"?>
  <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context="com.example.mackerlee.android_49.MainActivity">
      //--设置RADIO组  
      <RadioGroup
          android:id="@+id/radiogroup01"
          android:layout_width="match_parent"
          android:layout_height="wrap_content"
          //--设置Radio组水平排列，默认是垂直排列
          android:orientation="horizontal">
          <RadioButton
              android:id="@+id/radio01"
              android:layout_width="wrap_content"
              android:layout_height="wrap_content"
              //--设置该radio默认选中
              android:checked="true"
              android:text="男"
              //--设置响应程序
              android:onClick="onRadioButtonClicked"/>
          <RadioButton
              android:id="@+id/radio02"
              android:layout_width="wrap_content"
              android:layout_height="wrap_content"
              android:text="女"
              //--设置响应程序
              android:onClick="onRadioButtonClicked"/>
      </RadioGroup>
  
  </RelativeLayout>

  如何在app->java->包名->MainActivity.java中设置上面的布局和响应程序：
  package com.example.mackerlee.android_49;

  import android.support.v7.app.AppCompatActivity;
  import android.os.Bundle;
  import android.view.View;
  import android.widget.CheckBox;
  import android.widget.RadioButton;
  import android.widget.Toast;
  
  /**
   * CheckBox组件的使用
   */
  public class MainActivity extends AppCompatActivity {
  
      //private CheckBox cb_bj,cb_sh,cb_gz;
      private RadioButton rb_man,rb_woman;
      @Override
      protected void onCreate(Bundle savedInstanceState) {
          super.onCreate(savedInstanceState);
          //--设置自定义的布局
          setContentView(R.layout.radiobutto_activity_main);
          //cb_bj = (CheckBox)findViewById(R.id.city_bj);
          //cb_sh = (CheckBox)findViewById(R.id.city_sh);
          //cb_gz = (CheckBox)findViewById(R.id.city_gz);
  
          rb_man = (RadioButton)findViewById(R.id.radio01);
          rb_woman = (RadioButton)findViewById(R.id.radio02);
  
      }
  
      //--复选框组件单击事件
      /*
      public void onCheckboxClicked(View view) {
          //--类型转换，然后判断是否被选中
          boolean checked = ((CheckBox) view).isChecked();
          //--根据组件ID判断
          switch(view.getId()) {
              //--根据选中不同的组件判断不同的功能
              case R.id.city_bj:
                  if (checked){
                      Toast.makeText(this,((CheckBox) view).getText().toString(),Toast.LENGTH_LONG).show();
                  }else{
                      Toast.makeText(this,"已取消"+((CheckBox) view).getText().toString(),Toast.LENGTH_LONG).show();
                  }
                  break;
              case R.id.city_sh:
                  if (checked){
                      Toast.makeText(this,((CheckBox) view).getText().toString(),Toast.LENGTH_LONG).show();
                  }else{
                      Toast.makeText(this,"已取消"+((CheckBox) view).getText().toString(),Toast.LENGTH_LONG).show();
                  }
                  break;
              case R.id.city_gz:
                  if (checked){
                      Toast.makeText(this,((CheckBox) view).getText().toString(),Toast.LENGTH_LONG).show();
                  }else{
                      Toast.makeText(this,"已取消"+((CheckBox) view).getText().toString(),Toast.LENGTH_LONG).show();
                   }
                  break;
          }
      }
      */
      //--单选按钮的单击事件响应方法
      public void onRadioButtonClicked(View view) {
          // Is the button now checked?
          boolean checked = ((RadioButton) view).isChecked();
  
          // Check which radio button was clicked
          switch(view.getId()) {
              case R.id.radio01:
                  if (checked) {
                      //--选中
                      Toast.makeText(this, ((RadioButton) view).getText().toString(), Toast.LENGTH_LONG).show();
                  }
                  break;
              case R.id.radio02:
                  if (checked) {
                      //--选中
                      Toast.makeText(this, ((RadioButton) view).getText().toString(), Toast.LENGTH_LONG).show();
                  }
                  break;
          }
      }
  
  }

3.如果想在程序中改变RadioButton状态可以用setChecked(boolean) 或者toggle（）方法.
