# Kotlin & Android Notes

## Coroutine

1. Job will stop execution of remaining child jobs if one of it’s child throws exception while SupervisorJob doesn’t affect other remaining child thread.
2. Use CoroutineExceptionHandler as lambda handler to catch exception in coroutine and it’s should be placed at the root launch keyword.
3. To implement synchronized java thread in kotlin when using coroutine, use mutex.
   Example:

   ```kotlin
   suspend fun synchronizeCoroutine() {
       mutex.withLock {
           // Execute Coroutine Job
       }
   }
   ```

## Work Manager

1. WorkManager is an Android library that runs deferrable background work when the work’s constraints are satisfied.
2. WorkManager is intended for tasks that require a guarantee that the system will run them even if the app exits.

## Notification

1. Notification Importance is set on notification channel while priority is set on notification, it distinguish by android version supported it.

## Notes about Android Component:

1. ContentProvider: Implementation class from android that enables an application to publicly expose its interface to access data storage (sqlite database) for other application to access it. It associates with URI that contains the authorities defined from application that owns the ContentProvider.
2. CursorLoader: We use this in order to create a cursor to load sqlite data at background thread. By using content provider we can create a new instance of CursorLoader that receives specificied “content://“ URI in the constructor.
3. StrictMode class from Android is use to detect undesired work like IO operations on main thread (Thread Policy), it can show warning or even throw exception.
4. By default, calling Handler in main thread is equals to Handler(Looper.getMainLooper())

## Useful Code

```kotlin
fun Context.convertDpToPx(dp: Float): Float {
    return TypedValue.applyDimension(
            TypedValue.COMPLEX_UNIT_DIP,
            dp,
            this.resources.displayMetrics
    )
}
```

## Important References

1. <https://medium.com/androiddevelopers/exceptions-in-coroutines-ce8da1ec060c>
2. <https://medium.com/androiddevelopers/dagger-code-generation-cheat-sheets-6b4fa2da4e7a>
3. <https://openclassrooms.com/en/courses/4561586-manage-your-data-to-have-a-100-offline-android-app/5770976-expose-your-data-with-a-contentprovider>
