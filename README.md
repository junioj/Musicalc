# Musicalc

Screenshots:
https://lh3.googleusercontent.com/fD2ntoRN3wHi5jH9q0cvP8oQV7YRlvhuyfqj2KwDQoWCJ-NMG17U5q0L_0JEHxx9LA=w1600-h789-rw
https://lh3.googleusercontent.com/DyXtI39PVXcSTJXhAdOxHYJE5V-8GQSwVPU0Wr2wZ78J7Og9_2FYW2FwXK7KeL-6b1Q=w1600-h789-rw

Published app:
https://play.google.com/store/apps/details?id=com.sagar.calculator

The following are the most important parts of the app's code:

<b>MainActivity.java</b>
```java
package com.example.calculator;

import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;

import android.content.res.Configuration;
import android.media.MediaPlayer;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

import static java.lang.Math.sqrt;

public class MainActivity extends AppCompatActivity {
    private TextView history;
    private TextView result;
    private TextView sign;
    private Double operand1 = null;
    private String pendingOperation = "";
    private static final String STATE_PENDING_OPERATION = "PendingOperation";
    private static final String STATE_OPERAND1 = "Operand1";
    private static final String historyText = "history";
    private static final String resultText = "result";


        /* Attempt to assign values using arrays failed, possibly retry later?
    private EditText[] tArray = new EditText[]{findViewById(R.id.history),(EditText)findViewById(R.id.sign),(EditText)findViewById(R.id.result)};
    private Button[] bArray = new Button[]{findViewById(R.id.b0), findViewById(R.id.b1), findViewById(R.id.b2), findViewById(R.id.b3), findViewById(R.id.b4), findViewById(R.id.b5), findViewById(R.id.b6), findViewById(R.id.b7), findViewById(R.id.b8), findViewById(R.id.b9), findViewById(R.id.dot), findViewById(R.id.equals), findViewById(R.id.plus), findViewById(R.id.minus), findViewById(R.id.times), findViewById(R.id.divide), findViewById(R.id.sqrroot), findViewById(R.id.ln), findViewById(R.id.powof), findViewById(R.id.to2)};
    private ArrayList<EditText> texts = new ArrayList<>();
    private ArrayList<Button> buttons = new ArrayList<>();*/

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        /* for(int i=0;i<=tArray.length;i++){
            texts.add(tArray[i]);
        }
        for(int i=0;i<=bArray.length;i++){
            buttons.add(bArray[i]);
        } */
        history = findViewById(R.id.history);
        sign = findViewById(R.id.sign);
        result = findViewById(R.id.result);
        Button b0 = findViewById(R.id.b0);
        Button b1 = findViewById(R.id.b1);
        Button b2 = findViewById(R.id.b2);
        Button b3 = findViewById(R.id.b3);
        Button b4 = findViewById(R.id.b4);
        Button b5 = findViewById(R.id.b5);
        Button b6 = findViewById(R.id.b6);
        Button b7 = findViewById(R.id.b7);
        Button b8 = findViewById(R.id.b8);
        Button b9 = findViewById(R.id.b9);
        Button dot = findViewById(R.id.dot);
        Button neg = findViewById(R.id.neg);

        Button equals = findViewById(R.id.equals);
        Button plus = findViewById(R.id.plus);
        Button minus = findViewById(R.id.minus);
        Button times = findViewById(R.id.times);
        Button divide = findViewById(R.id.divide);
        Button sqrroot = findViewById(R.id.sqrroot);
        Button clr = findViewById(R.id.clr);
        /*previously in landscape: Button powof = findViewById(R.id.powof);
        Button to2 = findViewById(R.id.to2);*/

        View.OnClickListener clear = new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                history.setText("");
                sign.setText("");
                result.setText("");
                operand1 = null;
                pendingOperation = "";
            }
        };
        clr.setOnClickListener(clear);

        final MediaPlayer C = MediaPlayer.create(this, R.raw.c);
        final MediaPlayer D = MediaPlayer.create(this, R.raw.d);
        final MediaPlayer E = MediaPlayer.create(this, R.raw.e);
        final MediaPlayer F = MediaPlayer.create(this, R.raw.f);
        final MediaPlayer G = MediaPlayer.create(this, R.raw.g);
        final MediaPlayer A = MediaPlayer.create(this, R.raw.a);
        final MediaPlayer B = MediaPlayer.create(this, R.raw.b);
        final MediaPlayer C2 = MediaPlayer.create(this, R.raw.c2);

        View.OnClickListener c = new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Button b = (Button) v;
                C.start();
                result.append(b.getText().toString());
            }
        };

        View.OnClickListener d = new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Button b = (Button) v;
                D.start();
                result.append(b.getText().toString());
            }
        };

        View.OnClickListener e = new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Button b = (Button) v;
                E.start();
                result.append(b.getText().toString());
            }
        };

        View.OnClickListener f = new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Button b = (Button) v;
                F.start();
                result.append(b.getText().toString());
            }
        };

        View.OnClickListener g = new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Button b = (Button) v;
                G.start();
                result.append(b.getText().toString());
            }
        };

        View.OnClickListener a = new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Button b = (Button) v;
                A.start();
                result.append(b.getText().toString());
            }
        };

        View.OnClickListener b = new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Button b = (Button) v;
                B.start();
                result.append(b.getText().toString());
            }
        };

        View.OnClickListener c2 = new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Button b = (Button) v;
                C2.start();
                result.append(b.getText().toString());
            }
        };

        b1.setOnClickListener(b);
        b2.setOnClickListener(c2);
        b4.setOnClickListener(f);
        b5.setOnClickListener(g);
        b6.setOnClickListener(a);
        b7.setOnClickListener(c);
        b8.setOnClickListener(d);
        b9.setOnClickListener(e);

        View.OnClickListener negv = new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                result.append("-");
            }
        };
        neg.setOnClickListener(negv);

        View.OnClickListener listener = new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Button b = (Button) v;
                result.append(b.getText().toString());
            }
        };
        /*for(int i=0;i<=10;i++){
            buttons.get(i).setOnClickListener(listener);
        }*/
        b0.setOnClickListener(listener);
        b3.setOnClickListener(listener);
        dot.setOnClickListener(listener);

        View.OnClickListener opListener = new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Button b = (Button) v;
                String op = b.getText().toString();
                String value = result.getText().toString();
                try {
                    Double doubleValue = Double.valueOf(value);
                    performOperation(doubleValue, op);
                } catch (NumberFormatException e) {
                    result.setText("");
                }
                /*if (value.length() != 0) {
                    performOperation(value, op);
                }*/
                pendingOperation = op;
                sign.setText(pendingOperation);
            }
        };
        equals.setOnClickListener(opListener);
        plus.setOnClickListener(opListener);
        minus.setOnClickListener(opListener);
        times.setOnClickListener(opListener);
        divide.setOnClickListener(opListener);
        sqrroot.setOnClickListener(opListener);

        /* powof.setOnClickListener(opListener);
        to2.setOnClickListener(opListener); */

    }

    @Override
    protected void onSaveInstanceState(@NonNull Bundle outState) {
        outState.putString(STATE_PENDING_OPERATION, pendingOperation);
        outState.putString(resultText, result.getText().toString());
        outState.putString(historyText, history.getText().toString());
        if (operand1 != null) {
            outState.putDouble(STATE_OPERAND1, operand1);
        }
        super.onSaveInstanceState(outState);
    }

    @Override
    protected void onRestoreInstanceState(@NonNull Bundle savedInstanceState) {
        super.onRestoreInstanceState(savedInstanceState);
        pendingOperation = savedInstanceState.getString(STATE_PENDING_OPERATION);
        operand1 = savedInstanceState.getDouble(STATE_OPERAND1);
        sign.setText(pendingOperation);
        history.setText(savedInstanceState.getString(historyText));
        result.setText(savedInstanceState.getString(resultText));
    }

    private void performOperation(Double value, String operation) {
        if (null == operand1) {
            operand1 = value;
        } else {
            if (pendingOperation.equals("=")) {
                pendingOperation = operation;
            }
            switch (pendingOperation) {
                case "=":
                    operand1 = value;
                    break;
                case "÷":
                    if (value == 0) {
                        operand1 = 0.0;
                    } else {
                        operand1 /= value;
                    }
                    break;
                case "×":
                    operand1 *= value;
                    break;
                case "-":
                    operand1 -= value;
                    break;
                case "+":
                    operand1 += value;
                    break;
                case "ln":
                    operand1 = Math.log(value);
                case "√":
                    operand1 = sqrt(value);
            }
        }

        history.setText(operand1.toString());
        result.setText("");

    }

}
```

<b>activity_main.xml</b> (Portrait, constraint layout)
``` xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#FFC107"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/sign"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:layout_marginStart="16dp"
        android:ems="10"
        android:inputType="textPersonName"
        android:textSize="40sp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/history" />

    <TextView
        android:id="@+id/result"
        android:layout_width="0dp"
        android:layout_height="50dp"
        android:layout_marginStart="16dp"
        android:layout_marginEnd="16dp"
        android:ems="10"
        android:inputType="numberSigned|numberDecimal"
        android:textSize="40sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/sign"
        app:layout_constraintTop_toBottomOf="@+id/history" />

    <Button
        android:id="@+id/b8"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:layout_marginTop="32dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="8"
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/result" />

    <Button
        android:id="@+id/times"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="×"
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintStart_toEndOf="@+id/minus"
        app:layout_constraintTop_toBottomOf="@+id/b0"
        tools:layout_editor_absoluteY="432dp" />

    <Button
        android:id="@+id/clr"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="@string/clr"
        android:textAllCaps="false"
        android:textColor="#9C27B0"
        android:textSize="60sp"
        android:typeface="monospace"
        app:layout_constraintStart_toStartOf="@+id/b9"
        app:layout_constraintTop_toBottomOf="@+id/minus" />

    <Button
        android:id="@+id/sqrroot"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="√"
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintStart_toEndOf="@+id/b7"
        app:layout_constraintTop_toBottomOf="@+id/minus" />

    <Button
        android:id="@+id/b3"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="3"
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintStart_toEndOf="@+id/b2"
        app:layout_constraintTop_toTopOf="@+id/b2" />

    <Button
        android:id="@+id/divide"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="÷"
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintStart_toStartOf="@+id/b7"
        app:layout_constraintTop_toBottomOf="@+id/minus" />

    <Button
        android:id="@+id/minus"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="-"
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintStart_toEndOf="@+id/plus"
        app:layout_constraintTop_toBottomOf="@+id/b0"
        tools:layout_editor_absoluteY="432dp" />

    <Button
        android:id="@+id/plus"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="+"
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintStart_toStartOf="@+id/b1"
        app:layout_constraintTop_toBottomOf="@+id/b0"
        tools:layout_editor_absoluteY="432dp" />

    <Button
        android:id="@+id/b6"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="6"
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintStart_toEndOf="@+id/b5"
        app:layout_constraintTop_toTopOf="@+id/b5" />

    <Button
        android:id="@+id/b0"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="0"
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintStart_toStartOf="@+id/b1"
        app:layout_constraintTop_toBottomOf="@+id/b2" />

    <Button
        android:id="@+id/dot"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="."
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintStart_toEndOf="@+id/b0"
        app:layout_constraintTop_toBottomOf="@+id/b2"
        tools:layout_editor_absoluteX="156dp" />

    <Button
        android:id="@+id/equals"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="="
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintStart_toEndOf="@+id/dot"
        app:layout_constraintTop_toBottomOf="@+id/b2" />

    <Button
        android:id="@+id/b7"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="7"
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintEnd_toStartOf="@+id/b8"
        app:layout_constraintTop_toTopOf="@+id/b8" />

    <Button
        android:id="@+id/b2"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="2"
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintStart_toEndOf="@+id/b1"
        app:layout_constraintTop_toTopOf="@+id/b1" />

    <Button
        android:id="@+id/b1"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="1"
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintStart_toStartOf="@+id/b4"
        app:layout_constraintTop_toBottomOf="@+id/b4" />

    <Button
        android:id="@+id/b5"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="5"
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintStart_toEndOf="@+id/b4"
        app:layout_constraintTop_toTopOf="@+id/b4" />

    <Button
        android:id="@+id/b9"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="9"
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintStart_toEndOf="@+id/b8"
        app:layout_constraintTop_toTopOf="@+id/b8" />

    <TextView
        android:id="@+id/history"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="16dp"
        android:ems="10"
        android:inputType="textPersonName"
        android:textSize="40sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/b4"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="70dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="4"
        android:textColor="#9C27B0"
        android:textSize="60sp"
        app:layout_constraintStart_toStartOf="@+id/b7"
        app:layout_constraintTop_toBottomOf="@+id/b7" />

    <Button
        android:id="@+id/neg"
        android:layout_width="100dp"
        android:layout_height="40dp"
        android:text="neg"
        android:textSize="20sp"
        android:background="#CDDC39"
        android:textColor="#9C27B0"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/sqrroot" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

<b>activity_main.xml</b> (Landscape, constraint layout)
``` xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#FFC107"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/clr"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="200dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="clr"
        android:textColor="#9C27B0"
        android:textSize="40sp"
        android:typeface="monospace"
        app:layout_constraintStart_toEndOf="@+id/equals"
        app:layout_constraintTop_toBottomOf="@+id/b3" />

    <TextView
        android:id="@+id/result"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginEnd="16dp"
        android:layout_marginStart="16dp"
        android:ems="10"
        android:inputType="numberDecimal"
        android:textSize="40sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="@+id/guideline4"
        app:layout_constraintTop_toBottomOf="@+id/history" />

    <TextView
        android:id="@+id/sign"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginEnd="16dp"
        android:ems="10"
        android:inputType="textPersonName"
        android:textSize="40sp"
        app:layout_constraintEnd_toStartOf="@+id/guideline4"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/history" />

    <Button
        android:id="@+id/b8"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"

        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="8"
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintEnd_toStartOf="@+id/b9"
        app:layout_constraintTop_toTopOf="@+id/b9" />

    <Button
        android:id="@+id/times"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="×"
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintStart_toEndOf="@+id/b6"
        app:layout_constraintTop_toTopOf="@+id/b6" />

    <Button
        android:id="@+id/sqrroot"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="√"
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintStart_toEndOf="@+id/b3"
        app:layout_constraintTop_toTopOf="@+id/b3" />

    <Button
        android:id="@+id/b3"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="3"
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintStart_toEndOf="@+id/b2"
        app:layout_constraintTop_toTopOf="@+id/b2" />

    <Button
        android:id="@+id/divide"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="÷"
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintStart_toEndOf="@+id/times"
        app:layout_constraintTop_toTopOf="@+id/times" />

    <Button
        android:id="@+id/minus"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="-"
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintStart_toEndOf="@+id/plus"
        app:layout_constraintTop_toTopOf="@+id/b7" />

    <Button
        android:id="@+id/plus"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="+"
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintStart_toEndOf="@+id/b9"
        app:layout_constraintTop_toTopOf="@+id/b7" />

    <Button
        android:id="@+id/b6"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="6"
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintStart_toEndOf="@+id/b5"
        app:layout_constraintTop_toTopOf="@+id/b5" />

    <Button
        android:id="@+id/b0"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="0"
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintStart_toStartOf="@+id/b1"
        app:layout_constraintTop_toBottomOf="@+id/b2" />

    <Button
        android:id="@+id/dot"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="."
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintStart_toEndOf="@+id/b0"
        app:layout_constraintTop_toBottomOf="@+id/b2" />

    <Button
        android:id="@+id/equals"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="="
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintStart_toEndOf="@+id/dot"
        app:layout_constraintTop_toBottomOf="@+id/b2" />

    <Button
        android:id="@+id/b7"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="7"
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintEnd_toStartOf="@+id/b8"
        app:layout_constraintTop_toTopOf="@+id/b8" />

    <Button
        android:id="@+id/b2"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="2"
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintStart_toEndOf="@+id/b1"
        app:layout_constraintTop_toTopOf="@+id/b1" />

    <Button
        android:id="@+id/b1"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="1"
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintStart_toStartOf="@+id/b4"
        app:layout_constraintTop_toBottomOf="@+id/b4" />

    <Button
        android:id="@+id/b5"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="5"
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintStart_toEndOf="@+id/b4"
        app:layout_constraintTop_toTopOf="@+id/b4" />

    <Button
        android:id="@+id/b9"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:layout_marginTop="24dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="9"
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintEnd_toEndOf="parent"

        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/result" />

    <TextView
        android:id="@+id/history"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="16dp"
        android:ems="10"
        android:inputType="textPersonName"
        android:textSize="40sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/b4"
        style="@style/Widget.AppCompat.Button.Colored"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="4"
        android:textColor="#9C27B0"
        android:textSize="40sp"
        app:layout_constraintStart_toStartOf="@+id/b7"
        app:layout_constraintTop_toBottomOf="@+id/b7" />

    <androidx.constraintlayout.widget.Guideline
        android:id="@+id/guideline4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        app:layout_constraintGuide_begin="146dp" />

    <Button
        android:id="@+id/neg"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:background="#CDDC39"
        android:fontFamily="sans-serif-smallcaps"
        android:text="neg"
        android:textColor="#9C27B0"
        android:textSize="30sp"
        app:layout_constraintStart_toEndOf="@+id/sqrroot"
        app:layout_constraintTop_toBottomOf="@+id/divide" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
