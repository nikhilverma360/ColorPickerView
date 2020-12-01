@@ -1,2 +1,82 @@
# ColorPickerView
Color Picker Library For Andriod
[![](https://jitpack.io/v/nikhilverma360/ColorPickerView.svg)](https://jitpack.io/#nikhilverma360/ColorPickerView)
## Brief introduction.
The following features are mainly implemented:
- Select the color on the disc color selection picture and listen in real time
- You can set a color selection to indicate the picture, follow the touch position, indicate the selected color, and, in the example, a white ring
- You can set your own color selection pictures (currently only round pictures are supported)

## Use effects
Let's start by looking at how to use it: <br>
![](http://i.imgur.com/oIM1je2.gif)

## Use the example
### Import the library in your project
Add in the build.gradle of the project:
```java
allprojects {
		repositories {
			...
			maven { url "https://jitpack.io" }
		}
	}
```
Add dependencies to module's build.gradle:
```java
dependencies {
	        implementation 'com.github.nikhilverma360:ColorPickerView:v1'
	}
```
### xml
```java
<RelativeLayout
        android:id="@+id/rl_picker"
        android:layout_below="@+id/img_color"
        android:layout_marginTop="30dp"
        android:layout_centerHorizontal="true"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content">

        <colorpicker.nikhilverma360.com.colorpicker.ColorPickerView
            android:id="@+id/color_picker"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"/>


        <ImageView
            android:id="@+id/img_picker"
            android:layout_centerInParent="true"
            android:src="@mipmap/color_picker"
            android:layout_width="25dp"
            android:layout_height="25dp" />

    </RelativeLayout>
```
### Color selection code
```java
   private void initRgbPicker() {
        colorPickerView = (ColorPickerView) findViewById(R.id.color_picker);
        colorPickerView.setImgPicker(MainActivity.this, img_picker, 25); //The last parameter is that the color indicates the size of the circle (dp)
        colorPickerView.setColorChangedListener(new ColorPickerView.onColorChangedListener() {
            @Override
            public void colorChanged(int red, int blue, int green) {
                img_color.setColorFilter(Color.argb(255, red, green, blue));
            }

            @Override
            public void stopColorChanged(int red, int blue, int green) {

            }
        });
    }
```
#### API that is publicly available
```java
 public void setImgPicker(final Context context, final ImageView imgPicker, final int pickerViewWidth)

 public void setImgResource(final int imgResource)

 public void setColorChangedListener(onColorChangedListener colorChangedListener)
```
#### Thankyou
Contributions are welcome !