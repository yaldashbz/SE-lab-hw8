# Profiling using YourKit in Java 
در این تمرین با استفاده از بررسی منابع استفاده شده توسط هر تابع، سعی میکنیم کد را بهینه کنیم. 

پس از انجام مراحل موجود در دستورکار، برنامه را اجرا میکنیم. خروجی به صورت زیر است.

![Image1: output of Flame Graph for memory allocation](resources/image1.png)

![Image2: output of Memory Allocation for functions](resources/image.png)


![Image3: output of CPU Time for functions](resources/image2.png)

## پرسش اول

همانطور که در تصاویر دوم و سوم مشخص است، تابع temp بیشترین مقدار پردازنده و مموری را استفاده میکند. 

این تابع تاثیری در عملکرد برنامه ندارد، در نتیجه میتوان آن را کامل حذف کرد. اما برای آنکه کد را بهینه کنیم، به صورت زیر عمل میکنیم. 