# MyReminder
 Remider Confused Program

- `style.xml`
```xml
//type 1
<item name="android:statusBarColor" tools:targetApi="l">@android:color/white</item>
<item name="android:fitsSystemWindows">false</item>

//type 2
<item name="android:navigationBarColor">@color/black</item>
<item name="android:windowLightNavigationBar" tools:targetApi="27">true</item>
```
```java
int decore = -1;
//type 1
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.M) {
    //enable this tho maker icon status bar become black
    decore += View.SYSTEM_UI_FLAG_LIGHT_STATUS_BAR;
}

//type 2
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
    //enable this tho maker icon Navigation bar become black
    decore +=  View.SYSTEM_UI_FLAG_LIGHT_NAVIGATION_BAR;
}

getWindow().getDecorView().setSystemUiVisibility(decore);
```
#
- View Height
```java
LinearLayout content = findViewById(R.id.content);
LinearLayout.LayoutParams layoutParams;
//Width Height
layoutParams = new LinearLayout.LayoutParams(
        ViewGroup.LayoutParams.MATCH_PARENT,
        GblFunction.getValueInDP(getApplicationContext(), 100)
);
```
[GblFunction.java](https://github.com/gzeinnumer/ImmersiveBestConfig/blob/master/README.md#gblfunction)
#
- Set View Padding
```java
LinearLayout parent = findViewById(R.id.parent);
parent.setPadding(0, 0, 0, 0);
```
#
- Height actionBarSize
```xml
android:layout_marginTop="?attr/actionBarSize"
```
#
- Remove WORD
```java
String str = "Select * FROM table1 WHERaE 1";
String strTemp = str.toUpperCase();
String toRemove = "WHERE";
int x = strTemp.indexOf(toRemove);
if (x != -1) str = str.substring(0,x) + str.substring(x+toRemove.length(),str.length());
Log.d(TAG, "onCreate_: " + str);
```
#
- `GblVariable.myDB`
```java
public class GblVariabel {
    private static final String TAG = "GblVariabel";

    public static SQLiteDatabase myDb = null;

    public static void initDb(Context context) {
        DatabaseHelperOLD dbHelper = null;
        try {
            dbHelper = new DatabaseHelperOLD(context);k
            if (dbHelper.checkDatabase()) {
                GblVariabel.myDb = dbHelper.openDataBase();
            } else {
                Log.e(TAG, "initDb:  database kosong");
            }
        } catch (Throwable throwable) {
            throwable.printStackTrace();
            Log.e(TAG, "initDb: " + throwable.getMessage());
        }
    }
}
```
[DatabaseHelper](https://github.com/gzeinnumer/MyReminder/blob/master/files/DatabaseHelper.java)
& [DatabaseHelper Old Style](https://github.com/gzeinnumer/MyReminder/blob/master/files/DatabaseHelperOLD.java)
#
- External android 10 Spesial Permit
```xml
<application
    android:requestLegacyExternalStorage="true">

</application>
```
#
- Get Color
```java
ColorStateList color = ContextCompat.getColorStateList(this, R.color.white);
Color color = Color.parseColor("#F2F5F8");
int color = 0xFFCC5500;
```
#
- Get Drawable
```java
final int sdk = android.os.Build.VERSION.SDK_INT;
if(sdk < android.os.Build.VERSION_CODES.JELLY_BEAN) {
    layout.setBackgroundDrawable(ContextCompat.getDrawable(context, R.drawable.ready) );
} else {
    layout.setBackground(ContextCompat.getDrawable(context, R.drawable.ready));
}
```
#
- TextInputLayout Hint Color
```xml
<com.google.android.material.textfield.TextInputLayout
    android:textColorHint="@color/colorPrimary">

    <com.google.android.material.textfield.TextInputEditText />
</com.google.android.material.textfield.TextInputLayout>
```
#
- TextInputLayout Password Toggle
```xml
<com.google.android.material.textfield.TextInputLayout
    app:endIconMode="password_toggle">

    <com.google.android.material.textfield.TextInputEditText/>
</com.google.android.material.textfield.TextInputLayout>
```
#
- Timer CountDown
```java
//30 second 29 Second 28 Second ...... 1 Second
new CountDownTimer(30000, 1000) {

    public void onTick(long millisUntilFinished) {
        int progress = (int) millisUntilFinished / 1000;

    }

    public void onFinish() {

    }
}.start();
```
#
- adjustResize & screenOrientation
```xml
android:screenOrientation="portrait"
android:windowSoftInputMode="adjustResize"
```

---

```
Copyright 2021 M. Fadli Zein
```