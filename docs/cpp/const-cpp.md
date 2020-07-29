---
title: const (C++)
ms.date: 11/04/2016
f1_keywords:
- const_cpp
helpviewer_keywords:
- const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
ms.openlocfilehash: db79e228f1fabc4b2da0a7778126a1b576a67768
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229041"
---
# <a name="const-c"></a>const (C++)

Podczas modyfikowania deklaracji danych, **`const`** słowo kluczowe Określa, że obiekt lub zmienna nie można modyfikować.

## <a name="syntax"></a>Składnia

```
const declaration ;
member-function const ;
```

## <a name="const-values"></a>wartości stałe

**`const`** Słowo kluczowe Określa, że wartość zmiennej jest stała i instruuje kompilator, aby zapobiec modyfikowaniu przez programistę.

```cpp
// constant_values1.cpp
int main() {
   const int i = 5;
   i = 10;   // C3892
   i++;   // C2105
}
```

W języku C++ można użyć **`const`** słowa kluczowego zamiast dyrektywy preprocesora [#define](../preprocessor/hash-define-directive-c-cpp.md) do definiowania wartości stałych. Wartości zdefiniowane przy użyciu **`const`** są objęte sprawdzaniem typów i mogą być używane zamiast wyrażeń stałych. W języku C++ można określić rozmiar tablicy ze **`const`** zmienną w następujący sposób:

```cpp
// constant_values2.cpp
// compile with: /c
const int maxarray = 255;
char store_char[maxarray];  // allowed in C++; not allowed in C
```

W języku C, domyślne wartości są stałe w zewnętrznych powiązaniach, więc mogą być one wyświetlane tylko w plikach źródłowych. W języku C++, wartości stałe są domyślne wewnątrz powiązania, co pozwala im pojawiać się w plikach nagłówkowych.

**`const`** Słowo kluczowe może być również używane w deklaracjach wskaźników.

```cpp
// constant_values3.cpp
int main() {
   char *mybuf = 0, *yourbuf;
   char *const aptr = mybuf;
   *aptr = 'a';   // OK
   aptr = yourbuf;   // C3892
}
```

Wskaźnik do zmiennej zadeklarowanej jako **`const`** może być przypisany tylko do wskaźnika, który jest również zadeklarowany jako **`const`** .

```cpp
// constant_values4.cpp
#include <stdio.h>
int main() {
   const char *mybuf = "test";
   char *yourbuf = "test2";
   printf_s("%s\n", mybuf);

   const char *bptr = mybuf;   // Pointer to constant data
   printf_s("%s\n", bptr);

   // *bptr = 'a';   // Error
}
```

Można użyć wskaźników do danych stałych, takich jak parametry funkcji, aby zapobiec modyfikowaniu parametru przekazywanego za pomocą wskaźnika funkcji.

W przypadku obiektów, które są zadeklarowane jako **`const`** , można wywołać tylko stałe funkcje członkowskie. Dzięki temu stały obiekt nie jest nigdy modyfikowany.

```cpp
birthday.getMonth();    // Okay
birthday.setMonth( 4 ); // Error
```

Stałe lub niestałe funkcje członkowskie można wywoływać dla obiektu niestałego. Można również przeciążać funkcję składową za pomocą **`const`** słowa kluczowego. umożliwia to różne wersje funkcji, które mają być wywoływane w przypadku obiektów stałych i niestałych.

Nie można zadeklarować konstruktorów ani destruktorów za pomocą **`const`** słowa kluczowego.

## <a name="const-member-functions"></a>funkcje składowe const

Deklarowanie funkcji członkowskiej za pomocą **`const`** słowa kluczowego określa, że funkcja jest funkcją "tylko do odczytu", która nie modyfikuje obiektu, dla którego jest wywoływana. Stała funkcja członkowska nie może modyfikować żadnych niestatycznych składowych danych ani wywoływać żadnych funkcji Członkowskich, które nie są stałymi. Aby zadeklarować stałą funkcję członkowską, umieść **`const`** słowo kluczowe po nawiasie zamykającym listy argumentów. **`const`** Słowo kluczowe jest wymagane zarówno w deklaracji, jak i w definicji.

```cpp
// constant_member_function.cpp
class Date
{
public:
   Date( int mn, int dy, int yr );
   int getMonth() const;     // A read-only function
   void setMonth( int mn );   // A write function; can't be const
private:
   int month;
};

int Date::getMonth() const
{
   return month;        // Doesn't modify anything
}
void Date::setMonth( int mn )
{
   month = mn;          // Modifies data member
}
int main()
{
   Date MyDate( 7, 4, 1998 );
   const Date BirthDate( 1, 18, 1953 );
   MyDate.setMonth( 4 );    // Okay
   BirthDate.getMonth();    // Okay
   BirthDate.setMonth( 4 ); // C2662 Error
}
```

## <a name="c-and-c-const-differences"></a>Różnice w języku C i C++

Po zadeklarowaniu zmiennej jako **`const`** w pliku kodu źródłowego C, należy to zrobić:

```cpp
const int i = 2;
```

Tej zmiennej można następnie użyć w innym module w następujący sposób:

```cpp
extern const int i;
```

Jednak aby uzyskać takie samo zachowanie w języku C++, należy zadeklarować **`const`** zmienną jako:

```cpp
extern const int i = 2;
```

Jeśli chcesz zadeklarować **`extern`** zmienną w pliku kodu źródłowego C++ do użycia w pliku kodu źródłowego C, użyj:

```cpp
extern "C" const int x=10;
```

Aby zapobiec przekręcaniu nazwy przez kompilator języka C++.

## <a name="remarks"></a>Uwagi

Gdy po liście parametrów funkcji składowej, **`const`** słowo kluczowe Określa, że funkcja nie modyfikuje obiektu, dla którego jest wywoływana.

Aby uzyskać więcej informacji na temat **`const`** , zobacz następujące tematy:

- [Wskaźniki const i volatile](../cpp/const-and-volatile-pointers.md)

- [Kwalifikatory typów (odwołanie w języku C)](../c-language/type-qualifiers.md)

- [volatile](../cpp/volatile-cpp.md)

- [#define](../preprocessor/hash-define-directive-c-cpp.md)

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)
