# Android Development.

**Directory :** E:\AndroidDevelopment\Notes\Android-Programming

## Class 1 (Data Types)

The data type is a set of values. The data type is a pre-defined set of values.

- int: 1,2,3,100.-5
- float: 1.5,2.6,-5.7
- double:  Double is a 64-bit floating data type. So there is more space to store value.  EX: 4.7984379297934
- boolean: true, false
- String: "Hello", "world"
- Array: .........

### Variables _______________

Variables are like a box. You can put a single value in it. You must provide a name for a variable. In java, If we want to define a variable, we have to provide a Data Type and Name for it.

```java
DataType variableName;
```

When we declare a variable, the store makes a space for it. 



## Class 2 (Data Types)

In MainActivity, There is a bundle method called the onCreate bundle method. In the android lifecycle, it was called first. 

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
	super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
}
```

If we define a variable inside the onCreate method. We can't use it outside of it. If we need to define a global variable, we have to define a variable outside of it.

**We can define multiple variables like this.**

```java
int int1,int2,int3;
```

> If we add a String with a number, the result will be a string. 



## Class 3 (User Input)

If we want to work with user input we have to make an input box for a user.

```xml
<EditText
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Enter your message..."
    android:inputType="textPersonName"/>
```

**We can use java like this to get data from the input box.**

```java
String editTextData;
editTextData = editText.getText().toString();
```



## Class 4 (User Input)

When we get data from the user data comes in string format. That's why if we want to work with integer input we have to convert this value to an integer/float/double.

<img src="images\class4.PNG" style="zoom:%25;" />

**We can convert types like this.**

```java
String userInput = editText.getText().toString();
// Converting into numeric ...
int data = Integer.parseInt(userInput);
float data = Float.parseFloat(userInput);
double data = Double.parseDouble(userInput);

// Benifit percentage value
double percenge = profit/buyPrice*100;
```



## Class 5 (Exploring Logcat)

- **Invalided and Restart**:  If you see your project code all are invalid and a red underline under your code you can simply do these steps. 

  > //This command will restart your project.
  >
  > File > Invalidate Caches and Restart > Invalidate and Restart.

- **Clean Project**

  >  // This command clean your previous build-cache files.
  >
  > Build > Clean Project 
  >
  > Build > Rebuild Project  // After cleaning we should rebuild your project.

- **Build Error**

  If your project build failed, Check your bottom navbar and there is an option called Build. You can check and fix your problem.

- **Runtime Error**

  When your project builds successfully but your app crashes, You can check **logcat**. 

  Logcat has different options like :

  - Verbose  // It shows the activity on our phones.
  - Debug  //
  - Info
  - Warn
  - Error // It shows only errors
  - Assert 

  When you open the logcat tab, It shows us lots of errors. All of these are not our application errors. To find the error, check the logcat **Caused by** section. If you understand your problem, Great. If you don't understand your problem search for it on google.
  
  
## Class 13 (Error on Input) 
We must always remember, users can be wrong with our apps. So always make your application secure 

for unexpected input. Now, how do you save your apps?

```java
String inputedVal = editText.getText().toString();
if(inputedVal.lenght() > 0){
    // CODE GOES HERE .....
}else{
    // If the input value is equel to 0 
}
```
> Always try to visualize what will go on.

  

## Class 20 (Alert Dialog Box)

Alert Dialog Box is like a popup.  It has different benefits. For example, you can use it to prevent application exit, You can use it for show loading or etc. Now the question is how to use it.

<img src="images\alertDialog.gif" style="zoom:25%;" />



### Alert dialog code

```Java
new AlertDialog.Builder(MainActivity.this)
    .setTitle("Alert title")
    .setMessage("Alert message goes here...")
    .setCancelable(false)
    .setNegativeButton("NO",new DialogInterface.OnClickListener(){
        @Override
        public void onClick(DialogInterface dialogInterface, int i) {
			// No button code block.
        }
    })
    .setPositiveButton("Yes", new DialogInterface.OnClickListener() {
        @Override
        public void onClick(DialogInterface dialogInterface, int i) {
           // Yes button code block.        
        }
    })
    .setNeutralButton("Can't Say", new DialogInterface.OnClickListener() {
        @Override
        public void onClick(DialogInterface dialogInterface, int i) {
            // Left side button code block.            
        }
    })
    .show();
```



### Alert dialog code explain.

- `.setTitle("Alert title")` Alert title goes here.

- `.setMessage("Alert message goes here...")` Alert message goes here.

- `.setCancelable(false)` if cancelable is false, you can't cancel it. 

- `.setNegativeButton` it's a dialog **No** button.

- `.setPositiveButton` it's a dialog **Yes** button.

- `.setNeutralButton` it's a dialog left-side button.



## Class 21 (Control app exit)

When the user will press the back button, we need to show a dialog box. That will helps a user to take a decision again. Since the alert box come after pressing the back button so to listen back button clicked you need to add an overridden method called `onBackPressed()`

Add the `onBackPressed()` overridden method under `onCreate()` method.

```java
@Override
public void onBackPressed(){
	// Alert code goes here...
}
```

To cancel the dialog box put `dialogInterface.cancel();` inside  `.setNegativeButton()` method.

```java
// It's a part of the Alert Dialog method ...
.setNegativeButton("No", new DialogInterface.OnClickListener() {
	@Override
	public void onClick(DialogInterface dialogInterface, int i) {
		dialogInterface.cancel();
    }
})
```

To exit from the application you simply put `finish()` inside  `.setPositiveButton()` method.

```java
// It's a part of the Alert Dialog method ...
.setPositiveButton("Yes", new DialogInterface.OnClickListener() {
	@Override
	public void onClick(DialogInterface dialogInterface, int i) {
		finish();
	}
})
```



## Class 22 (Check Network Info)

If you are working with the internet you must check whether users are connected or not. You can check it by using a simple function ``

First, take permission from `AndroidManifest.xml` 

```xml
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
```

Then, check the internet form the java file.

```java
ConnectivityManager connectivityManager = (ConnectivityManager)getSystemService(Context.CONNECTIVITY_SERVICE);
NetworkInfo networkInfo = connectivityManager.getActiveNetworkInfo();

if(networkInfo != null && networkInfo.isConnectedOrConnecting()){
	// Network is connected code...
}else{
	//Network is not connected code...
}
```



## Class 23 (Play Audio Files)

In this class, we will learn about how can we play an audio file from the application or the internet. To put an audio file inside your application you must create an empty folder for it.

So, Create a `raw` folder inside `res` and paste your music inside it.

<img src="images\folder_structure.png" style="zoom:25%;" />

Now, to play the music you need to take help from a class called `MediaPlayer`

```java
// Initialize media player
MediaPlayer mediaPlayer;
```

After initializing, play the music when the button clicks.

```java
buttonOffline.setOnClickListener(new View.OnClickListener() {
	@Override
	public void onClick(View view) {
		mediaPlayer = MediaPlayer.create(MainActivity.this,R.raw.birthday);
		mediaPlayer.start();
    }
});
```

In media player class has some methods that you can use on your project buttons.

```java
mediaPlayer.stop();
mediaPlayer.pause();
mediaPlayer.reset();
mediaPlayer.start();
```

**To play Online Music** you can follow those codes.

```
buttonOnline.setOnClickListener(new View.OnClickListener() {
	@Override
	public void onClick(View view) {
       mediaPlayer.setDataSource("https://example.com/music_file.mp3");
       mediaPlayer.prepare();
       mediaPlayer.start();
    }
});
```

But there is a problem. If you click the multiple-time play button the music will play multiple times at a single time. So first check and then play.

```java
buttonOffline.setOnClickListener(new View.OnClickListener() {
	@Override
	public void onClick(View view) {
        // FIRST RELEASE AND THEN CREATE INSTANCE
		if(mediaPlayer!=null) mediaPlayer.release();
		mediaPlayer = new MediaPlayer(); 
		try {
			mediaPlayer.setDataSource("https://example.com/example.mp3");
			mediaPlayer.prepare(); //Important
			mediaPlayer.start();
		catch(IOException e){
			 e.printStackTrace();
		}
	}
});
```

> For hosting you can't use **Google Drive**.  Because they don't support it. 



## Class 26 (User defined method)

```java
// Syntex
privet returnType methodName(){
    // CODE GOES HERE ...
}
```

The return type can be a **String, int, or something.** 

```java
privet String schollCloseing(){
    return something.
}
```

If we want no return from our method. We can simply use the return type **void**.

We also can use parameters in this user-defined function. 

```java
public int Addition(int a, int b){
    int sum = a+b;
    return sum;
}
```



## Class 35 (Array)

A variable can store a single value. If you want to store multiple values in an array you can simply use **Array**. The array can store multiple values at a time. How you can declare an array?

```java
// Declaration and Insertion.
String[] myArray = {"Hello","Bangladesh","India"};

// Access value.
myArray[0];
```



## Class 36 (Shared preferences)

If you want to save some data in our application without a database we can simply use **Shared Preferences**. This functionality is very useful. We can use it as a database. We can use it as a First Time Application Open Tester or many more.

```java
// Decleration
SharedPreferences sharedPreferences;
SharedPreferences.Editor editor;

// Initializetion
sharedPreferences = getSharedPreferences("TrackFirstOpen",MODE_PRIVATE);
editor = sharedPreferences.edit();

//Set Value;
editor.putString("Key","Value");
editor.apply();
```

**MODE_PRIVATE** means you make it private so other applications can't access this value.



Now it's time to get data from our Shared preferences.

```java
//Get Shared preferences value.
sharedPreferences.getString("Key","Default Value");
```

> If you want to get the string on other activities, First you have to do Declaration and Initialization shared Preferences.  
