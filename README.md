# Tugas Pertemuan 9
Nama &nbsp; &nbsp;: Rhendy Diki Nugraha<br>
NIM&nbsp; &nbsp; &nbsp; : 312210150<br>
Kelas&ensp; &nbsp; : TI.22.A.1<br>
Dosen &nbsp; : Donny Maulana, S.Kom., M.M.S.I.<br><br>
*Semua source code sudah saya sertakan dalam repository ini.*

## Perintah Tugas
Project membuat aplikasi intent, yang menghubungkan semua activity yang sudah dibuat sebelumnya.<br>
![image](https://github.com/RhendyDikiN/Intent-App/assets/115677376/0e21e70e-b6a4-480b-9c4b-885e213a0c39)

## 1. Launcher Splash Logo
Pertama, yang akan Saya lakukan adalah membuat Launcher Splash Logo, atau menampilkan logo saat kita pertama kali membuka aplikasi.<br>
Caranya adalah :<br>

- Membuat sebuah Drawable Resource File baru, untuk background logo launcher kita nanti. Buat file baru pada directory *res/drawable/disini*.<br>
![new](https://github.com/RhendyDikiN/Intent-App/assets/115677376/42df77da-946c-4636-a367-99a6a4886097)<br>

- Jika file berhasil dibuat, kita tambahkan terlebih dahulu logo yang kita miliki ke dalam project kita, caranya hanya copy logonya, lalu paste di folder *drawable* tadi.<br>
![copaslogo](https://github.com/RhendyDikiN/Intent-App/assets/115677376/08239c2f-0d4d-4f3d-bdbd-4521a29d39e0)<br>

- Lalu buka backgroundlauncher.xml yang sudah dibuat tadi, dan masukan code ini :<br>
```
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:drawable="@color/grey"/>
    <item>
        <bitmap
            android:src="@drawable/logo"
            android:gravity="center" />
    </item>
</layer-list>
```
>warna bisa menyesuaikan dengan keinginan, lalu masukan logo yang sudah kita tambahkan tadi.<br>

- Lalu, buka **themes.xml** yang letaknya ada di *res/values/themes*, dan tambahkan code ini didalam resourcesnya :<br>
```
  <style name="SplashScreen" parent="Theme.MaterialComponents.DayNight.NoActionBar">
        <item name="android:windowBackground">@drawable/backgroundlauncher</item>
        <item name="android:statusBarColor">?attr/colorOnPrimary</item>
  </style>
```

- Lanjut, kita buat java class nya, agar splashscreen bisa berjalan.<br>
![ezgif com-video-to-gif](https://github.com/RhendyDikiN/Intent-App/assets/115677376/b2548459-9ed2-4cbe-8582-2f3153ae8796)<br>
didalam SplashScreen.java ini, kita buat codenya, seperti ini :<br>
```
package com.example.tugassembilan;

import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;

import androidx.appcompat.app.AppCompatActivity;

public class SplashScreen extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        new Handler().postDelayed(new Runnable() {
            @Override
            public void run() {
                startActivity(new Intent(SplashScreen.this, MainActivity.class));
                finish();
            }
        }, 2500);
    }
}
```
>code ini berguna untuk menampilkan splashcreen, ketika splashscreen selesai dalam 2.5 detik nanti akan langsung berpindah ke MainActivity.java.<br>

- Buka **AndroidManifest.xml**, dan tambahkan code berikut didalam *application* :<br>
```
        <activity
            android:name=".SplashScreen"
            android:exported="true"
            android:theme="@style/SplashScreen">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
```
Dengan ini, perintah membuat Launcher Splash Logo sudah selesai, lanjut ke tahap berikutnya yaitu membuat menu untuk menampilkan semua project yang sudah dibuat pada pertemuan sebelumnya.<br>

## 2. Menu Utama
Yang kedua, disini Saya akan membuat menu utamanya yang akan berjalan setelah SplashScreen Logo tadi.<br>
Caranya adalah:<br>

- Jika awal pembuatan project kita memilih template *empty views activity*, maka pada layout otomatis terbuat file *activity_main.xml* dan pada java akan terbuat *MainActivity.java*
  Langsung saja kita buka **activity_main.xml**, dan buat code seperti berikut ini:<br>

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"
        android:src="@drawable/background" />

    <Button
        android:id="@+id/btnHelloWorld"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="btnHelloWorld"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="200dp"
        android:text="@string/project_hello"
        tools:ignore="UsingOnClickInXml" />

    <Button
        android:id="@+id/btnProjectCount"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="btnCount"
        android:layout_below="@+id/btnHelloWorld"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="20dp"
        android:text="@string/project_count"
        tools:ignore="UsingOnClickInXml" />

    <Button
        android:id="@+id/btnProjectSianida"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="btnSianida"
        android:layout_below="@+id/btnProjectCount"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="20dp"
        android:text="@string/project_sianida"
        tools:ignore="UsingOnClickInXml" />

    <Button
        android:id="@+id/btnTwoActivity"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="btnTwoActivity"
        android:layout_below="@+id/btnProjectSianida"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="20dp"
        android:text="@string/project_twoactivity"
        tools:ignore="UsingOnClickInXml" />

    <Button
        android:id="@+id/btnSetAlarm"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="btnSetAlarm"
        android:layout_below="@+id/btnTwoActivity"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="20dp"
        android:text="@string/project_set_alarm"
        tools:ignore="UsingOnClickInXml" />

</RelativeLayout>
```
>Background disini sesuai dengan keinginan, tambahkan gambar kedalam folder *drawable* seperti memasukan logo pada cara sebelumnya.<br>
>Tampilan desain:<br>
>![image](https://github.com/RhendyDikiN/Intent-App/assets/115677376/6bdc4699-0318-4e93-9a91-9a319cf06427)

- Setelah itu kita buka, MainActivity.java untuk menambahkan code intent untuk masing-masing tombol.<br>
```
package com.example.tugassembilan;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        findViewById(R.id.btnSetAlarm).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Panggil metode untuk mengatur alarm
                setAlarm();
            }
        });
    }
    private void setAlarm() {
        Intent alarm = new Intent(android.provider.AlarmClock.ACTION_SET_ALARM);
        startActivity(alarm);
    }

    public void btnHelloWorld(View view) {
        Intent helloworld = new Intent(MainActivity.this, HelloActivity.class);
        startActivity(helloworld);
    }

    public void btnCount(View view) {
        Intent count = new Intent(MainActivity.this, CountActivity.class);
        startActivity(count);
    }

    public void btnSianida(View view) {
        Intent sianida = new Intent(MainActivity.this, SianidaActivity.class);
        startActivity(sianida);
    }

    public void btnTwoActivity(View view) {
        Intent twoact = new Intent(MainActivity.this, TwoactActivity.class);
        startActivity(twoact);
    }
}
```
>semua button dari a - d menggunakan explicit intent, dan button e. Project Set Alarm menggunakan implicit intent.<br>

Dengan ini menu halaman utama, dengan tombol-tombol sudah berhasil dibuat. Selanjutnya kita hanya tinggal menambahkan beberapa coding kedalam **AndroidManifest.xml** agar aplikasi dapat berjalan.<br>

## 3. AndroidManifest.xml
Didalam AndroidManifest.xml ini kita tambahkan semua .java dari semua project kita sebelumnya. Berikut nama .java dari berbagai project yang telah saya buat:<br>
- a. Project Hello World = HelloActivity.java
- b. Project Count = CountActivity.java
- c. Project Sianida = SianidaActivity.java
- d. Project TwoActivity = TwoactActivity.java dan Twoact2Activity.java
- e. Project Set Alarm = MainActivity.java (karena implicit intent, jadi code untuk set alarm dibuat langsung disini)
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <uses-permission
        android:name="com.android.alarm.permission.SET_ALARM" />
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.TugasSembilan"
        tools:targetApi="31">

        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.SET_ALARM" />
                <category android:name="android.intent.category.DEFAULT" />
            </intent-filter>
        </activity>

        <activity
            android:name=".HelloActivity"
            android:exported="true" />

        <activity
            android:name=".TwoactActivity"
            android:exported="true" />

        <activity
            android:name=".Twoact2Activity"
            android:exported="true" />

        <activity
            android:name=".CountActivity"
            android:exported="true" />

        <activity
            android:name=".SianidaActivity"
            android:exported="true" />

        <activity
            android:name=".SplashScreen"
            android:exported="true"
            android:theme="@style/SplashScreen">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```
## 4. Hasil RUN
Berikut video hasil RUN, dari aplkasi yang sudah saya buat ini :<br>

https://github.com/RhendyDikiN/Intent-App/assets/115677376/104224a1-493b-41dd-9880-dd7429013064

