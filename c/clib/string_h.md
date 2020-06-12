# string.h header

## size_t strlen(const char &#42;str)

str의 길이를 반환 합니다.

```.c
printf("%d",strlen("hello"));
```
```.bash
5
```

## char &#42; strpbrk(const char &#42; str1, const char &#42; str2)
 str1에 str2가 있는지 확인 있으면 str1에서 어디에 있는지 반환 없으면 str2를 반환

```.c
 char  a[]  = "hellow hi";
 char b[] = "w";
 printf(" a = %s  b = %s strpbrk(a,b) = %s\n",a ,b ,  strpbrk(b,a)  );
 printf("%p %p %p\n",&a ,&b ,  strpbrk(a,b)  );
```

```.bash
a = hellow hi  b = w  strpbrk(a,b) = w
0x7ffd1c1bda40 0x7ffd1c1bda30 0x7ffd1c1bda45
```
