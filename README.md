# Ex.No:4 To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

Step 1: Open Android Studio and select File → New → New Project.

Step 2: Enter the application name as ExplicitIntent and click Next.

Step 3: Select the required Minimum SDK and click Next.

Step 4: Select Empty Activity and click Finish.

Step 5: Design the first screen in activity_main.xml with a TextView, EditText, and Button.

Step 6: Create a second Activity, MainActivity2, along with its layout file activity_main2.xml.

Step 7: Design the second screen in activity_main2.xml.

Step 8: Register MainActivity2 in the AndroidManifest.xml file.

Step 9: In MainActivity.java, create an explicit Intent to navigate from MainActivity to MainActivity2.

Step 10: In MainActivity2.java, create an explicit Intent to navigate back to MainActivity.

Step 11: Set the onClick methods for the buttons in the respective XML layouts.

Step 12: Save and run the application.

## PROGRAM:
```
Program to print the text “ExplicitIntent”.
Developed by: HEMAVARSHINI D
Registeration Number : 212225220039
```
## MainActivity.java
```
package com.example.explicit_intent;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Get references to UI elements
        final EditText inputField = findViewById(R.id.input_field);
        Button factorialButton = findViewById(R.id.factorial_button);

        // Set up the "Explicit Intent" button
        factorialButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Get the input number from the text field
                int inputNumber = Integer.parseInt(inputField.getText().toString());

                // Create an Intent to start the FactorialActivity
                Intent explicitIntent = new Intent(MainActivity.this, MainActivity2.class);
                // Pass the input number as an extra
                explicitIntent.putExtra("input_number", inputNumber);

                // Start the FactorialActivity
                startActivity(explicitIntent);
            }
        });
    }


}
```
## MainActivity1.java
```
package com.example.explicit_intent;


import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;
import java.math.BigInteger;
public class MainActivity2 extends AppCompatActivity{
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity2);

        // Get the input number from the Intent extra
        int inputNumber = getIntent().getIntExtra("input_number", 0);

        // Calculate the factorial of the input number using BigInteger
        BigInteger factorial = BigInteger.ONE;
        for (int i = 2; i <= inputNumber; i++) {
            factorial = factorial.multiply(BigInteger.valueOf(i));
        }
        // Display the factorial result in a TextView
        TextView resultTextView = findViewById(R.id.resultText);
        resultTextView.setText(
                "Factorial of " + inputNumber + " is: " + factorial
        );
    }
    public void back(View view) {
        Intent i = new Intent(getApplicationContext(), MainActivity.class);
        startActivity(i);
    }
}

```
## activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/linearLayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#EFF2F4"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/input_field"
        android:layout_width="252dp"
        android:layout_height="48dp"
        android:hint="Enter a number"
        android:inputType="number"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/factorial_button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:backgroundTint="#D26BDA"
        android:text="FIND FACTORIAL"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/input_field" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="261dp"
        android:layout_height="99dp"
        android:text="FACTORIAL FINDER"
        android:textAlignment="center"
        android:textColor="#AE218F"
        android:textSize="34sp"
        android:textStyle="bold|italic"
        app:layout_constraintBottom_toTopOf="@+id/input_field"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.72" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
## activity_main1.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#EFF2F4"
    tools:context=".MainActivity2">

    <TextView
        android:id="@+id/resultText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="The Factorial is : "
        android:textColor="#AE218F"
        android:textSize="34sp"
        android:textStyle="bold|italic"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.496"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.349" />

    <Button
        android:id="@+id/button"
        android:layout_width="122dp"
        android:layout_height="65dp"
        android:backgroundTint="#C362CA"
        android:onClick="back"
        android:text="BACK"
        android:textColorLink="#C85A5A"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/resultText" />

</androidx.constraintlayout.widget.ConstraintLayout>
```




## OUTPUT

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/47607da8-d29c-4242-b7ed-284de1c87483" />


<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b2c3788c-b8ca-4c20-9577-4383dd01fe65" />



## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


