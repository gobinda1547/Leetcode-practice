### Problem name
/* enter problem name */


### Solution approch
/* enter solution */


### Code
```kotlin
/**
* It is possible that this function is being invoked when the activity or fragment
* is destroyed already, In that case the binding object will be null. So we have to
* handle this using try-catch block. Also it's a good practice to destroy previous
* native ad while showing the new one to ignore memory leak.
*/
private fun showNativeAdInTemplateView(mNativeAd: NativeAd) {
    try {
        binding.nativeAdTemplateView.destroyNativeAd()
        binding.nativeAdTemplateView.applyStyles(getStyleForNativeAd())
        binding.nativeAdTemplateView.setNativeAd(mNativeAd)
    } catch (e: Exception) {
        e.printStackTrace()
    }
}
```


### Time complexity
/* enter time complexity */


### Space complexity
/* enter space complexity */
