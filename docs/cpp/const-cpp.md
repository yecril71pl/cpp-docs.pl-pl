---
title: Const (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- const_cpp
dev_langs:
- C++
helpviewer_keywords:
- const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c296f473f9128907e69437edf66734a7566242ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="const-c"></a>const (C++)
Podczas modyfikowania deklaracji danych **const** — słowo kluczowe Określa, czy obiektu lub zmienna nie jest można modyfikować.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      const declaration ;  
member-function const ;  
```  
  
## <a name="const-values"></a>wartości stałych  
 **Const** — słowo kluczowe Określa, że wartość zmiennej jest stałe i informuje kompilator, aby zapobiec dla programisty modyfikowania jej.  
  
```  
// constant_values1.cpp  
int main() {  
   const int i = 5;  
   i = 10;   // C3892  
   i++;   // C2105  
}  
```  
  
 W języku C++, można użyć **const** słowa kluczowego zamiast [#define](../preprocessor/hash-define-directive-c-cpp.md) dyrektywy preprocesora do definiowania stałej wartości. Wartości zdefiniowane z **const** podlegają Sprawdzanie typu, a następnie można użyć zamiast wyrażenia stałe. W języku C++, można określić rozmiaru tablicy o **const** zmiennej w następujący sposób:  
  
```  
// constant_values2.cpp  
// compile with: /c  
const int maxarray = 255;  
char store_char[maxarray];  // allowed in C++; not allowed in C  
```  
  
 W języku C, domyślne wartości są stałe w zewnętrznych powiązaniach, więc mogą być one wyświetlane tylko w plikach źródłowych. W języku C++, wartości stałe są domyślne wewnątrz powiązania, co pozwala im pojawiać się w plikach nagłówkowych.  
  
 **Const** — słowo kluczowe można również w deklaracji wskaźnika.  
  
```  
// constant_values3.cpp  
int main() {  
   char *mybuf = 0, *yourbuf;  
   char *const aptr = mybuf;  
   *aptr = 'a';   // OK  
   aptr = yourbuf;   // C3892  
}  
```  
  
 Wskaźnik do zmiennej zadeklarowany jako **const** można przypisać tylko do wskaźnika, który jest również zadeklarowany jako **const**.  
  
```  
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
  
 Dla obiektów, które są zadeklarowane jako **const**, użytkownik może wywołać tylko członek stałej funkcji. Dzięki temu stały obiekt nie jest nigdy modyfikowany.  
  
```  
birthday.getMonth();    // Okay  
birthday.setMonth( 4 ); // Error  
```  
  
 Stałe lub niestałe funkcje członkowskie można wywoływać dla obiektu niestałego. Można także przeciążyć funkcji Członkowskich przy użyciu **const** słowa kluczowego; dzięki temu inna wersja funkcja wywoływana dla obiektów nieunikatowego i stałych.  
  
 Nie można zadeklarować konstruktorów ani destruktorów z **const** — słowo kluczowe.  
  
## <a name="const-member-functions"></a>stałe funkcje Członkowskie  
 Deklarowanie funkcji członkowskiej z **const** — słowo kluczowe Określa, że funkcja jest funkcja "tylko do odczytu", która nie modyfikuje obiektu, dla którego jest wywoływana. Funkcja członkowska stałej nie można zmodyfikować żadnych elementów członkowskich danych niestatyczna ani wywołanie funkcji, które nie są stałe dowolnego elementu członkowskiego. Aby zadeklarować funkcji członkowskiej stałej, umieść **const** — słowo kluczowe po nawiasie zamykającym listy argumentów. **Const** — słowo kluczowe jest wymagany w deklaracji i definicji.  
  
```  
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
  
## <a name="c-and-c-const-differences"></a>Różnice dotyczące słowa kluczowego const w C i C++  
 Gdy zadeklarować zmiennej jako **const** w pliku kodu źródłowego C, możesz to zrobić jako:  
  
```  
const int i = 2;  
```  
  
 Tej zmiennej można następnie użyć w innym module w następujący sposób:  
  
```  
extern const int i;  
```  
  
 Jednak aby uzyskać takie samo zachowanie w języku C++, należy zadeklarować Twojej **const** zmiennej jako:  
  
```  
extern const int i = 2;  
```  
  
 Jeśli chcesz zadeklarować zmienną `extern` w pliku kodu źródłowego języka C++ do użytku w pliku kodu źródłowego C, należy użyć:  
  
```  
extern "C" const int x=10;  
```  
  
 Aby zapobiec przekręcaniu nazwy przez kompilator języka C++.  
  
## <a name="remarks"></a>Uwagi  
 Po liście parametrów funkcji członkowskiej, **const** — słowo kluczowe określa funkcja nie modyfikuje obiektu, dla którego jest wywoływany.  
  
 Aby uzyskać więcej informacji na temat **const**, zobacz następujące tematy:  
    
-   [Wskaźniki stałe i nietrwałe](../cpp/const-and-volatile-pointers.md)  
  
-   [Kwalifikatory typów (Dokumentacja języka C)](../c-language/type-qualifiers.md)  
  
-   [volatile](../cpp/volatile-cpp.md)  
  
-   [#define](../preprocessor/hash-define-directive-c-cpp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)