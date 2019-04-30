---
title: Przeciążanie operatora
ms.date: 11/04/2016
f1_keywords:
- operator_cpp
- operator
helpviewer_keywords:
- redefinable operators [C++]
- non-redefinable operators [C++]
- operator keyword [C++]
- operators [C++], overloading
- operator overloading
ms.assetid: 56ad4c4f-dd0c-45e0-adaa-08fe98cb1f8e
ms.openlocfilehash: d6a294af3ea7ef6085eae0f7069ea2d1fdbb30e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377364"
---
# <a name="operator-overloading"></a>Przeładowanie operatora

**Operator** — słowo kluczowe deklaruje funkcję, określając co *symbol operatora* oznacza, że po zastosowaniu do wystąpienia klasy. Zapewnia znaczenia więcej niż jeden operator lub "overloads" go. Kompilator rozróżnia różne znaczenie w operatorze, sprawdzając typy argumentów.

## <a name="syntax"></a>Składnia

> *Typ* **operator** *symbol operatora* **(** *listy parametrów* **)**

## <a name="remarks"></a>Uwagi

Funkcja z największą liczbą wbudowanych operatorów można zmienić globalnie lub na zasadzie klasa po klasie. Przeciążone operatory są implementowane jako funkcje.

Nazwa Przeciążony operator jest **operator** *x*, gdzie *x* jest operatorem, która jest wyświetlana w poniższej tabeli. Na przykład aby przeciążyć operator dodawania, należy zdefiniować funkcję o nazwie **operator +**. Podobnie, aby można było przeciążyć operator dodawania/przypisania **+=**, zdefiniuj funkcję o nazwie **operator +=**.

### <a name="redefinable-operators"></a>Operatory które można definiować ponownie

|Operator|Nazwa|Typ|
|--------------|----------|----------|
|**,**|Przecinek|plików binarnych|
|**\!**|Logiczne NOT|Jednoargumentowy|
|**\!=**|Nierówność|plików binarnych|
|**%**|Modulo|plików binarnych|
|**%=**|Modulo i przypisanie|plików binarnych|
|**&**|Bitowe ORAZ|plików binarnych|
|**&**|Adres|Jednoargumentowy|
|**&&**|Logicznego AND|plików binarnych|
|**&=**|Bitowe AND i przypisanie|plików binarnych|
|**( )**|Wywołanie funkcji|—|
|**( )**|Operator rzutowania|Jednoargumentowy|
|**&#42;**|Mnożenie|plików binarnych|
|**&#42;**|Wyłuskanie wskaźnika|Jednoargumentowy|
|**&#42;=**|Mnożenie i przypisanie|plików binarnych|
|**+**|Dodawanie|plików binarnych|
|**+**|Plus jednoargumentowy|Jednoargumentowy|
|**++**|Inkrementacja <sup>1</sup>|Jednoargumentowy|
|**+=**|Dodawanie i przypisanie|plików binarnych|
|**-**|Odejmowanie|plików binarnych|
|**-**|negacja jednoargumentowa|Jednoargumentowy|
|**--**|Dekrementacja <sup>1</sup>|Jednoargumentowy|
|**-=**|Odejmowanie i przypisanie|plików binarnych|
|**->**|Wybór elementu członkowskiego|plików binarnych|
|**->&#42;**|Wybór wskaźników do elementów członkowskich|plików binarnych|
|**/**|Dzielenie|plików binarnych|
|**/=**|Dzielenie i przypisanie|plików binarnych|
|**\<**|Mniejsze niż|plików binarnych|
|**<<**|Przesunięcie w lewo|plików binarnych|
|**<<=**|Przypisanie przesunięcia w lewo|plików binarnych|
|**<=**|Mniejsze niż lub równe|plików binarnych|
|**=**|Przypisanie|plików binarnych|
|**==**|Równości|plików binarnych|
|**>**|Większe niż|plików binarnych|
|**>=**|Większe niż lub równe|plików binarnych|
|**>>**|Przesunięcie w prawo|plików binarnych|
|**>>=**|Przypisanie przesunięcia bitowego w prawo|plików binarnych|
|**[ ]**|Indeks dolny tablicy|—|
|**^**|Wykluczające OR|plików binarnych|
|**^=**|Wykluczające i przypisanie|plików binarnych|
|**&#124;**|Bitowe alternatywne OR|plików binarnych|
|**&#124;=**|Bitowe OR alternatywne i przypisanie|plików binarnych|
|**&#124;&#124;**|Logicznego OR|plików binarnych|
|**~**|Uzupełnienie jedynkowe|Jednoargumentowy|
|**delete**|Usuwanie|—|
|**new**|New|—|
|operatory konwersji|operatory konwersji|Jednoargumentowy|

<sup>1</sup> Zwiększ dwie wersje jednoargumentowy i istnieje operatory dekrementacji: operacja preinkrementacji i postincrement.

Zobacz [zasady ogólne dotyczące przeciążania operatora](../cpp/general-rules-for-operator-overloading.md) Aby uzyskać więcej informacji. Ograniczenia dotyczące różnych kategorii przeciążone operatory są opisane w następujących tematach:

- [Operatory jednoargumentowe](../cpp/overloading-unary-operators.md)

- [Operatory binarne](../cpp/binary-operators.md)

- [Przypisanie](../cpp/assignment.md)

- [Wywołanie funkcji](../cpp/function-call-cpp.md)

- [Tworzenie indeksów dolnych](../cpp/subscripting.md)

- [Dostęp do składowej klasy](../cpp/member-access.md)

- [Inkrementacja i dekrementacja](../cpp/increment-and-decrement-operator-overloading-cpp.md).

- [Konwersje typów zdefiniowane przez użytkownika](../cpp/user-defined-type-conversions-cpp.md)

Nie mogą być przeciążone operatory pokazano w poniższej tabeli. W tabeli przedstawiono symboli preprocesora **#** i **##**.

### <a name="nonredefinable-operators"></a>Operatory Nonredefinable

|Operator|Nazwa|
|-|-|
|**.**|Wybór elementu członkowskiego|
|**.&#42;**|Wybór wskaźników do elementów członkowskich|
|**::**|Rozpoznawanie zakresu|
|**? :**|Warunkowe|
|**#**|Preprocesora przekonwertować na ciąg|
|**##**|Łączenie preprocesora|

Mimo że przeciążone operatory są zwykle nazywane niejawnie przez kompilator po ich napotkaniu w kodzie, one mogą być wywoływane jawnie taki sam sposób, jak dowolnego elementu członkowskiego lub niebędących funkcja jest wywoływana:

```cpp
Point pt;
pt.operator+( 3 );  // Call addition operator to add 3 to pt.
```

## <a name="example"></a>Przykład

Poniższy przykład przeciążenia **+** operatora, aby dodać złożone dwie liczby i zwraca wynik.

```cpp
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

```Output
6.8, 11.2
```

## <a name="in-this-section"></a>W tej sekcji

- [Zasady ogólne dotyczące przeciążania operatorów](../cpp/general-rules-for-operator-overloading.md)

- [Przeładowanie operatorów jednoargumentowych](../cpp/overloading-unary-operators.md)

- [Operatory binarne](../cpp/binary-operators.md)

- [Przypisanie](../cpp/assignment.md)

- [Wywołanie funkcji](../cpp/function-call-cpp.md)

- [Tworzenie indeksów dolnych](../cpp/subscripting.md)

- [Dostęp do składowej](../cpp/member-access.md)

## <a name="see-also"></a>Zobacz także

[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)