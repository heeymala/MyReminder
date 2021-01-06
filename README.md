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

- Set View Padding
```java
LinearLayout parent = findViewById(R.id.parent);
parent.setPadding(0, 0, 0, 0);
```

---

```
Copyright 2021 M. Fadli Zein
```