## Workshop-01 Develop an android application to pass the data between the activities using Intent.

## Instructions:

1.Create in design part user name, user age, user emailid and user contactnumber.
  
2.Read the input value from the user.
  
3.Display the output on the other activities.

## activity_main.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/numberEditText4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="348dp"
        android:autofillHints=""
        android:ems="10"
        android:hint="Enter Phone Number"
        android:inputType="phone"
        android:minHeight="48dp"
        android:text=""
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="@+id/numberEditText3"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="@+id/numberEditText3"
        tools:ignore="LabelFor,TextFields,SpeakableTextPresentCheck" />

    <EditText
        android:id="@+id/numberEditText3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:autofillHints=""
        android:ems="10"
        android:hint="Enter MailID"
        android:inputType="textEmailAddress"
        android:minHeight="48dp"
        android:text=""
        app:layout_constraintBottom_toTopOf="@+id/numberEditText4"
        app:layout_constraintEnd_toEndOf="@+id/numberEditText2"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="@+id/numberEditText2"
        app:layout_constraintTop_toBottomOf="@+id/numberEditText2"
        app:layout_constraintVertical_bias="0.428"
        tools:ignore="LabelFor,TextFields,SpeakableTextPresentCheck" />

    <EditText
        android:id="@+id/numberEditText1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:autofillHints=""
        android:ems="10"
        android:hint="Enter Username"
        android:inputType="textPersonName"
        android:minHeight="48dp"
        android:text=""
        app:layout_constraintBottom_toTopOf="@+id/numberEditText2"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.914"
        tools:ignore="LabelFor,TextFields,SpeakableTextPresentCheck" />

    <EditText
        android:id="@+id/numberEditText2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="76dp"
        android:autofillHints=""
        android:ems="10"
        android:hint="Enter Age"
        android:inputType="phone"
        android:minHeight="48dp"
        android:text=""
        app:layout_constraintBottom_toTopOf="@+id/numberEditText4"
        app:layout_constraintEnd_toEndOf="@+id/numberEditText1"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="@+id/numberEditText1"
        tools:ignore="LabelFor,TextFields,SpeakableTextPresentCheck" />

    <Button
        android:id="@+id/buttonSubmit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="36dp"
        android:onClick="onSubmitClicked"
        android:text="Submit"
        app:layout_constraintEnd_toEndOf="@+id/numberEditText4"
        app:layout_constraintHorizontal_bias="0.504"
        app:layout_constraintStart_toStartOf="@+id/numberEditText4"
        app:layout_constraintTop_toBottomOf="@+id/numberEditText4" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

## MainActivity.java:
```
package com.example.application;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {
    EditText editTextName, editTextAge, editTextEmail, editTextPhone;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editTextName = findViewById(R.id.numberEditText1);
        editTextAge = findViewById(R.id.numberEditText2);
        editTextEmail = findViewById(R.id.numberEditText3);
        editTextPhone = findViewById(R.id.numberEditText4);

    }
    public void onSubmitClicked(View view) {
        String name = editTextName.getText().toString();
        String age = editTextAge.getText().toString();
        String email = editTextEmail.getText().toString();
        String phone = editTextPhone.getText().toString();

        Intent intent = new Intent(this, MainActivity2.class);
        intent.putExtra("name", name);
        intent.putExtra("age", age);
        intent.putExtra("email", email);
        intent.putExtra("phone", phone);
        startActivity(intent);
    }
}
```

## activity_main2.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity2">

    <TextView
        android:id="@+id/textViewInfo"
        android:layout_width="369dp"
        android:layout_height="383dp"
        android:layout_gravity="center"
        android:textSize="18sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        android:gravity="center" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

## MainActivity2.java:
```
package com.example.application;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.widget.TextView;

public class MainActivity2 extends AppCompatActivity {
    TextView textViewInfo;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);

        textViewInfo = findViewById(R.id.textViewInfo);

        Intent intent = getIntent();
        String name = intent.getStringExtra("name");
        String age = intent.getStringExtra("age");
        String email = intent.getStringExtra("email");
        String phone = intent.getStringExtra("phone");

        String info = "Name: " + name + "\nAge: " + age + "\nEmail: " + email + "\nPhone: " + phone;
        textViewInfo.setText(info);
    }
}
```

## Output:
![Screenshot (242)](https://github.com/DonBoscoBlaiseA/MAD-Workshop01/assets/140850829/f6152386-0b3f-43ac-8869-a6f3da7a9a94)
![Screenshot (243)](https://github.com/DonBoscoBlaiseA/MAD-Workshop01/assets/140850829/500a29e5-6ef1-4d50-816e-07551e77a489)
![Screenshot (244)](https://github.com/DonBoscoBlaiseA/MAD-Workshop01/assets/140850829/aa15742c-cf11-4677-950e-5e80879e4612)
![Screenshot (245)](https://github.com/DonBoscoBlaiseA/MAD-Workshop01/assets/140850829/6c596db7-0a84-4962-bbff-d37b64ef1f0d)
![Output2 (2)](https://github.com/DonBoscoBlaiseA/MAD-Workshop01/assets/140850829/2057d77f-614b-4f7c-828d-5839a7f671af)
![Output1 (2)](https://github.com/DonBoscoBlaiseA/MAD-Workshop01/assets/140850829/e29cf06b-7998-43c4-8cac-7cc1980e4197)
![Output3 (2)](https://github.com/DonBoscoBlaiseA/MAD-Workshop01/assets/140850829/4d9e51dd-767a-4d79-95fd-2cc5d9b24aff)


## Result:
Thus a Simple Android Application to pass the data between the activities using Intent using Android Studio is developed and executed successfully.
