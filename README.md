# SlideMenu
自定义侧滑菜单布局(NavigationView+DrawerLayout)的实现

## 效果图

![GIF.gif](http://upload-images.jianshu.io/upload_images/1074123-9070d90b2d5022e2.gif?imageMogr2/auto-orient/strip)

## 添加依赖

```gradle
compile 'com.android.support:design:25.0.1'
```

## 简单布局

```xml
<?xml version="1.0" encoding="utf-8"?>
<android.support.v4.widget.DrawerLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/drawer_layout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:fitsSystemWindows="true">


    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">

        <android.support.v7.widget.Toolbar
            android:id="@+id/tool_bar"
            android:layout_width="match_parent"
            android:layout_height="?attr/actionBarSize"
            android:fitsSystemWindows="true"
            android:background="@color/colorAccent"
            />

        <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:gravity="center_horizontal"
            android:text="你好 侧滑菜单!"
            android:textAllCaps="false"
            android:textColor="@color/colorAccent"
            android:textSize="25sp"/>
    </LinearLayout>

    <android.support.design.widget.NavigationView
        android:id="@+id/navigation_view"
        android:layout_width="420dp"
        android:layout_height="match_parent"
        android:layout_gravity="start"
        android:fitsSystemWindows="true"
      ></android.support.design.widget.NavigationView>
</android.support.v4.widget.DrawerLayout>
```
## 代码实现

```java
import android.os.Bundle;
import android.support.design.widget.NavigationView;
import android.support.design.widget.Snackbar;
import android.support.v4.content.ContextCompat;
import android.support.v4.widget.DrawerLayout;
import android.support.v7.app.ActionBarDrawerToggle;
import android.support.v7.app.AppCompatActivity;
import android.support.v7.widget.Toolbar;
import android.view.View;
import android.widget.ImageView;
import android.widget.LinearLayout;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity implements View.OnClickListener {
    private DrawerLayout mDrawerLayout;
    private Toolbar mToolbar;
    private NavigationView mNavigationView;
    private ActionBarDrawerToggle mDrawerToggle;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        init();
    }

    private void init() {
        mDrawerLayout = (DrawerLayout) findViewById(R.id.drawer_layout);
        mNavigationView = (NavigationView) findViewById(R.id.navigation_view);
        mToolbar = (Toolbar) findViewById(R.id.tool_bar);
        mToolbar.setTitle("littonishir");
        mToolbar.setTitleTextColor(ContextCompat.getColor(this, R.color.white));
        setSupportActionBar(mToolbar);
        getSupportActionBar().setDisplayHomeAsUpEnabled(true);

        mDrawerToggle = new ActionBarDrawerToggle(this, mDrawerLayout, mToolbar, R.string.drawer_layout_open, R.string.drawer_layout_close);
        mDrawerToggle.setDrawerIndicatorEnabled(true);
        mDrawerToggle.syncState();
        mDrawerLayout.setDrawerListener(mDrawerToggle);
        mDrawerLayout.setStatusBarBackgroundColor(ContextCompat.getColor(this, R.color.colorPrimaryDark));
        //自定义NavigationView布局加载
        View headerView = mNavigationView.inflateHeaderView(R.layout.nav_header_main);
        ImageView imageView = (ImageView) headerView.findViewById(R.id.iv_head);
        TextView textView = (TextView)headerView.findViewById(R.id.tv_username);
        LinearLayout ll_1 = (LinearLayout)headerView.findViewById(R.id.ll_one);
        LinearLayout ll_2 = (LinearLayout)headerView.findViewById(R.id.ll_two);
        LinearLayout ll_3 = (LinearLayout)headerView.findViewById(R.id.ll_thr);
        LinearLayout ll_4 = (LinearLayout)headerView.findViewById(R.id.ll_four);
        LinearLayout ll_5 = (LinearLayout)headerView.findViewById(R.id.ll_fi);
        imageView.setOnClickListener(this);
        textView.setOnClickListener(this);
        ll_1.setOnClickListener(this);
        ll_2.setOnClickListener(this);
        ll_3.setOnClickListener(this);
        ll_4.setOnClickListener(this);
        ll_5.setOnClickListener(this);
    }


    @Override
    public void onClick(View view) {
        switch (view.getId()){
            case R.id.iv_head :
                Snackbar.make(view, "我是图片", Snackbar.LENGTH_SHORT).show();
                break;

            case R.id.tv_username:
                Snackbar.make(view, "我是名字", Snackbar.LENGTH_SHORT).show();
                break;
            case R.id.ll_one:
                Snackbar.make(view, "ITEMLALALA1", Snackbar.LENGTH_SHORT).show();
                break;
            case R.id.ll_two:
                Snackbar.make(view, "ITEMLALALA2", Snackbar.LENGTH_SHORT).show();
                break;
            case R.id.ll_thr:
                Snackbar.make(view, "ITEMLALALA3", Snackbar.LENGTH_SHORT).show();
                break;
            case R.id.ll_four:
                Snackbar.make(view, "ITEMLALALA4", Snackbar.LENGTH_SHORT).show();
                break;
            case R.id.ll_fi:
                Snackbar.make(view, "ITEMLALALA5", Snackbar.LENGTH_SHORT).show();
                break;
        }

    }

}
```
欢迎start 红心 

[作者简书](http://www.jianshu.com/p/dcdafe00076c)
