
## 📚 Delphi Android Tips:

Welcome to **Delphi Android Tips**, a plain-text guide with essential tips for building and improving Android apps using Delphi. This guide includes tips based on our previous discussions to help you solve specific issues.

---

<details>
<summary>Tip1: Fixing Stretched Splash Images (After using the ArtWork generator from Delphi IDE) 🌟</summary>


 **Problem:**  
 If you've ever generated Android splash screen images using Delphi IDE and noticed they appear stretched,  
 here's a simple way to fix that and ensure your splash image is always centered without distortion.

 **Solution:**  
 To fix the stretched splash images, follow these steps:

==> **Create a custom splash image definition:**

After building your project, go to the following paths where the splash screen files are generated:
   ```xml
      if your target android system is 64bit:
      <YourProjectDirectory>\Android64\Debug\<YourProjectName>\res\drawable
      <YourProjectDirectory>\Android64\Debug\<YourProjectName>\res\drawable-anydpi-v21  
        or
      <YourProjectDirectory>\Android\Debug\<YourProjectName>\res\drawable  
      <YourProjectDirectory>\Android\Debug\<YourProjectName>\res\drawable-anydpi-v21   
   ```
  
1. **Copy both files** **`splash_image_def.xml | splash_image_def-v21.xml`** from this folder and paste
it into a new directory in your project (e.g., **`<YourProjectDirectory>\res\theme`**).  
  
   1.2  **Open both files in Delphi IDE** and add the following line inside each file:  
      ```pascal
      android:scaleType="centerInside"
      ```
   1.3 **Deployment:**  
         Go to Project > Deployment in Delphi IDE.
      Select all configurations for your target system.
      Click on the column header "Local Name" to sort the list by name.
      Scroll down, find the default splash xml files, uncheck them, and replace them with your newly edited files.
      Don’t forget to set the remote path for the new files according to the unchecked ones.
       That’s it! **Clean&Rebuild** and deploy your project, and you’ll see your splash image properly centered on all devices without any stretching! 

**Finally,Modified splash_image_def.xml should look like this:**  
```xml
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android" android:opacity="opaque">
  <item android:drawable="@color/splash_background" />
  <item>
      <bitmap
          android:src="@drawable/splash_image"
          android:antialias="true"
          android:dither="true"
          android:filter="true"
          android:gravity="center"
          android:scaleType="centerInside"
          android:tileMode="disabled"/>
  </item>
</layer-list>
```
**Modified splash_image_def-v21.xml should look like this:**  
```xml
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:drawable="@color/splash_background" />
    <item
        android:gravity="center"
        android:scaleType="centerInside"
        android:drawable="@drawable/splash_vector">
    </item>
</layer-list
 ```
  
  
This should solve the stretching issue and provide a visually appealing splash screen for your users.

---

## Closing Notes

We hope this tip helps you improve your Delphi Android app development experience. Stay tuned for more tips!

Happy coding! 🚀



</details>
