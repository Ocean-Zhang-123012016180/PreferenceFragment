MainActivity.java
package com.example.myapplication;


import android.app.FragmentManager;
import android.app.FragmentTransaction;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        //加载Fragment
        FragmentManager fragmentManager=getFragmentManager();
        //开启一个新事务
        FragmentTransaction transaction=fragmentManager.beginTransaction();
        PreFragment preFragment=new PreFragment();
        transaction.add(android.R.id.content,preFragment);
        transaction.commit();
    }
}

PreFragment.java
package com.example.myapplication;


        import android.os.Bundle;
        import android.preference.PreferenceFragment;
        import android.support.annotation.Nullable;
public class PreFragment extends PreferenceFragment {
    @Override
    public void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        //从xml文件中加载选项
        addPreferencesFromResource(R.xml.preference);
    }
}

preference.xml
<?xml version="1.0" encoding="utf-8"?>
<PreferenceScreen xmlns:android="http://schemas.android.com/apk/res/android">
    <PreferenceCategory android:title="In-line preferences">
        <CheckBoxPreference
            android:key="checkbox_preference"
            android:summary="This a checkbox"
            android:title="Checkbox_preference"/>
    </PreferenceCategory>
    <PreferenceCategory android:title="Dialog-based preferences">
        <EditTextPreference
            android:dialogTitle="Enter your favorite animal"
            android:title="EditTextPreference"
            android:key="edittext_preference"
            android:summary="An example that uses an edit text dialog"/>
        <ListPreference
            android:entries="@array/options"
            android:entryValues="@array/options"
            android:dialogTitle="Choose one"
            android:summary="An example that use a list dialog"
            android:title="List prefernce"
            android:key="list_preference"/>
        <!--需要补充列表项的数据来源-->
    </PreferenceCategory>
    <PreferenceCategory android:title="Launch preferences">
        <PreferenceScreen
            android:key="screen_preference"
            android:summary="Shows another screen of preferences"
            android:title="Screen preference">
            <CheckBoxPreference
                android:key="next_scrren_checkbox_preference"
                android:summary="Preference that is on the next screen but same hierarchy"
                android:title="Toggle preference"/>
        </PreferenceScreen>
        <PreferenceScreen
            android:summary="Launches an Activity from an intent"
            android:title="Intent preference"/>
        <intent
            android:action="android.intent.action.VIEW"
            android:data="http://www.google.com"/>
    </PreferenceCategory>
    <!--设置项关联，选中父选项时，子选项才显示。使用dependency属性-->
    <PreferenceCategory android:title="Preference attributes">
        <CheckBoxPreference
            android:key="parent_checkbox_preference"
            android:summary="This is visually parent"
            android:title="Parent checkbox preference" />
        <!-- 子类的可见类型是由样式属性定义的 -->
        <CheckBoxPreference
            android:dependency="parent_checkbox_preference"
            android:key="child_checkbox_preference"
            android:summary="This is visually a child"
            android:title="Child checkbox preference" />
    </PreferenceCategory>
</PreferenceScreen>

遇到的问题：不知道为什么每次GitHub上传实验总是上传上一次实验的内容，好比这次Preference项目上传的确实UI的项目，实验3的项目上传的结果是实验二的项目，很郁闷！
![Image text](https://github.com/Ocean-Zhang-123012016180/PreferenceFragment/blob/master/image/QQ%E6%88%AA%E5%9B%BE20190505163046.png)
![Image text](https://github.com/Ocean-Zhang-123012016180/PreferenceFragment/blob/master/image/QQ%E6%88%AA%E5%9B%BE20190505163059.png)
![Image text](https://github.com/Ocean-Zhang-123012016180/PreferenceFragment/blob/master/image/QQ%E6%88%AA%E5%9B%BE20190505163109.png)
![Image text](https://github.com/Ocean-Zhang-123012016180/PreferenceFragment/blob/master/image/QQ%E6%88%AA%E5%9B%BE20190505163117.png)
![Image text](https://github.com/Ocean-Zhang-123012016180/PreferenceFragment/blob/master/image/QQ%E6%88%AA%E5%9B%BE20190505163135.png)



