---
title: Błąd kompilatora C2664
ms.date: 11/04/2016
f1_keywords:
- C2664
helpviewer_keywords:
- C2664
ms.assetid: 3595d66e-cf87-4fda-a896-c0cd81f95db4
ms.openlocfilehash: 8bb9ecef2e08e1f65a817e1a6496a421e727eb13
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221123"
---
# <a name="compiler-error-c2664"></a>Błąd kompilatora C2664

"Function": nie można skonwertować argumentu n z "type1" na "type2"

Ten problem konwersji parametrów może wystąpić w przypadku utworzenia wystąpienia klasy i próby niejawnej konwersji na Konstruktor oznaczony za pomocą **`explicit`** słowa kluczowego. Aby uzyskać więcej informacji na temat konwersji jawnych, zobacz [konwersje typów zdefiniowane przez użytkownika](../../cpp/user-defined-type-conversions-cpp.md).

Jeśli obiekt tymczasowy jest przekazanie do funkcji, która pobiera odwołanie do obiektu jako parametr, odwołanie musi być **`const`** odwołaniem.

Jeśli do funkcji jest przekazywany parametr, który jest typu innego niż ten, którego oczekuje funkcja, tymczasowy obiekt jest tworzony za pomocą odpowiedniego konstruktora. Ten tymczasowy obiekt jest następnie przekazywany do funkcji. W tym przypadku tymczasowy obiekt jest używany do zainicjowania odwołania. We wcześniejszych wersjach języka wszystkie odwołania można było zainicjować przez obiekty tymczasowe.

Aby rozwiązać C2664,

- Sprawdź ponownie prototyp dla danej funkcji i popraw argument wymieniony w komunikacie o błędzie.

- Jeśli to konieczne, podaj konwersję jawną.

C2664 może być też wygenerowany, jeśli klasa ukrywa składową w jednej z jej klas podstawowych.

Aby uzyskać więcej informacji, zobacz [How to: Convert system:: String to wchar_t * lub \* char](../../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C2664 i pokazuje, jak rozwiązać ten problem.

```cpp
// C2664.cpp
// C2664
struct A {
   void f(int i) {};
};

struct B : public A {
   // To fix, uncomment the following line.
   // using A::f;
   void f(A a) {};
};

int main() {
   B b;
   int i = 1;
   b.f(i);   // B::F hides A::f Uncomment the using declaration in B.
}
```

## <a name="example"></a>Przykład

Ten przykład generuje również C2664 i pokazuje, jak rozwiązać ten problem.

```cpp
// C2664b.cpp
// C2664 expected
struct A {
   // To fix, uncomment the following line.
   // A(int i){}
};

void func( int, A ) {}

int main() {
   func( 1, 1 );   // No conversion from int to A.
}
```

## <a name="example"></a>Przykład

Następny przykład ilustruje C2664 za pomocą literału ciągu do wywołania `Test` i pokazuje, jak rozwiązać ten problem. Ponieważ parametr jest `szString` odwołaniem, obiekt musi być utworzony przez odpowiedni Konstruktor. W wyniku powstaje tymczasowy obiekt, którego nie można użyć do zainicjowania odwołania.

```cpp
// C2664c.cpp
// compile with: /EHsc
// C2664 expected
#include <iostream>
#include <string.h>
using namespace std;

class szString {
   int slen;
   char *str;

public:
   szString(const char *);
   int len() const {
      return slen;
   }
};

// Simple reference cannot bind to temp var.
void Test(szString &a) {}

// To fix, uncomment the following line.
// void Test(const szString &a) {}

szString::szString(const char * newstr) : slen(0), str(NULL) {
   slen=strlen(newstr);
   str = new char[slen + 1];
   if (str)
      strcpy_s(str, (slen + 1), newstr);
}

int main() {
   Test("hello");
}
```

## <a name="example"></a>Przykład

Kompilator wymusza standardowe wymagania dotyczące języka C++ do zastosowania **`const`** . Ten przykład generuje C2664:

```cpp
// C2664d.cpp
// C2664 expected
#include <windows.h>

void func1(LPCSTR &s)
{

}

void func2(LPSTR &s)
{
   func1(s);
}

int main()
{
   return 0;
}
```

## <a name="example"></a>Przykład

Poniżej przedstawiono bardziej skomplikowaną sytuację, w której jest generowany C2664, w tym wskazówki dotyczące sposobu jej naprawy:

```cpp
// C2664e.cpp
// compile with: /EHsc
// C2664 expected
#define _INTL
#include <locale>
#include <iostream>

using namespace std;
#define LEN 90

int main( ) {
   char* pszExt = "This is the string to be converted!";
   wchar_t pwszInt [LEN+1];
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));

   // To fix, delete the following line.
   char* pszNext;

   // To fix, uncomment the following line.
   // const char* pszNext;

   wchar_t* pwszNext;
   mbstate_t state;
   locale loc("C");
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).in( state,
      pszExt, &pszExt[strlen(pszExt)], pszNext,
      pwszInt, &pwszInt[strlen(pszExt)], pwszNext );
   // See earlier comment.
      pwszInt[strlen(pszExt)] = 0;
   wcout << ( (res!=codecvt_base::error) ?
                       L"It worked! " : L"It didn't work! " )
   << L"The converted string is:\n ["
   << &pwszInt[0]
   << L"]" << endl;

   exit(-1);
}
```

## <a name="example"></a>Przykład

Zmienna enum nie jest konwertowana na jej typ podstawowy, tak aby wywołanie funkcji zostało spełnione. Aby uzyskać więcej informacji, zobacz [enum Class](../../extensions/enum-class-cpp-component-extensions.md). Poniższy przykład generuje C2664 i pokazuje, jak rozwiązać ten problem.

```cpp
// C2664f.cpp
// compile with: /clr
using namespace System;
public enum class A : Char {
   None = 0,
   NonSilent = 1,
};

void Test(Char c) {}

int main() {
   A aa = A::None;
   Test(aa);   // C2664
   Test(Char(aa));   // OK - fix by using a conversion cast
}
```

## <a name="example"></a>Przykład

Błąd w kompilatorze midl powoduje, że typ wchar_t jest emitowany jako short bez znaku w bibliotece typów. Aby wyeliminować ten błąd, rzutuj typ w kodzie źródłowym C++ lub zdefiniuj typ jako ciąg w pliku idl.

```
// C2664g.idl
import "prsht.idl";

[ object, uuid(8402B8F1-BF7F-4B49-92D4-C2B9DF4543E9) ]

interface IMyObj1 : IUnknown {
   HRESULT  teststr([in, string] wchar_t *wstr);
   HRESULT  testarr([in, size_is(len)] wchar_t wstr[], [in] int len);
   HRESULT  testbstr([in] BSTR bstr);
};

[  uuid(44463307-CBFC-47A6-8B4F-13CD0A83B436) ]
library myproj1 {
   [  version(1.0), uuid(D8622C12-5448-42B8-8F0E-E3AD6B8470C1) ]
   coclass CMyObj1 { interface IMyObj1; };
}
```

C2664 jest również uruchamiany przy użyciu **`wchar_t`** podczas przenoszenia kodu z Visual C++ 6,0 do nowszych wersji. W Visual C++ 6,0 i starszych **`wchar_t`** była **`typedef`** dla **`unsigned short`** i była niejawnie przekonwertowana na ten typ. Po Visual C++ 6,0, **`wchar_t`** jest własnym typem wbudowanym, jak określono w standardzie C++, i nie jest już niejawnie konwertowany na **`unsigned short`** . Zobacz [/Zc: wchar_t (Wchar_t jest typem natywnym)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C2664 i pokazuje, jak rozwiązać ten problem.

```cpp
// C2664h.cpp
#import "C2664g.tlb"
using namespace myproj1;

int main() {
   IMyObj1Ptr ptr;

   wchar_t * mybuff = 0;
   BSTR bstr = 0;
   int len;
   ptr->teststr(mybuff);
   ptr->testbstr(bstr);
   ptr->testarr(mybuff, len);   // C2664
   ptr->testarr((unsigned short *)mybuff, len);   // OK - Fix by using a cast
}
```

## <a name="example"></a>Przykład

Jeśli kompilator nie może wywnioskować argumentów szablonu, również jest generowany C2664.

```cpp
// C2664i.cpp
#include <stdio.h>
template <class T, int iType=0>
class CTypedImg {
public:
   CTypedImg() {}
   void run() {}

   operator CTypedImg<T>& () {
      return *((CTypedImg<T>*)this);
    }
};

template <class t1>
void test(CTypedImg<t1>& myarg) {
   myarg.run();
}

int main() {
   CTypedImg<float,2> img;

   test((CTypedImg<float>&)img);   // OK
   test<float>(img);   // OK
   test(img);   // C2664 - qualify as above to fix
}
```
