# Profiling using YourKit in Java 
در این تمرین با استفاده از بررسی منابع استفاده شده توسط هر تابع، سعی میکنیم کد را بهینه کنیم. 

پس از انجام مراحل موجود در دستورکار، برنامه را اجرا میکنیم. خروجی به صورت زیر است.

![Image1: output of Flame Graph for memory allocation](resources/image1.png)

![Image2: output of Memory Allocation for functions](resources/image.png)


![Image3: output of CPU Time for functions](resources/image2.png)

![Time for each indivisual thread](resources/image3.png)

![Methods list with the time they own](resources/image4.png)

## پرسش اول

همانطور که در تصاویر دوم و سوم مشخص است، تابع temp بیشترین مقدار پردازنده و مموری را استفاده میکند. 

این تابع تاثیری در عملکرد برنامه ندارد، در نتیجه میتوان آن را کامل حذف کرد. اما برای آنکه کد را بهینه کنیم، به صورت زیر عمل میکنیم. 
میدانیم که استفاده از ArrayList با طول نامشخص بهینه نیست. در نتیجه تا جایی که ممکن است باید از آرایه های با طول ثابت استفاده کنیم. 

همچنین میتوان دو حلقه تودرتو را تبدیل به یک حلقه کرد. البته تاثیر زیادی در پرفورمنس ندارد و تغییر عمده برای تبدیل اری لیست به آرایه عادی است. 




```java
public static void temp1(){
        int [] a = new int[10000*20000];
        for (int i = 0; i < 10000 * 20000; i++) {
            int j = i % 20000;
            int sum = (i / 20000) + j;
            a[i] = sum;
        }
    }
```

حال خروجی های پروفایلر را بررسی میکنیم و تغییر کاملا مشهود است. 

![Performance after changing code](resources/image5.png)

همانطور که در تصویر بالا مشهود است، منابع کمتری پس از اعمال این تغییر استفاده شده است. 

