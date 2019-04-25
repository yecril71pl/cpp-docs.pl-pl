---
title: const (C++)
ms.date: 11/04/2016
f1_keywords:
- const_cpp
helpviewer_keywords:
- const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
ms.openlocfilehash: 759ee503acb12f6c1a30fbbfaf87a8f66433e571
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154753"
---
# <a name="const-c"></a>const (C++)

Podczas modyfikowania deklarację danych **const** — słowo kluczowe Określa, że obiekt lub zmienna nie można modyfikować.

## <a name="syntax"></a>Składnia

```
const declaration ;
member-function const ;
```

## <a name="const-values"></a>wartości stałych

**Const** — słowo kluczowe Określa, że wartość zmiennej jest stała i informuje kompilator, aby uniemożliwić modyfikowanie przez programistę.

```cpp
// constant_values1.cpp
int main() {
   const int i = 5;
   i = 10;   // C3892
   i++;   // C2105
}
```

W języku C++, można użyć **const** słowa kluczowego zamiast [#define](../preprocessor/hash-define-directive-c-cpp.md) dyrektywy preprocesora do definiowania wartości stałych. Wartości zdefiniowane za pomocą **const** podlegają kontroli typów i mogą być używane zamiast wyrażeń stałych. W języku C++, można określić rozmiar tablicy o liczbie **const** zmiennej w następujący sposób:

```cpp
// constant_values2.cpp
// compile with: /c
const int maxarray = 255;
char store_char[maxarray];  // allowed in C++; not allowed in C
```

W języku C, domyślne wartości są stałe w zewnętrznych powiązaniach, więc mogą być one wyświetlane tylko w plikach źródłowych. W języku C++, wartości stałe są domyślne wewnątrz powiązania, co pozwala im pojawiać się w plikach nagłówkowych.

**Const** również można użyć słowa kluczowego w deklaracjach wskaźnika.

```cpp
// constant_values3.cpp
int main() {
   char *mybuf = 0, *yourbuf;
   char *const aptr = mybuf;
   *aptr = 'a';   // OK
   aptr = yourbuf;   // C3892
}
```

Wskaźnik do zmiennej, zadeklarowanej jako **const** można przypisać tylko do wskaźnika, który także jest zadeklarowany jako **const**.

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

Dla obiektów, które są zadeklarowane jako **const**, może wywołać tylko stałe elementy członkowskie funkcji. Dzięki temu stały obiekt nie jest nigdy modyfikowany.

```cpp
birthday.getMonth();    // Okay
birthday.setMonth( 4 ); // Error
```

Stałe lub niestałe funkcje członkowskie można wywoływać dla obiektu niestałego. Można także przeciążyć funkcji składowej za pomocą **const** słowa kluczowego; dzięki temu w innej wersji programu funkcja będzie wywoływana dla obiektów stałych i niestałych.

Nie można zadeklarować konstruktorów i destruktorów ze **const** — słowo kluczowe.

## <a name="const-member-functions"></a>Funkcje składowe const

Deklarowanie funkcji składowej z **const** — słowo kluczowe Określa, że funkcja jest funkcją "tylko do odczytu", która nie powoduje modyfikacji obiektu, dla którego jest wywoływana. Stała składowa nie można modyfikować żadnych składowych danych niestatycznych lub wywołania funkcji, które nie są stałe dowolnego elementu członkowskiego. Aby zadeklarować funkcję stałe elementy członkowskie, umieść **const** — słowo kluczowe po nawiasie zamykającym listy argumentów. **Const** — słowo kluczowe jest wymagany w deklaracji i definicji.

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

## <a name="c-and-c-const-differences"></a>Różnice const w C i C++

Kiedy Deklarujesz zmienną **const** w pliku kodu źródłowego C, możesz to zrobić jako:

```cpp
const int i = 2;
```

Tej zmiennej można następnie użyć w innym module w następujący sposób:

```cpp
extern const int i;
```

Jednak aby uzyskać takie samo zachowanie w języku C++, należy zadeklarować swoje **const** zmiennej jako:

```cpp
extern const int i = 2;
```

Jeśli chcesz zadeklarować **extern** zmiennej w pliku kodu źródłowego języka C++ do użycia w pliku kodu źródłowego C, użyj:

```cpp
extern "C" const int x=10;
```

Aby zapobiec przekręcaniu nazwy przez kompilator języka C++.

## <a name="remarks"></a>Uwagi

Jeśli zgodnie z listą parametrów dla funkcji członkowskiej, **const** — słowo kluczowe określa funkcja nie powoduje modyfikacji obiektu, dla której zostanie wywołana.

Aby uzyskać więcej informacji na temat **const**, zobacz następujące tematy:

- [Wskaźniki stałe i nietrwałe](../cpp/const-and-volatile-pointers.md)

- [Kwalifikatory typów (Skorowidz języka c)](../c-language/type-qualifiers.md)

- [volatile](../cpp/volatile-cpp.md)

- [#define](../preprocessor/hash-define-directive-c-cpp.md)

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)