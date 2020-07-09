# c++ builder에서 dll을 만드는법

dll에서 어떤 함수를 실행하기 위해서는 export라는 개념을 사용한다.

일반적으로 함수를 컴파일 하면 이름이 아닌 주소로 매치을 하지만 dll은 이름을 포함하지 못한다.

때문에 export를 이용하여 함수의 이름을 고정한다.

따라서 일반적인 환경에서는 주소로 함수를 호출하고 dll은 이름으로 호출한다.

explicit (명시적) -  dll,  (lib , a) <-  import library 필요하다.

implicit (암시적) -  loadlibrary 같은 api를 사용해야 한다.

### explicit방식 부터 살펴 보자 

일단 dll프로젝트를 생성하고 int sum(int a, int b);라는 함수를 생성해보자.

```c++
// in dll
__declspec(dllexport) int sum(int a,int b)
{
  return a + b;
}

int WINAPI DllEntryPoint(HINSTANCE hinst, unsigned long reason, void* lpReserved)
{
  return 1;
}

```

```c++
//in executable project 

int sum(int , int );
int main()
{
    print("%d + %d = %d \n ", 10 , 20 , sum(10,20));
    return 0;
}
```



이때 함수를 주소가 아닌 이름으로 고정하기 위해서 __declspec(dllexport)를 사용한다.

그리고 나서 컴파일을 진행하면 .a파일과 dll파일이 생성된다.

명시적으로 링크를 하기 위해서는 dll을 사용하는 프로젝트 폴더에 .a파일을 추가 해야 한다.

그럼 링커에서 이해 하고 링크를 걸어준다.  이경우를 생략하면 링커가 알지 못하여 링커가 에러를 낸다.



### implicit 방식을 보자

implicit 에서는 함수를 호출하기 좀더 복잡하다. 일단 앞서 한  방식처럼 함수 형태를 저장해서 사용하지 못한다?? 그럼 어떻게 해야 하는 가 ? 이때 api를 사용해야 한다. 

```c++
//in executable project 

typedef int (*sum)(int , int );
int main()
{
    HMODULE hmodule =  LoadLibrary("dllname.dll");
    FARPROC proc = GetProcAddress(hmodule,"sum");
    sum f = (sum)proc;
    
    printf("%d + %d = %d \n ", 10 , 20 , f(10,20));
    return 0;
}
```

LoadLibrary는 동적으로 dll을 탑제 하는 코드이다. HMODULE을 리턴한다. GetProcAddress에 HMODULE과 함수이름을 넣어서 함수의 주소를 가지고 온다. 이제 주소를 알아 내었으니 함수 포인터를 이용하여 실행한다. 이 방식으로 컴파일을 하면 링커 에러가 나올 일이 없다. 단 같은 디렉토리에 dll이 있어야 한다. 또 dll이름과 함수이름이 인자이기 때문에 런타임에서 사용자나 다른 스크립트에서 받아서 실행이 가능하다. 

