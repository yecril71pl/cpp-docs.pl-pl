---
title: "Przeładowanie operatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- operator_cpp
- operator
dev_langs: C++
helpviewer_keywords:
- redefinable operators [C++]
- non-redefinable operators [C++]
- operator keyword [C++]
- operators [C++], overloading
- operator overloading
ms.assetid: 56ad4c4f-dd0c-45e0-adaa-08fe98cb1f8e
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 617236d30f3c4473f6c7785db97789105d6cd565
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="operator-overloading"></a>Przeciążanie operatora
`operator` — Słowo kluczowe deklaruje funkcję określenie, jakie `operator-symbol` oznacza to, gdy jest stosowany do wystąpienia klasy. Zapewnia znaczenie więcej niż jeden operator lub "overloads" go. Kompilator rozróżnia znaczenie innego operatora, sprawdzając typy argumentów.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
type operator operator-symbol ( parameter-list )  
```  
  
## <a name="remarks"></a>Uwagi  
 Można ponownie zdefiniować funkcję największą liczbą wbudowanych operatorów globalnie lub na podstawie klasy klasy. Przeciążone operatory są zaimplementowane jako funkcje.  
  
 Nazwa Przeciążony operator jest `operator x`, gdzie `x` jest operatorem, pojawiającą się w poniższej tabeli. Na przykład do przeciążenia operatora dodawania, zdefiniować funkcji o nazwie `operator+`. Podobnie, aby można było przeciążyć operator dodawania/przypisania `+=`, zdefiniuj funkcji o nazwie `operator+=`.  
  
### <a name="redefinable-operators"></a>Operatory które można definiować ponownie  
  
|Operator|Nazwa|Typ|  
|--------------|----------|----------|  
|`,`|Przecinek|plików binarnych|  
|`!`|NEGACJA|Jednoargumentowe|  
|`!=`|Nierówność|plików binarnych|  
|`%`|Modulo|plików binarnych|  
|`%=`|Modulo i przypisanie|plików binarnych|  
|`&`|Bitowe ORAZ|plików binarnych|  
|`&`|Adres|Jednoargumentowe|  
|`&&`|AND logiczne|plików binarnych|  
|`&=`|Bitowe AND i przypisanie|plików binarnych|  
|`( )`|Wywołanie funkcji|—|  
|`( )`|Operator rzutowania|Jednoargumentowe|  
|`*`|Mnożenie|plików binarnych|  
|`*`|Wyłuskania wskaźnika|Jednoargumentowe|  
|`*=`|Mnożenie i przypisanie|plików binarnych|  
|`+`|Dodawanie|plików binarnych|  
|`+`|Jednoargumentowe Plus|Jednoargumentowe|  
|`++`|Przyrost <sup>1</sup>|Jednoargumentowe|  
|`+=`|Dodawanie i przypisanie|plików binarnych|  
|`-`|Odejmowanie|plików binarnych|  
|`-`|negacja jednoargumentowa|Jednoargumentowe|  
|`--`|Zmniejszenie <sup>1</sup>|Jednoargumentowe|  
|`-=`|Odejmowanie i przypisanie|plików binarnych|  
|`->`|Wybór elementu członkowskiego|plików binarnych|  
|`->*`|Wybór wskaźnika do elementu członkowskiego|plików binarnych|  
|`/`|Dzielenie|plików binarnych|  
|`/=`|Dzielenie i przypisanie|plików binarnych|  
|`<`|Mniejsze niż|plików binarnych|  
|`<<`|Przesunięcie w lewo|plików binarnych|  
|`<<=`|Przypisania przesunięcia w lewo|plików binarnych|  
|`<=`|Mniejsze niż lub równe|plików binarnych|  
|`=`|Przypisanie|plików binarnych|  
|`==`|Równość|plików binarnych|  
|`>`|Większe niż|plików binarnych|  
|`>=`|Większe niż lub równe|plików binarnych|  
|`>>`|Przesunięcie w prawo|plików binarnych|  
|`>>=`|Przypisania przesunięcia w prawo|plików binarnych|  
|`[ ]`|Indeks dolny tablicy|—|  
|`^`|Wyłączny OR|plików binarnych|  
|`^=`|Przypisanie wyłączny OR|plików binarnych|  
|`&#124;`|Bitowe alternatywne OR|plików binarnych|  
|`&#124;=`|Bitowe OR alternatywne i przypisanie|plików binarnych|  
|`&#124;&#124;`|OR logiczne|plików binarnych|  
|`~`|Uzupełnienie jedynkowe|Jednoargumentowe|  
|`delete`|`Delete`|—|  
|`new`|`New`|—|  
|`conversion operators`|operatory konwersji|Jednoargumentowe|  
  
 1 Zwiększ dwie wersje jednoargumentowego i istnieje dekrementacji: preincrement i postincrement.  
  
 Zobacz [zasady ogólne dotyczące przeciążania operatora](../cpp/general-rules-for-operator-overloading.md) Aby uzyskać więcej informacji. Ograniczenia dotyczące różnych kategorii przeciążone operatory są opisane w następujących tematach:  
  
-   [Operatory jednoargumentowe](../cpp/overloading-unary-operators.md)  
  
-   [Operatory binarne](../cpp/binary-operators.md)  
  
-   [Przypisanie](../cpp/assignment.md)  
  
-   [Wywołania funkcji](../cpp/function-call-cpp.md)  
  
-   [Tworzenie indeksów dolnych](../cpp/subscripting.md)  
  
-   [Dostęp do elementu członkowskiego klasy](../cpp/member-access.md)  
  
-   [Inkrementacja i dekrementacja](../cpp/increment-and-decrement-operator-overloading-cpp.md).  
  
-   [Konwersje zdefiniowane przez użytkownika](../cpp/user-defined-type-conversions-cpp.md)  
  
 Operatory pokazano w poniższej tabeli nie może być przeciążony. W tabeli przedstawiono symboli preprocesora `#` i `##`.  
  
### <a name="nonredefinable-operators"></a>Operatory Nonredefinable  
  
|||  
|-|-|  
|`Operator`|`Name`|  
|`.`|Wybór elementu członkowskiego|  
|`.*`|Wybór wskaźnika do elementu członkowskiego|  
|`::`|Rozpoznawanie zakresu|  
|`? :`|Warunkowe|  
|`#`|Preprocesora przekonwertować na ciąg|  
|`##`|Łączenie preprocesora|  
  
 Mimo że przeciążone operatory są zwykle nazywane niejawnie przez kompilator, gdy wystąpi w kodzie, ich mogą być wywoływane jawnie taki sam sposób jak dowolnego elementu członkowskiego lub nosi nazwę funkcji nieczłonkowskiej:  
  
```  
Point pt;  
pt.operator+( 3 );  // Call addition operator to add 3 to pt.  
```  
  
## <a name="example"></a>Przykład  
 Następujący przykład przeciążeń `+` operatora, aby dodać złożone dwie liczby i zwraca wynik.  
  
```  
// operator_overloading.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct Complex {  
   Complex( double r, double i ) : re(r), im(i) {}  
   Complex operator+( Complex &other );  
   void Display( ) {   cout << re << ", " << im << endl; }  
private:  
   double re, im;  
};  
  
// Operator overloaded using a member function  
Complex Complex::operator+( Complex &other ) {  
   return Complex( re + other.re, im + other.im );  
}  
  
int main() {  
   Complex a = Complex( 1.2, 3.4 );  
   Complex b = Complex( 5.6, 7.8 );  
   Complex c = Complex( 0.0, 0.0 );  
  
   c = a + b;  
   c.Display();  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
6.8, 11.2  
```  
  
## <a name="in-this-section"></a>W tej sekcji  
  
1.  [Zasady ogólne dotyczące przeciążania operatorów](../cpp/general-rules-for-operator-overloading.md)  
  
2.  [Przeładowanie operatorów jednoargumentowych](../cpp/overloading-unary-operators.md)  
  
3.  [Operatory binarne](../cpp/binary-operators.md)  
  
4.  [Przypisanie](../cpp/assignment.md)  
  
5.  [Wywołania funkcji](../cpp/function-call-cpp.md)  
  
6.  [Tworzenie indeksów dolnych](../cpp/subscripting.md)  
  
7.  [Dostęp do składowej](../cpp/member-access.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)