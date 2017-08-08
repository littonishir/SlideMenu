# SlideMenu
自定义侧滑菜单布局(NavigationView+DrawerLayout)的实现

## 效果图

![GIF.gif](http://upload-images.jianshu.io/upload_images/1074123-d866a58440855d47.gif?imageMogr2/auto-orient/strip)

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

        <android.support.design.widget.AppBarLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content">

            <android.support.v7.widget.Toolbar
                android:id="@+id/tool_bar"
                android:layout_width="match_parent"
                android:layout_height="?attr/actionBarSize"
                android:background="@color/colorAccent" />

        </android.support.design.widget.AppBarLayout>

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="center_horizontal"
            android:layout_margin="@dimen/size_10dp"
            android:paddingTop="@dimen/size_120dp"
            android:text="你好 侧滑菜单 !"
            android:textColor="@color/colorAccent"
            android:textSize="20sp" />

    </LinearLayout>

    <android.support.design.widget.NavigationView
        android:id="@+id/navigation_view"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_gravity="start"
        android:fitsSystemWindows="true"></android.support.design.widget.NavigationView>
</android.support.v4.widget.DrawerLayout>
```
## 代码实现

```java
import android.graphics.Color;
import android.os.Build;
import android.os.Bundle;
import android.support.annotation.RequiresApi;
import android.support.design.widget.NavigationView;
import android.support.design.widget.Snackbar;
import android.support.v4.content.ContextCompat;
import android.support.v4.view.GravityCompat;
import android.support.v4.widget.DrawerLayout;
import android.support.v7.app.ActionBar;
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
    private ActionBar actionBar;

    @RequiresApi(api = Build.VERSION_CODES.LOLLIPOP)
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        //透明状态栏
        transparentStatusBar();
        //初始化控件
        initView();
    }

    private void initView() {
        mDrawerLayout = (DrawerLayout) findViewById(R.id.drawer_layout);
        mNavigationView = (NavigationView) findViewById(R.id.navigation_view);
        mToolbar = (Toolbar) findViewById(R.id.tool_bar);
        //设置Toolbar
        mToolbar.setTitle("littonishir");
        mToolbar.setTitleTextColor(ContextCompat.getColor(this, R.color.white));
        setSupportActionBar(mToolbar);
        actionBar = getSupportActionBar();
        actionBar.setDisplayHomeAsUpEnabled(true);
        //设置DrawerToggle
        mDrawerToggle = new ActionBarDrawerToggle(this, mDrawerLayout, mToolbar, R.string.drawer_layout_open, R.string.drawer_layout_close);
        mDrawerToggle.setDrawerIndicatorEnabled(true);
        mDrawerToggle.syncState();
        mDrawerLayout.addDrawerListener(mDrawerToggle);
        mDrawerLayout.setStatusBarBackgroundColor(ContextCompat.getColor(this, R.color.colorAccent));
        //自定义NavigationView布局加载
        View headerView = mNavigationView.inflateHeaderView(R.layout.nav_header_main);
        ImageView imageView = (ImageView) headerView.findViewById(R.id.iv_head);
        TextView textView = (TextView) headerView.findViewById(R.id.tv_username);
        LinearLayout ll_1 = (LinearLayout) headerView.findViewById(R.id.ll_one);
        LinearLayout ll_2 = (LinearLayout) headerView.findViewById(R.id.ll_two);
        LinearLayout ll_3 = (LinearLayout) headerView.findViewById(R.id.ll_thr);
        LinearLayout ll_4 = (LinearLayout) headerView.findViewById(R.id.ll_four);
        LinearLayout ll_5 = (LinearLayout) headerView.findViewById(R.id.ll_fi);
        //设置点击监听
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
        switch (view.getId()) {
            case R.id.iv_head:
                Snackbar.make(view, "我是图片", Snackbar.LENGTH_SHORT).show();
                break;

            case R.id.tv_username:
                Snackbar.make(view, "我是名字", Snackbar.LENGTH_SHORT).show();
                break;
            case R.id.ll_one:
                mDrawerLayout.closeDrawer(GravityCompat.START);
                Snackbar.make(view, "侧滑菜单已关闭", Snackbar.LENGTH_SHORT).show();
                break;
            case R.id.ll_two:
                mDrawerLayout.closeDrawer(GravityCompat.START);
                Snackbar.make(view, "侧滑菜单已关闭", Snackbar.LENGTH_SHORT).show();
                break;
            case R.id.ll_thr:
                mDrawerLayout.closeDrawer(GravityCompat.START);
                Snackbar.make(view, "侧滑菜单已关闭", Snackbar.LENGTH_SHORT).show();
                break;
            case R.id.ll_four:
                mDrawerLayout.closeDrawer(GravityCompat.START);
                Snackbar.make(view, "侧滑菜单已关闭", Snackbar.LENGTH_SHORT).show();
                break;
            case R.id.ll_fi:
                mDrawerLayout.closeDrawer(GravityCompat.START);
                Snackbar.make(view, "侧滑菜单已关闭", Snackbar.LENGTH_SHORT).show();
                break;
        }

    }

    private void transparentStatusBar() {
        if (Build.VERSION.SDK_INT >= 21) {
            View decorView = getWindow().getDecorView();
            int option = View.SYSTEM_UI_FLAG_LAYOUT_FULLSCREEN
                    | View.SYSTEM_UI_FLAG_LAYOUT_STABLE;
            decorView.setSystemUiVisibility(option);
            getWindow().setStatusBarColor(Color.TRANSPARENT);
        }
    }
}
```
欢迎start 红心 点赞

[作者简书](http://www.jianshu.com/p/dcdafe00076c)
