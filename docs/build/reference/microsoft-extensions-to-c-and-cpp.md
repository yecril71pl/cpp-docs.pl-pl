---
title: Rozszerzenia Microsoft do C i C++ | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- or_eq operator
- ~ operator, extensions to C/C++
- '& operator, extensions to C/C++'
- '&= operator'
- iso646.h header
- Xor operator, Microsoft extensions to C/C++
- '!= operator'
- '! operator, extension to C++'
- Or operator, Microsoft extensions to C/C++
- ^ operator, extensions to C/C++
- ^= operator, C++ extensions
- xor_eq operator
- and_eq operator
- Microsoft extensions to C/C++
- '|= operator'
- '|| operator'
- And operator, extensions to C/C++
- NOT operator
- '&& operator'
- extensions, C language
- Visual C++, extensions to C/C++
- '| operator, extensions'
- not_eq operator
- Visual C, Microsoft extensions
- extensions
- compl method
ms.assetid: e811a74a-45ba-4c00-b206-2f2321b8689a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d8453209a92b8f7485a9e7f575fb8810196d27fb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="microsoft-extensions-to-c-and-c"></a>Rozszerzenia Microsoft do C i C++
Środowisko Visual C++ rozszerza standardy ANSI języków C i C++ w następujący sposób.  
  
## <a name="keywords"></a>Słowa kluczowe  
 Dodano kilka słów kluczowych. Na liście w [słowa kluczowe](../../cpp/keywords-cpp.md), słów kluczowych, które mają dwa wiodące znaki podkreślenia są rozszerzenia Visual C++.  
  
## <a name="out-of-class-definition-of-static-const-integral-or-enum-members"></a>Pozaklasowa definicja elementów członkowskich będących całkowitoliczbowymi statycznymi stałymi static const (lub wyliczeniami enum)  
 Zgodnie ze standardem (**/Za**), należy się upewnić definicji klasy elementów członkowskich danych, jak pokazano poniżej:  
  
```  
  
      class CMyClass  {  
   static const int max = 5;  
   int m_array[max];  
}  
...  
const int CMyClass::max;   // out of class definition  
```  
  
 W obszarze **/Ze**, definicji klasy jest opcjonalne dla elementów członkowskich danych statycznych, stała wyliczenia całkowite i const. Tylko elementy całkowitoliczbowe i wyliczenia, które są statyczne i stałe, mogą mieć inicjatory w klasach. Wyrażenie inicjujące musi być wyrażeniem stałym.  
  
 Aby uniknąć błędów podczas definicji klasy została podana w nagłówku pliku i plik nagłówka jest uwzględniane w wielu plikach źródłowych, należy użyć [selectany](../../cpp/selectany.md). Na przykład:  
  
```  
__declspec(selectany) const int CMyClass::max = 5;  
```  
  
## <a name="casts"></a>Rzutowania  
 Kompilatory języków C++ i C obsługują następujące rodzaje rzutowań niezgodnych ze standardem ANSI:  
  
-   Rzutowania niezgodne ze standardem ANSI generujące wartości lvalue. Na przykład:  
  
    ```  
    char *p;  
    (( int * ) p )++;  
    ```  
  
    > [!NOTE]
    >  To rozszerzenie jest dostępne tylko w języku C. W celu zmodyfikowania wskaźnika tak, aby wskazywał inny typ, w kodzie języka C++ można użyć odpowiedniego kodu języka C zgodnego ze standardem ANSI.  
  
     Poprzedni przykład można dopasować do standardu ANSI języka C w następujący sposób:  
  
    ```  
    p = ( char * )(( int * )p + 1 );  
    ```  
  
-   Rzutowania wskaźnika funkcji do wskaźnika danych niezgodne ze standardem ANSI. Na przykład:  
  
    ```  
    int ( * pfunc ) ();   
    int *pdata;  
    pdata = ( int * ) pfunc;  
    ```  
  
     Aby wykonać to samo rzutowanie z utrzymaniem zgodności ze standardem ANSI, można rzutować wskaźnik funkcji na typ danych `uintptr_t`, a dopiero potem na wskaźnik danych:  
  
    ```  
    pdata = ( int * ) (uintptr_t) pfunc;  
    ```  
  
## <a name="variable-length-argument-lists"></a>Listy argumentów o zmiennej długości  
 Kompilatory języków C++ i C obsługują deklaratora funkcji, który określa zmienną liczbę argumentów, a następnie definicję funkcji wskazującą typ:  
  
```  
void myfunc( int x, ... );  
void myfunc( int x, char * c )  
{ }  
```  
  
## <a name="single-line-comments"></a>Komentarze jednowierszowe  
 Kompilator języka C obsługuje komentarze jednowierszowe, które wprowadza się przy użyciu dwóch znaków ukośnika (//):  
  
```  
// This is a single-line comment.  
```  
  
## <a name="scope"></a>Zakres  
 Kompilator języka C obsługuje następujące funkcje dotyczące zakresu.  
  
-   Zmiana definicji zewnętrznych elementów na statyczne:  
  
    ```  
    extern int clip();  
    static int clip()  
    {}  
    ```  
  
-   Używanie nieszkodliwych zmian definicji typów w tym samym zakresie:  
  
    ```  
    typedef int INT;  
    typedef int INT;  
    ```  
  
-   Deklaratory funkcji z ustawionym zakresem pliku:  
  
    ```  
    void func1()  
    {  
        extern int func2( double );  
    }  
    int main( void )  
    {  
        func2( 4 );    //  /Ze passes 4 as type double  
    }                  //  /Za passes 4 as type int  
    ```  
  
-   Używanie zmiennych z ustawionym zakresem bloku, które są inicjowane za pomocą wyrażeń niebędących stałymi:  
  
    ```  
    int clip( int );  
    int bar( int );  
    int main( void )  
    {  
        int array[2] = { clip( 2 ), bar( 4 ) };  
    }  
    int clip( int x )  
    {  
        return x;  
    }  
    int bar( int x )  
    {  
        return x;  
    }  
    ```  
  
## <a name="data-declarations-and-definitions"></a>Deklaracje i definicje danych  
 Kompilator języka C obsługuje następujące funkcje deklarowania i definiowania danych.  
  
-   Mieszane znaki i stałe w postaci ciągów w inicjatorze:  
  
    ```  
    char arr[5] = {'a', 'b', "cde"};  
    ```  
  
-   Bit pola, które mają inne niż typy podstawowe **unsigned int** lub **podpisany int**.  
  
-   Deklaratory, które nie mają typu:  
  
    ```  
    x;  
    int main( void )  
    {  
        x = 1;  
    }  
    ```  
  
-   Tablice bez określonego rozmiaru występujące jako ostatnie pole w strukturach i złożeniach:  
  
    ```  
    struct zero  
    {  
        char *c;  
        int zarray[];  
    };  
    ```  
  
-   Struktury nienazwane (anonimowe):  
  
    ```  
    struct  
    {  
        int i;  
        char *s;  
    };  
    ```  
  
-   Złożenia nienazwane (anonimowe):  
  
    ```  
    union  
    {  
        int i;  
        float fl;  
    };  
    ```  
  
-   Nienazwane elementy członkowskie:  
  
    ```  
    struct s  
    {  
       unsigned int flag : 1;  
       unsigned int : 31;  
    }  
    ```  
  
## <a name="intrinsic-floating-point-functions"></a>Wewnętrzne funkcje zmiennoprzecinkowe  
 Kompilatora C++ i kompilatora C obsługuje generowania wbudowanego **x86 określonych >** z `atan`, `atan2`, `cos`, `exp`, `log`, `log10`, `sin`, `sqrt`, i `tan` funkcje **zakończenia x86 określonych** podczas **/Oi** jest określona. Użycie tych wewnętrznych funkcji powoduje, że kompilator języka C traci zgodność ze standardem ANSI, ponieważ funkcje nie ustawiają zmiennej `errno`.  
  
## <a name="passing-a-non-const-pointer-parameter-to-a-function-that-expects-a-reference-to-a-const-pointer-parameter"></a>Przekazywanie parametru wskaźnika niebędącego stałą do funkcji, która oczekuje odwołania do parametru wskaźnika będącego stałą  
 Jest to rozszerzenie języka C++. Ten kod będzie kompilacji z **/Ze**:  
  
```  
typedef   int   T;  
  
const T  acT = 9;      // A constant of type 'T'  
const T* pcT = &acT;   // A pointer to a constant of type 'T'  
  
void func2 ( const T*& rpcT )   // A reference to a pointer to a constant of type 'T'  
{  
   rpcT = pcT;  
}  
  
T*   pT;               // A pointer to a 'T'  
  
void func ()  
{  
   func2 ( pT );      // Should be an error, but isn't detected  
   *pT   = 7;         // Invalidly overwrites the constant 'acT'  
}  
```  
  
## <a name="iso646h-not-enabled"></a>Niewłączony nagłówek ISO646.H  
 W obszarze **/Ze**, powinien obejmować iso646.h, jeśli chcesz używać formy tekst następujące operatory:  
  
-   && (and)  
  
-   &= (and_eq)  
  
-   & (bitand)  
  
-   &#124; (bitor)  
  
-   ~ (compl)  
  
-   ! (not)  
  
-   != (not_eq)  
  
-   &#124; &#124; (lub)  
  
-   &#124; = (or_eq)  
  
-   ^ (xor)  
  
-   ^= (xor_eq)  
  
## <a name="address-of-string-literal-has-type-const-char--not-const-char--"></a>Adres literału będącego ciągiem tekstowym ma typ const char [], a nie const char (*) []  
 Poniższy przykład będą dane wyjściowe char const (\*) [4] w obszarze **/Za**, ale char const [4] w obszarze **/Ze**.  
  
```  
#include <stdio.h>  
#include <typeinfo>  
  
int main()  
{  
    printf_s("%s\n", typeid(&"abc").name());  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [/ Za, /Ze (Wyłącz rozszerzenia językowe)](../../build/reference/za-ze-disable-language-extensions.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)