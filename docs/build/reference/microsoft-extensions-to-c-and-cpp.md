---
title: Rozszerzenia Microsoft do C i C++
ms.date: 06/14/2018
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
ms.openlocfilehash: 77f2ed64a0c816d84e67f66b664141581a9fad51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231510"
---
# <a name="microsoft-extensions-to-c-and-c"></a>Rozszerzenia Microsoft do C i C++

Środowisko Visual C++ rozszerza standardy ANSI języków C i C++ w następujący sposób.

## <a name="keywords"></a>Słowa kluczowe

Dodano kilka słów kluczowych. Na liście w [słowach kluczowych](../../cpp/keywords-cpp.md)słowa kluczowe, które mają dwie wiodące podkreślenia, są Visual C++ rozszerzenia.

## <a name="out-of-class-definition-of-static-const-integral-or-enum-members"></a>Definicja poza klasą składowych static const Integer (lub enum)

W obszarze Standard (**/za**) należy utworzyć definicję poza klasą dla elementów członkowskich danych, jak pokazano poniżej:

```cpp
class CMyClass  {
   static const int max = 5;
   int m_array[max];
}
// . . .
const int CMyClass::max;   // out of class definition
```

W obszarze **/ze**Definicja poza klasą jest opcjonalna dla elementów członkowskich danych static, const integer i const. Tylko elementy całkowitoliczbowe i wyliczenia, które są statyczne i stałe, mogą mieć inicjatory w klasach. Wyrażenie inicjujące musi być wyrażeniem stałym.

Aby uniknąć błędów w przypadku podanej definicji poza klasą w pliku nagłówkowym, a plik nagłówkowy jest uwzględniany w wielu plikach źródłowych, użyj [selectany](../../cpp/selectany.md). Na przykład:

```cpp
__declspec(selectany) const int CMyClass::max = 5;
```

## <a name="casts"></a>Rzutowania

Kompilatory języków C++ i C obsługują następujące rodzaje rzutowań niezgodnych ze standardem ANSI:

- Rzutowania niezgodne ze standardem ANSI generujące wartości lvalue. Na przykład:

   ```C
   char *p;
   (( int * ) p )++;
   ```

   > [!NOTE]
   > To rozszerzenie jest dostępne tylko w języku C. W celu zmodyfikowania wskaźnika tak, aby wskazywał inny typ, w kodzie języka C++ można użyć odpowiedniego kodu języka C zgodnego ze standardem ANSI.

   Poprzedni przykład można dopasować do standardu ANSI języka C w następujący sposób:

   ```C
   p = ( char * )(( int * )p + 1 );
   ```

- Rzutowania wskaźnika funkcji do wskaźnika danych niezgodne ze standardem ANSI. Na przykład:

   ```C
   int ( * pfunc ) ();
   int *pdata;
   pdata = ( int * ) pfunc;
   ```

   Aby wykonać to samo rzutowanie z utrzymaniem zgodności ze standardem ANSI, można rzutować wskaźnik funkcji na typ danych `uintptr_t`, a dopiero potem na wskaźnik danych:

   ```C
   pdata = ( int * ) (uintptr_t) pfunc;
   ```

## <a name="variable-length-argument-lists"></a>Listy argumentów o zmiennej długości

Kompilatory języków C++ i C obsługują deklaratora funkcji, który określa zmienną liczbę argumentów, a następnie definicję funkcji wskazującą typ:

```cpp
void myfunc( int x, ... );
void myfunc( int x, char * c )
{ }
```

## <a name="single-line-comments"></a>Komentarze jednowierszowe

Kompilator języka C obsługuje komentarze jednowierszowe, które wprowadza się przy użyciu dwóch znaków ukośnika (//):

```C
// This is a single-line comment.
```

## <a name="scope"></a>Zakres

Kompilator języka C obsługuje następujące funkcje dotyczące zakresu.

- Zmiana definicji zewnętrznych elementów na statyczne:

   ```C
   extern int clip();
   static int clip()
   {}
   ```

- Używanie nieszkodliwych zmian definicji typów w tym samym zakresie:

   ```C
   typedef int INT;
   typedef int INT;
   ```

- Deklaratory funkcji z ustawionym zakresem pliku:

   ```C
   void func1()
   {
       extern int func2( double );
   }
   int main( void )
   {
       func2( 4 );    //  /Ze passes 4 as type double
   }                  //  /Za passes 4 as type int
   ```

- Używanie zmiennych z ustawionym zakresem bloku, które są inicjowane za pomocą wyrażeń niebędących stałymi:

   ```C
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

- Mieszane znaki i stałe w postaci ciągów w inicjatorze:

   ```C
   char arr[5] = {'a', 'b', "cde"};
   ```

- Pola bitowe mające typy podstawowe inne niż **`unsigned int`** lub **`signed int`** .

- Deklaratory, które nie mają typu:

   ```C
   x;
   int main( void )
   {
       x = 1;
   }
   ```

- Tablice bez określonego rozmiaru występujące jako ostatnie pole w strukturach i złożeniach:

   ```C
   struct zero
   {
       char *c;
       int zarray[];
   };
   ```

- Struktury nienazwane (anonimowe):

   ```C
   struct
   {
       int i;
       char *s;
   };
   ```

- Złożenia nienazwane (anonimowe):

   ```C
   union
   {
       int i;
       float fl;
   };
   ```

- Nienazwane elementy członkowskie:

   ```C
   struct s
   {
      unsigned int flag : 1;
      unsigned int : 31;
   }
   ```

## <a name="intrinsic-floating-point-functions"></a>Wewnętrzne funkcje zmiennoprzecinkowe

Kompilator x86 C++ i kompilator C obsługują wbudowaną generację `atan` funkcji,,,,,,, `atan2` `cos` i w `exp` `log` `log10` `sin` `sqrt` `tan` przypadku określenia **/Oi** . Użycie tych wewnętrznych funkcji powoduje, że kompilator języka C traci zgodność ze standardem ANSI, ponieważ funkcje nie ustawiają zmiennej `errno`.

## <a name="passing-a-non-const-pointer-parameter-to-a-function-that-expects-a-reference-to-a-const-pointer-parameter"></a>Przekazywanie parametru wskaźnika innego niż const do funkcji, która oczekuje odwołania do parametru wskaźnika const

Jest to rozszerzenie języka C++. Ten kod zostanie skompilowany z **/ze**:

```cpp
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

## <a name="iso646h-not-enabled"></a>Iso646. H nie włączona

W obszarze **/ze**należy uwzględnić iso646. h, jeśli chcesz używać form tekstowych następujących operatorów:

- && (i)

- &= (and_eq)

- & (BitAnd)

- &#124; (BitOr)

- ~ (compl)

- ! (not)

- != (not_eq)

- &#124;&#124; (lub)

- &#124;= (or_eq)

- ^ (xor)

- ^= (xor_eq)

## <a name="address-of-string-literal-has-type-const-char--not-const-char--"></a>Adres literału ciągu zawiera typ const char [], a nie const char (*) []

Poniższy przykład zostanie wyprowadzony `char const (*)[4]` w obszarze **/za**, ale `char const [4]` w obszarze **/ze**.

```cpp
#include <stdio.h>
#include <typeinfo>

int main()
{
    printf_s("%s\n", typeid(&"abc").name());
}
```

## <a name="see-also"></a>Zobacz także

- [/Za,/ze (Wyłącz rozszerzenia językowe)](za-ze-disable-language-extensions.md)
- [Opcje kompilatora MSVC](compiler-options.md)
- [Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
