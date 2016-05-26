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
          // Is the view now checked?
          boolean checked = ((CheckBox) view).isChecked();
  
          // Check which checkbox was clicked
          switch(view.getId()) {
              case R.id.city_bj:
                  if (checked){
  
                  }else{
  
                  }
                  break;
              case R.id.city_sh:
                  if (checked){
  
                  } else{
  
                  }
                  break;
              case R.id.city_gz:
                  if (checked){
  
                  } else{
  
                  }
                  break;
          }
      }
  
  }

