# MyReminder
 Remider Confused Program

- `style.xml`
```
<item name="android:statusBarColor" tools:targetApi="l">@android:color/white</item>
<item name="android:fitsSystemWindows">false</item>
<item name="android:navigationBarColor">@color/black</item>
```

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

- Set View Padding
```java
LinearLayout parent = findViewById(R.id.parent);
parent.setPadding(0, 0, 0, 0);
```

- Height actionBarSize
```xml
android:layout_marginTop="?attr/actionBarSize"
```

- Remove WORD
```java
String str = "Select * FROM table1 WHERaE 1";
String strTemp = str.toUpperCase();
String toRemove = "WHERE";
int x = strTemp.indexOf(toRemove);
if (x != -1) str = str.substring(0,x) + str.substring(x+toRemove.length(),str.length());
Log.d(TAG, "onCreate_: " + str);
```

- `GblVariable.myDB`
```java
public class GblVariabel {
    private static final String TAG = "GblVariabel";

    public static SQLiteDatabase myDb = null;

    public static void initDb(Context context) {
        DatabaseHelperOLD dbHelper = null;
        try {
            dbHelper = new DatabaseHelperOLD(context);
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
[DatabaseHelper](https://github.com/gzeinnumer/MyLibSimpleSQLite/blob/master/app/src/main/java/com/gzeinnumer/mylibsimplesqlite/helper/DatabaseHelper.java)
[DatabaseHelper Old Style](https://github.com/gzeinnumer/MyLibSimpleSQLite/blob/master/app/src/main/java/com/gzeinnumer/mylibsimplesqlite/helper/DatabaseHelper.java)

---

```
Copyright 2021 M. Fadli Zein
```