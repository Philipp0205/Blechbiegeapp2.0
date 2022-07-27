# 9 Best Practices to Handle Exceptions in Java
Source: https://stackify.com/best-practices-exceptions-java/

## 8. Don’t Log and Throw

The additional messages also don’t add any information.

As explained in best practice #4, the exception message should describe the exceptional event. And the stack trace tells you in which class, method, and line the exception was thrown.

If you need to add additional information, you should catch the exception and wrap it in a custom one. But make sure to follow best practice number 9.

It might feel intuitive to log an exception when it occurred and then rethrow it so that the caller can handle it appropriately. But it will write multiple error messages for the same exception.

## 4. Throw Exceptions With Descriptive Messages