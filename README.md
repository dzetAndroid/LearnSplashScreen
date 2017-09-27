# LearnSplashScreen

#### 网络上，两种办法：

 - 1 无SplashActivity，主要是 切换 theme
 - 2 有SplashActivity，单独的Activity，用来显示Splash theme，然后finish()

---

#### 无SplashActivity

> 效果图

![这里写图片描述](https://github.com/dzetAndroid/LearnSplashScreen/blob/master/screenshot/no_splash.gif?raw=true)

> 代码

https://github.com/dzetAndroid/LearnSplashScreen

##### 一 drawable文件夹 新建 splash.xml（根标签 layer-list）

> layer 图层

> opacity 不透明度

> opaque 不透明

> 可以使用mipmap文件夹下的图片，但是android studio没提示

```
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android"
    android:opacity="opaque">

    <item android:drawable="@color/colorPrimary" />
    <item>
        <bitmap
            android:gravity="center"
            android:src="@mipmap/ic_launcher"
            />
    </item>

</layer-list>
```

##### 二 定义 SplashTheme 继承 AppTheme

```
<resources>
  <style name="SplashTheme" parent="AppTheme">
    <item name="android:windowBackground">@drawable/splash</item>
  </style>
</resources>
```

##### 三 设置启动Activity，Theme（androidmanifest清单文件中）

```
<activity android:name=".activities.MainActivity"
  android:theme="@style/SplashTheme">
  <intent-filter>
    <action android:name="android.intent.action.MAIN" />
    <category android:name="android.intent.category.LAUNCHER" />
  </intent-filter>
</activity>
```

##### 四 最终，启动Activity，切换 原来Theme（Java代码中）

```
public class MainActivity extends AppCompatActivity {
   
  @Override
  protected void onCreate(Bundle savedInstanceState) {
    // Make sure this is before calling super.onCreate
    setTheme(R.style.AppTheme);
    super.onCreate(savedInstanceState);
  }
  
}
```

---

#### 有SplashActivity

> 效果图

![这里写图片描述](https://github.com/dzetAndroid/LearnSplashScreen/blob/master/screenshot/yes_splash.gif?raw=true)

> 代码

https://github.com/cstew/Splash

##### 一、二都是一样的

##### 三 设置SplashActivity Theme（清单文件中）

##### 四 最终，SplashActivity 跳转并Finish()

```
public class SplashActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        Intent intent = new Intent(this, MainActivity.class);
        startActivity(intent);
        finish();
    }
}
```


---
#### 参考来源：

##### 博客
https://android.jlelse.eu/launch-screen-in-android-the-right-way-aca7e8c31f52
https://stackoverflow.com/questions/5486789/how-do-i-make-a-splash-screen/15832037#15832037

https://www.bignerdranch.com/blog/splash-screens-the-right-way/

##### 视频（英文）
https://www.youtube.com/watch?time_continue=160&v=E5Xu2iNHRkk
https://github.com/dzetAndroid/androidVideo（该视频已存储至个人github，欢迎下载，观看）

##### 关于两种模式的思考

https://android.jlelse.eu/which-splash-screen-approaches-is-better-4de3128988fd
> 这篇，进行了讨论，但是个人未发现，无SplashActivity版的，

> 切换Activity出现Splash theme的现象


---

#### 小点

> YouTube官方Android教程也是无SplashActivity版

---
end
