---
title: Operatory przypisania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/05/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- =
- '*='
- /=
- '%='
- +=
- -=
- <<=
- '>>='
- '&='
- ^=
- '|='
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], C++
- '&= operator'
- ^= operator
- += operator
- '>>= operator'
- '|= operator'
- operator>>=
- '*= operator'
- '%= operator'
- ^= operator
- operator >>=
- = operator
- -= operator
- /= operator
- <<= operator
ms.assetid: b028cf35-2ff1-4f14-9027-fd53ebec8aa0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1429bcb9f4002cb65cc14000d3bcf62004000566
ms.sourcegitcommit: b05cff71a8a6a8a4c7bbea1263fd0a711853f921
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49307922"
---
# <a name="assignment-operators"></a>Operatory przypisania

## <a name="syntax"></a>Składnia

*wyrażenie* *operator przypisania* *wyrażenia*

*operator przypisania* : jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>= * =, / = % =, +=,-= \< \<= >> = & = ^ =   \|=</strong>

## <a name="remarks"></a>Uwagi

Operatory przypisania przechowują wartość w obiekcie wyznaczonym przez lewy operand. Istnieją dwa rodzaje operacji przypisania:

1. *Przypisanie proste*, w którym wartość drugiego operandu jest przechowywana w obiekcie określonym przez pierwszy operand.

1. *przydział złożony*, w którym operacje arytmetyczne, przesunięcia lub operacji na poziomie bitowym są wykonywane przed zachowaniem wyniku.

Wszystkie operatory przypisania w tabeli poniżej, z wyjątkiem operatora =, są operatorami przypisania złożonego.

### <a name="assignment-operators"></a>Operatory przypisania

|Operator|Znaczenie|
|--------------|-------------|
|**=**|Przechowuje wartość drugiego operandu w obiekcie określonym przez pierwszy operand (przypisanie proste).|
|**\*=**|Mnoży wartość pierwszego operandu przez wartość drugiego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand.|
|**/=**|Dzieli wartość pierwszego operandu przez wartość drugiego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand.|
|**%=**|Wyznacza moduł wartości pierwszego operandu określonej przez wartość drugiego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand.|
|**+=**|Dodaje wartość drugiego operandu do wartości pierwszego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand.|
|**-=**|Odejmuje wartość drugiego operandu od wartości pierwszego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand.|
|**<\<=**|Przesuwa wartość pierwszego operandu w lewo o liczbę bitów określoną przez wartość drugiego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand.|
|**>>=**|Przesuwa wartość pierwszego operandu w prawo o liczbę bitów określoną przez wartość drugiego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand.|
|**&=**|Uzyskuje bitowe AND pierwszego i drugiego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand.|
|**^=**|Uzyskuje bitowe wykluczające OR pierwszego i drugiego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand.|
|**\|=**|Uzyskuje bitowe zawierające OR pierwszego i drugiego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand.|

**Słowa kluczowe operatora**

Trzy z operatorów przypisania złożonego mają odpowiedniki tekstowe. Są to:

|Operator|Odpowiednik|
|--------------|----------------|
|**&=**|`and_eq`|
|**\|=**|`or_eq`|
|**^=**|`xor_eq`|

Istnieją dwa sposoby dostępu do tych słów kluczowych operatora w programach: dołączanie pliku nagłówka `iso646.h`, lub kompilowanie z [/za](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora (Wyłącz rozszerzenia językowe).

## <a name="example"></a>Przykład

```cpp
// expre_Assignment_Operators.cpp
// compile with: /EHsc
// Demonstrate assignment operators
#include <iostream>
using namespace std;
int main() {
   int a = 3, b = 6, c = 10, d = 0xAAAA, e = 0x5555;

   a += b;      // a is 9
   b %= a;      // b is 6
   c >>= 1;      // c is 5
   d |= e;      // Bitwise--d is 0xFFFF

   cout  << "a = 3, b = 6, c = 10, d = 0xAAAA, e = 0x5555" << endl
         << "a += b yields " << a << endl
         << "b %= a yields " << b << endl
         << "c >>= 1 yields " << c << endl
         << "d |= e yields " << hex << d << endl;
}
```

## <a name="simple-assignment"></a>Przypisanie proste

Prosty operator przypisania (**=**) powoduje, że wartość drugiego operandu w obiekcie określonym przez pierwszy operand. Jeśli oba obiekty są typami arytmetycznymi, prawy operand jest konwertowany na typ po lewej stronie, przed zachowaniem wartości.

Obiekty **const** i **volatile** typy mogą być przypisane do l wartości typów, które są po prostu **volatile** lub które nie należą do żadnej **const** ani **volatile**.

Przypisanie do obiektów typu klasy (struktury, Unii i typy klas) jest wykonywane przez funkcję o nazwie `operator=`. Domyślne zachowanie tej funkcji operatora ma wykonywać kopię bitową; jednak to zachowanie może być modyfikowane przy użyciu przeciążonych operatorów. Zobacz [przeciążania operatora](../cpp/operator-overloading.md) Aby uzyskać więcej informacji. Ponadto może mieć typu klasy *przypisania kopiowania* i *Przenieś przypisania* operatorów. Aby uzyskać więcej informacji, zobacz [kopiowanie konstruktorów i operatory przypisania kopiowania](copy-constructors-and-copy-assignment-operators-cpp.md) i [konstruktory przenoszenia i operatory przypisania przenoszenia](move-constructors-and-move-assignment-operators-cpp.md).

Obiekt dowolnej jednoznacznej klasy pochodnej od danej klasy bazowej może być przypisany do obiektu klasy bazowej. Przeciwny warunek nie jest spełniony, ponieważ istnieje niejawna konwersja z klasy pochodnej do klasy bazowej, ale nie z klasy bazowej do klasy pochodnej. Na przykład:

```cpp
// expre_SimpleAssignment.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
class ABase
{
public:
    ABase() { cout << "constructing ABase\n"; }
};

class ADerived : public ABase
{
public:
    ADerived() { cout << "constructing ADerived\n"; }
};

int main()
{
    ABase aBase;
    ADerived aDerived;

    aBase = aDerived; // OK
    aDerived = aBase; // C2679
}
```

Przydziały do typów referencyjnych zachowują się tak, jakby przypisanie zostało wykonane do obiektu, do którego wskazuje odwołanie.

Dla obiektów typu klasy, przypisanie różni się od inicjowania. Aby zilustrować jak różne może być przypisanie i inicjowanie, należy rozważyć kod

```cpp
UserType1 A;
UserType2 B = A;
```

W poprzednim kodzie zaprezentowano inicjator; wywołuje on konstruktor dla `UserType2`, który pobiera argument typu `UserType1` Dany kod

```cpp
UserType1 A;
UserType2 B;

B = A;
```

instrukcja przypisania

```cpp
B = A;
```

może mieć jeden z następujących efektów:

- Wywołaj funkcję `operator=` dla `UserType2`, podana `operator=` jest dostarczana z `UserType1` argumentu.

- Wywołanie funkcji konwersji jawnej `UserType1::operator UserType2`, jeśli istnieje taka funkcja.

- Wywołanie konstruktora `UserType2::UserType2`, jeśli taki konstruktor istnieje, który przyjmuje argument `UserType1` i kopiuje wynik.

## <a name="compound-assignment"></a>Przydział złożony

Złożone operatory przypisania, jak pokazano w tabeli w [operatory przypisania](#assignment-operators), są określone w formie *e1* *op*= *e2*, gdzie *e1* jest modyfikowalną l wartością nie **const** typu i *e2* jest jednym z następujących czynności:

- Typ arytmetyczny

- Wskaźnik, jeśli *op* jest **+** lub **-**

*E1* *op*= *e2* formularz, który zachowuje się jak *e1* **=** *e1* *op* *e2*, ale *e1* jest oceniane tylko raz.

Przydział złożony, aby Typ wyliczany generuje komunikat o błędzie. Jeśli lewy operand jest typu wskaźnika, prawy operand musi być typem wskaźnika lub musi być wyrażeniem stałym, którego wynikiem jest 0. Jeśli lewy operand jest typu całkowitego, prawy operand nie musi być typu wskaźnika.

## <a name="result-of-assignment-operators"></a>Wynik dla operatorów przypisania

Operatory przypisania zwróć wartość obiektu określonego przez lewy argument operacji po przypisaniu. Wynikowy typ jest typem operandu po lewej stronie. Wynik wyrażenia przypisania zawsze jest l wartością. Te operatory mają łączność od prawej do lewej. Lewy operand musi być modyfikowalną l wartością.

W ANSI C wynik wyrażenia przypisania nie jest l wartością. W związku z tym, prawne wyrażenie C++ `(a += b) += c` jest niedozwolony w C.

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami dwuargumentowymi](../cpp/expressions-with-binary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory przypisania w języku C](../c-language/c-assignment-operators.md)
