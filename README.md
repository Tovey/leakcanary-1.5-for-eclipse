# leakcanary-1.5-for-eclipse
move leakcanary 1.5 to eclipse library

该项目将[LeakCanary](https://github.com/square/leakcanary)的1.5版本，移植到Eclipse平台下。

## 使用方法
1、 导入leakcanary-1.5-eclipse到eclipse中，并在你的项目中引用该library
2、 在AndroidManifest.xml中添加权限及相关service和Activity

```xml
    <!-- To store the heap dumps and leak analysis results. -->
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />

    <application>
        <service
            android:name="com.squareup.leakcanary.internal.HeapAnalyzerService"
            android:enabled="false"
            android:process=":leakcanary" />
        <service
           android:name="com.squareup.leakcanary.DisplayLeakService"
            android:enabled="false" />
        <activity
           android:name="com.squareup.leakcanary.internal.DisplayLeakActivity"
            android:enabled="false"
            android:icon="@drawable/leak_canary_icon"
            android:label="@string/leak_canary_display_activity_label"
            android:taskAffinity="com.squareup.leakcanary"
            android:theme="@style/leak_canary_LeakCanary.Base" >
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        <activity
            android:name="com.squareup.leakcanary.internal.RequestStoragePermissionActivity"
            android:enabled="false"
            android:icon="@drawable/leak_canary_icon"
            android:label="@string/leak_canary_storage_permission_activity_label"
            android:taskAffinity="com.squareup.leakcanary"
            android:theme="@style/leak_canary_Theme.Transparent" />
    </application>
```
3、代码中的使用用法见示例工程leakcanary-sample
4、如果有其他问题，请参照[LeakCanary官方Git](https://github.com/square/leakcanary)
 