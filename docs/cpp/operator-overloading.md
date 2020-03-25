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
ms.openlocfilehash: a16f68088ffffd6c3cf38f5ae3adda5f2d59fb57
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188574"
---
# <a name="operator-overloading"></a>Przeładowanie operatora

Słowo kluczowe **operator** deklaruje funkcję określającą *symbol operatora* , gdy jest stosowany do wystąpień klasy. Daje to operatorowi więcej niż jedno znaczenie lub "przeciążenia". Kompilator rozróżnia różne znaczenia operatora, sprawdzając typy jego operandów...

## <a name="syntax"></a>Składnia

> operator *typu* **operator** *— symbol* **(** *Lista parametrów* **)**

## <a name="remarks"></a>Uwagi

Można ponownie zdefiniować funkcję większości wbudowanych operatorów globalnie lub w oparciu o klasę klasy. Przeciążone operatory są implementowane jako funkcje.

Nazwa przeciążonego operatora to **operator** *x*, gdzie *x* jest operatorem, jak pojawia się w poniższej tabeli. Na przykład aby przeciążyć operator dodawania, należy zdefiniować funkcję o nazwie **operator +** . Podobnie aby przeciążać operator dodawania/przypisywania, **+=** , zdefiniuj funkcję o nazwie **operator + =** .

### <a name="redefinable-operators"></a>Operatory do przedefiniować

|Operator|Name (Nazwa)|Typ|
|--------------|----------|----------|
|**,**|Przecinek|Binarny|
|**!**|Logiczne NOT|Jednostk|
|**!=**|Nierówność|Binarny|
|**%**|Modulus|Binarny|
|**%=**|Modulo i przypisanie|Binarny|
|**&**|Bitowe ORAZ|Binarny|
|**&**|Adres|Jednostk|
|**&&**|Logicznego AND|Binarny|
|**&=**|Bitowe AND i przypisanie|Binarny|
|**( )**|Wywołanie funkcji|—|
|**( )**|Operator rzutowania|Jednostk|
|**&#42;**|Mnożenie|Binarny|
|**&#42;**|Odwołuje się do wskaźnika|Jednostk|
|**&#42;=**|Mnożenie i przypisanie|Binarny|
|**+**|Dodawanie|Binarny|
|**+**|Jednoargumentowy Plus|Jednostk|
|**++**|Zwiększ <sup>1</sup>|Jednostk|
|**+=**|Dodawanie i przypisanie|Binarny|
|**-**|Odejmowanie|Binarny|
|**-**|negacja jednoargumentowa|Jednostk|
|**--**|Zmniejszenie <sup>1</sup>|Jednostk|
|**-=**|Odejmowanie i przypisanie|Binarny|
|**->**|Wybór elementu członkowskiego|Binarny|
|**->&#42;**|Wybór wskaźnika do elementu członkowskiego|Binarny|
|**/**|Dzielenie|Binarny|
|**/=**|Dzielenie i przypisanie|Binarny|
|**\<**|Mniejsze niż|Binarny|
|**<<**|Przesunięcie w lewo|Binarny|
|**<<=**|Przypisanie przesunięcia w lewo|Binarny|
|**<=**|Mniejsze niż lub równe|Binarny|
|**=**|Przypisanie|Binarny|
|**==**|Równości|Binarny|
|**>**|Większe niż|Binarny|
|**>=**|Większe niż lub równe|Binarny|
|**>>**|Przesunięcie w prawo|Binarny|
|**>>=**|Przypisanie przesunięcia w prawo|Binarny|
|**[ ]**|Indeks dolny tablicy|—|
|**^**|Wyłączny lub|Binarny|
|**^=**|Wyłączność lub przypisanie|Binarny|
|**&#124;**|Bitowe alternatywne OR|Binarny|
|**&#124;=**|Bitowe OR alternatywne i przypisanie|Binarny|
|**&#124;&#124;**|Logicznego OR|Binarny|
|**~**|Uzupełnienie jedynkowe|Jednostk|
|**usuwanie**|Usuwanie|—|
|**new**|Nowa|—|
|operatory konwersji|operatory konwersji|Jednostk|

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

|Operator|Name (Nazwa)|
|-|-|
|**.**|Wybór elementu członkowskiego|
|**.&#42;**|Wybór wskaźnika do elementu członkowskiego|
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

Poniższy przykład przeciąża operator **+** , aby dodać dwie liczby zespolone i zwraca wynik.

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

## <a name="see-also"></a>Zobacz też

[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
