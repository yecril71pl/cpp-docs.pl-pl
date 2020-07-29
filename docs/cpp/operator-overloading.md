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
ms.openlocfilehash: 822bd5efb3125e69ff60aa42ba6419969cace403
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227234"
---
# <a name="operator-overloading"></a>Przeładowanie operatora

**`operator`** Słowo kluczowe deklaruje funkcję określającą *symbol operatora* , gdy jest stosowany do wystąpień klasy. Daje to operatorowi więcej niż jedno znaczenie lub "przeciążenia". Kompilator rozróżnia różne znaczenia operatora, sprawdzając typy jego operandów...

## <a name="syntax"></a>Składnia

> *Typ* **`operator`** *operator-— symbol* **(** *Lista parametrów* **)**

## <a name="remarks"></a>Uwagi

Można ponownie zdefiniować funkcję większości wbudowanych operatorów globalnie lub w oparciu o klasę klasy. Przeciążone operatory są implementowane jako funkcje.

Nazwa przeciążonego operatora to **`operator`** *x*, gdzie *x* jest operatorem, który pojawia się w poniższej tabeli. Na przykład aby przeciążyć operator dodawania, należy zdefiniować funkcję o nazwie **operator +**. Podobnie, aby przeciążać operator dodawania/przypisywania, **+=** Zdefiniuj funkcję o nazwie **operator + =**.

### <a name="redefinable-operators"></a>Operatory do przedefiniować

|Operator|Nazwa|Typ|
|--------------|----------|----------|
|**,**|Przecinek|Binarne|
|**!**|Operator logiczny NOT|Jednoargumentowy|
|**!=**|Nierówność|Binarne|
|**%**|Modulo|Binarne|
|**%=**|Modulo i przypisanie|Binarne|
|**&**|Bitowe ORAZ|Binarne|
|**&**|Adres|Jednoargumentowy|
|**&&**|Logiczne AND|Binarne|
|**&=**|Bitowe AND i przypisanie|Binarne|
|**( )**|Wywołanie funkcji|—|
|**( )**|Operator rzutowania|Jednoargumentowy|
|**&#42;**|Mnożenie|Binarne|
|**&#42;**|Odwołuje się do wskaźnika|Jednoargumentowy|
|**&#42;=**|Mnożenie i przypisanie|Binarne|
|**+**|Dodawanie|Binarne|
|**+**|Jednoargumentowy Plus|Jednoargumentowy|
|**++**|Zwiększ <sup>1</sup>|Jednoargumentowy|
|**+=**|Dodawanie i przypisanie|Binarne|
|**-**|Odejmowanie|Binarne|
|**-**|negacja jednoargumentowa|Jednoargumentowy|
|**--**|Zmniejszenie <sup>1</sup>|Jednoargumentowy|
|**-=**|Odejmowanie i przypisanie|Binarne|
|**->**|Wybór elementu członkowskiego|Binarne|
|**->&#42;**|Wybór wskaźnika do elementu członkowskiego|Binarne|
|**/**|Dział|Binarne|
|**/=**|Dzielenie i przypisanie|Binarne|
|**\<**|Mniejsze niż|Binarne|
|**<<**|Przesunięcie w lewo|Binarne|
|**<<=**|Przypisanie przesunięcia w lewo|Binarne|
|**<=**|Mniejsze niż lub równe|Binarne|
|**=**|Przypisanie|Binarne|
|**==**|Równość|Binarne|
|**>**|Większe niż|Binarne|
|**>=**|Większe niż lub równe|Binarne|
|**>>**|Przesunięcie w prawo|Binarne|
|**>>=**|Przypisanie przesunięcia w prawo|Binarne|
|**[ ]**|Indeks dolny tablicy|—|
|**^**|Wyłączny lub|Binarne|
|**^=**|Wyłączność lub przypisanie|Binarne|
|**&#124;**|Bitowe alternatywne OR|Binarne|
|**&#124;=**|Bitowe OR alternatywne i przypisanie|Binarne|
|**&#124;&#124;**|Logiczne OR|Binarne|
|**~**|Uzupełnienie jedynkowe|Jednoargumentowy|
|**`delete`**|Usuń|—|
|**`new`**|Nowy|—|
|operatory konwersji|operatory konwersji|Jednoargumentowy|

Istnieją <sup>1</sup> dwie wersje jednoargumentowego przyrostu i zmniejszania: przyrostowe i postinkrementacji.

Aby uzyskać więcej informacji, zobacz [ogólne reguły przeładowania operatora](../cpp/general-rules-for-operator-overloading.md) . Ograniczenia dotyczące różnych kategorii przeciążonych operatorów są opisane w następujących tematach:

- [Operatory jednoargumentowe](../cpp/overloading-unary-operators.md)

- [Operatory binarne](../cpp/binary-operators.md)

- [Przypisanie](../cpp/assignment.md)

- [Wywołanie funkcji](../cpp/function-call-cpp.md)

- [Tworzenie indeksów dolnych](../cpp/subscripting.md)

- [Dostęp do elementu członkowskiego klasy](../cpp/member-access.md)

- [Zwiększ i zmniejsz](../cpp/increment-and-decrement-operator-overloading-cpp.md).

- [Konwersje typów zdefiniowane przez użytkownika](../cpp/user-defined-type-conversions-cpp.md)

Operatory podane w poniższej tabeli nie mogą być przeciążone. Tabela zawiera symbole preprocesora **#** i **##** .

### <a name="nonredefinable-operators"></a>Operatory Nonredefinable

|Operator|Nazwa|
|-|-|
|**.**|Wybór elementu członkowskiego|
|**. &#42;**|Wybór wskaźnika do elementu członkowskiego|
|**::**|Rozpoznawanie zakresu|
|**? :**|Warunkowe|
|**#**|Konwersja preprocesora na ciąg|
|**##**|Łączenie preprocesora|

Chociaż przeciążone operatory są zwykle wywoływane niejawnie przez kompilator, gdy są one napotkane w kodzie, mogą być wywoływane jawnie w taki sam sposób jak każdy element członkowski lub funkcja nieczłonkowska jest wywoływana:

```cpp
Point pt;
pt.operator+( 3 );  // Call addition operator to add 3 to pt.
```

## <a name="example"></a>Przykład

Poniższy przykład przeciąża **+** operatora, aby dodać dwie liczby zespolone i zwraca wynik.

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

- [Ogólne reguły przeciążania operatora](../cpp/general-rules-for-operator-overloading.md)

- [Przeciążanie operatorów jednoargumentowych](../cpp/overloading-unary-operators.md)

- [Operatory binarne](../cpp/binary-operators.md)

- [Przypisanie](../cpp/assignment.md)

- [Wywołanie funkcji](../cpp/function-call-cpp.md)

- [Tworzenie indeksów dolnych](../cpp/subscripting.md)

- [Dostęp do elementu członkowskiego](../cpp/member-access.md)

## <a name="see-also"></a>Zobacz także

[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
