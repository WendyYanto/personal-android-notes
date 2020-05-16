# Kotlin Notes

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

## Infix

Infix is simply use to remove parentheses and dot when calling a function. There's widely used keyword that most of us doesn't realized which is `to`.

```kotlin
//version one
val maps = mapOf(key1 to value1)
//version two
val maps = mapOf("key1".to("value1"))
//to is an extension function to make pair
```

Example:

```kotlin
// normal
fun <T> List<T>.combineWith(List<T> other): List<T> {
    val result = MutableList<T>()
    result.addAll(this)
    result.addAll(other)
    return result
}
//accessing normal version
val list = listOf(1,2,3).combineWith(listOf(4,5,6))

// best
infix fun <T> List<T>.combineWith(List<T> other): List<T> {
    return this + other
}
//accessing best version
val list = listOf(1,2,3) combineWith listOf(4,5,6)
```

## Operator

it add functionality to operator to perform certain jobs.
Example:

```kotlin
public operator fun <T> Collection<T>.plus(elements: Iterable<T>): List<T> {
    if (elements is Collection) {
        val result = ArrayList<T>(this.size + elements.size)
        result.addAll(this)
        result.addAll(elements)
        return result
    } else {
        val result = ArrayList<T>(this)
        result.addAll(elements)
        return result
    }
}
//Usage
val lists = listOf(1,2,3,4) + setOf(5,5,5,5,5,6)
```

## Semantic Validation
Java way
```java
Preconditions.checkArgument(validate(), "error message")
```

Kotlin way
```kotlin
val validate = () -> Boolean
require(validate.invoke()) { "error message" }
```

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
