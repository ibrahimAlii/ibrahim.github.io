## Introduction:-

Jetpack compose is an unusual new API from google to help us semplify and accelerate the UI developement on Android.
It's got shipped in library form which add more flexbility for change making and solve problems.


## Why we want to secure our UI?

Spying on your user's screens or taking screenshoots that contain sensitive data will make your users untrust your product and may uninstall it forever.

So protecting your application from such things will be a mandatory thing for you to prevent user's screen from getting screenshooted (Manual or automatic) or screen recorded ([Media Projection](https://developer.android.com/reference/android/media/projection/MediaProjection))

## How we secure UI in Android without Jetpack Compose?

[`FLAG_SECURE`](https://developer.android.com/reference/android/view/WindowManager.LayoutParams#FLAG_SECURE) Window flag: treat the content of the window as secure, preventing it from appearing in screenshots or from being viewed on non-secure displays.

And adding that flag is pretty easy:-

.SecureActivity.kt
```Kotlin
override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        
        window.setFlags(WindowManager.LayoutParams.FLAG_SECURE,
                         WindowManager.LayoutParams.FLAG_SECURE);
                         
        setContentView(R.layout.activity_main)
            
    }
```

**But** This won't secure all windows in your activities. 
**What that mean?**

Well any pop-up window in your activity still not secure, like:- `Dialog`, `Spinner`, `AutoCompleteTextView`, `ShareActionProvider`, etc

There are tricky ways to secure these pop-up windows too but it's tricky as I said!


## Jetpack Compose and it's Policy

Thankfully to Jetpack Compose. 

If [`FLAG_SECURE`](https://developer.android.com/reference/android/view/WindowManager.LayoutParams#FLAG_SECURE) is added under activity/fragment that is displaying composable then 
all composables got the `FLAG_SECURE` effect too.

This work fine on all pop-up window too unless `Dialog` you can set a manual `flag` when you creating it!
