# EXPERIMENT 2B :To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.
## NAME :  SHREYESHKAR SEKAR
## REGISTRATION NUMBER :  212224220099


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

Step 1: Start app → show first screen.

Step 2 : User enters a number in the box.

Step 3 :User presses the Factorial button.

Step 4 :Read the number from the box.

Step 5 :Send this number to the second screen using explicit intent.

Step 6: Open the second screen.

Step 7: Second screen receives the number.

Step 8 :Calculate factorial of the number.

Step 9 :Show the factorial result in a TextView.





## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by: SHREYESHKAR SEKAR
Registeration Number :  212224220099
*/
```
MainActivity.java

```package com.example.explicit;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity
{

    EditText numberInput;
    Button factorialBtn;

    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        numberInput = findViewById(R.id.editTextNumber);
        factorialBtn = findViewById(R.id.buttonFactorial);

        factorialBtn.setOnClickListener(new View.OnClickListener()
        {
            @Override
            public void onClick(View v)
            {
                String numStr = numberInput.getText().toString();
                if (!numStr.isEmpty())
                {
                    int number = Integer.parseInt(numStr);
                    Intent intent = new Intent(MainActivity.this, MainActivity2.class);
                    intent.putExtra("number", number);
                    startActivity(intent);
                }
            }
        });
    }
}

```
activity_main.xml

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/editTextNumber"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter a number"
        android:inputType="number"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.486" />

    <Button
        android:id="@+id/buttonFactorial"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Factorial"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editTextNumber"
        app:layout_constraintVertical_bias="0.468" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="312dp"
        android:layout_height="87dp"
        android:text="Explicit Intent"
        android:textColor="#FF5722"
        android:textSize="48sp"
        app:layout_constraintBottom_toTopOf="@+id/editTextNumber"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.494"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.747" />
</androidx.constraintlayout.widget.ConstraintLayout>

```

MainActivity2.java

```
package com.example.explicit;

import android.os.Bundle;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity2 extends AppCompatActivity
{

    TextView resultView;

    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);

        resultView = findViewById(R.id.textViewResult);
        int number = getIntent().getIntExtra("number", 0);
        long fact = factorial(number);
        resultView.setText("Factorial of " + number + " = " + fact);
    }
    private long factorial(int n)
    {
        long result = 1;
        for (int i = 1; i <= n; i++)
        {
            result *= i;
        }
        return result;
    }
}
```
activity_main2.xml

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity2">

    <TextView
        android:id="@+id/textViewResult"
        android:layout_width="231dp"
        android:layout_height="65dp"
        android:text="Result will appear here"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.588" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="325dp"
        android:layout_height="124dp"
        android:text="Explicit Intent"
        android:textColor="#FF5722"
        android:textSize="48sp"
        app:layout_constraintBottom_toTopOf="@+id/textViewResult"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.667" />
</androidx.constraintlayout.widget.ConstraintLayout>
```




## OUTPUT

<img width="1913" height="1035" alt="Screenshot 2026-11-02 090713" src="https://github.com/user-attachments/assets/94b79903-4abf-4827-89ef-a7889d2073af" />

<img width="1917" height="1083" alt="Screenshot 2026-11-02 091819" src="https://github.com/user-attachments/assets/2b60e275-62ca-4b65-ada7-3a85c8049122" />
<img width="1913" height="1161" alt="Screenshot 2026-11-02 091905" src="https://github.com/user-attachments/assets/1fedd2d3-52ba-4f5a-81ee-53471a57d9a7" />
<img width="1917" height="1012" alt="Screenshot 2026-11-02 092006" src="https://github.com/user-attachments/assets/8e33c5ba-54cb-4a6c-b6b5-de1af6a4dc8c" />



<img width="1917" height="987" alt="Screenshot 2026-11-02 092025" src="https://github.com/user-attachments/assets/2a9ea418-f765-4899-b56a-4204d109ac5e" />




## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.
