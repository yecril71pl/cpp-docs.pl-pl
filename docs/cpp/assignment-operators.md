---
title: Operatory przypisania
description: Składnia operatorów przypisania języka standardowego w języku C++ i użycie.
ms.date: 07/24/2020
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
ms.openlocfilehash: 91346d06c6fab4f3cd83c5318c88e738daf8d249
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229223"
---
# <a name="assignment-operators"></a>Operatory przypisania

## <a name="syntax"></a>Składnia

*wyrażenie* przypisania *wyrażenia* *operatora*

*przypisanie — operator*: jeden z<br/>
&emsp;**`=`**&emsp;**`*=`**&emsp;**`/=`**&emsp;**`%=`**&emsp;**`+=`**&emsp;**`-=`**&emsp;**`<<=`**&emsp;**`>>=`**&emsp;**`&=`**&emsp;**`^=`**&emsp;**`|=`**

## <a name="remarks"></a>Uwagi

Operatory przypisania przechowują wartość w obiekcie określonym przez lewy argument operacji. Istnieją dwa rodzaje operacji przypisania:

- *przypisanie proste*, w którym wartość drugiego operandu jest przechowywana w obiekcie określonym przez pierwszy operand.

- *przypisanie złożone*, w którym wykonywane jest operacje arytmetyczne, Shift lub bitowe przed zapisaniem wyniku.

Wszystkie operatory przypisania w poniższej tabeli, z wyjątkiem **`=`** operatora, są operatorami przypisania złożonego.

### <a name="assignment-operators-table"></a>Tabela operatorów przypisania

| Operator | Znaczenie |
|--|--|
| **`=`** | Przechowuje wartość drugiego operandu w obiekcie określonym przez pierwszy operand (przypisanie proste). |
| **`*=`** | Mnoży wartość pierwszego operandu przez wartość drugiego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand. |
| **`/=`** | Dzieli wartość pierwszego operandu przez wartość drugiego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand. |
| **`%=`** | Wyznacza moduł wartości pierwszego operandu określonej przez wartość drugiego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand. |
| **`+=`** | Dodaje wartość drugiego operandu do wartości pierwszego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand. |
| **`-=`** | Odejmuje wartość drugiego operandu od wartości pierwszego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand. |
| **`<<=`** | Przesuwa wartość pierwszego operandu w lewo o liczbę bitów określoną przez wartość drugiego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand. |
| **`>>=`** | Przesuwa wartość pierwszego operandu w prawo o liczbę bitów określoną przez wartość drugiego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand. |
| **`&=`** | Uzyskuje bitowe AND pierwszego i drugiego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand. |
| **`^=`** | Uzyskuje bitowe wykluczające OR pierwszego i drugiego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand. |
| **`|=`** | Uzyskuje bitowe zawierające OR pierwszego i drugiego operandu; przechowuje wynik w obiekcie określonym przez pierwszy operand. |

### <a name="operator-keywords"></a>Słowa kluczowe operatora

Trzy złożone operatory przypisania mają odpowiedniki słów kluczowych. Oto one:

| Operator | Odpowiednik |
|--|--|
| **`&=`** | **`and_eq`** |
| **`|=`** | **`or_eq`** |
| **`^=`** | **`xor_eq`** |

Język C++ określa te słowa kluczowe operatora jako alternatywne pisowni dla operatorów przypisania złożonego. W języku C alternatywna pisownia jest podawana jako makra w \<iso646.h> nagłówku. W języku C++ pisownia alternatywna to słowa kluczowe; Użycie \<iso646.h> lub odpowiednik języka C++ \<ciso646> jest przestarzałe. W programie Microsoft C++ [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Opcja kompilatora or jest wymagana do włączenia alternatywnej pisowni.

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

Prosty operator przypisania ( **`=`** ) powoduje, że wartość drugiego operandu, który ma być przechowywany w obiekcie określonym przez pierwszy operand. Jeśli oba obiekty są typu arytmetycznego, prawy operand jest konwertowany na typ po lewej stronie przed zapisaniem wartości.

Obiekty **`const`** i **`volatile`** typy można przypisywać do l-wartości typów, które są tylko **`volatile`** lub nie są **`const`** lub **`volatile`** .

Przypisanie do obiektów typu klasy ( **`struct`** , **`union`** , i **`class`** ) jest wykonywane przez funkcję o nazwie `operator=` . Domyślne zachowanie tej funkcji operatora ma wykonywać kopię bitową; jednak to zachowanie może być modyfikowane przy użyciu przeciążonych operatorów. Aby uzyskać więcej informacji, zobacz [przeciążanie operatora](../cpp/operator-overloading.md). Typy klas mogą także mieć *przypisanie kopiowania* i operatory *przypisania przenoszenia* . Aby uzyskać więcej informacji, zobacz [Kopiowanie konstruktorów i kopiowanie operatorów przypisania](copy-constructors-and-copy-assignment-operators-cpp.md) oraz [przenoszenie konstruktorów i przenoszenie operatorów przypisania](move-constructors-and-move-assignment-operators-cpp.md).

Obiekt dowolnej jednoznacznej klasy pochodnej od danej klasy bazowej może być przypisany do obiektu klasy bazowej. Odwrócenie nie jest prawdziwe, ponieważ istnieje niejawna konwersja z klasy pochodnej na klasę bazową, ale nie z klasy bazowej na klasę pochodną. Na przykład:

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

- Wywołaj funkcję `operator=` dla `UserType2` , dostarczono `operator=` z `UserType1` argumentem.

- Wywołanie funkcji konwersji jawnej `UserType1::operator UserType2`, jeśli istnieje taka funkcja.

- Wywołanie konstruktora `UserType2::UserType2`, jeśli taki konstruktor istnieje, który przyjmuje argument `UserType1` i kopiuje wynik.

## <a name="compound-assignment"></a>Przypisanie złożone

Operatory przypisania złożonego są wyświetlane w [tabeli operatorów przypisania](#assignment-operators-table). Te operatory mają formę *E1* *op* =  *E2*, gdzie *E1* jest **`const`** niemodyfikowalną literą l-Value i *E2* jest:

- typ arytmetyczny

- wskaźnik, jeśli *op* jest **`+`** lub**`-`**

Formularz *E1* *op* =  *E2* zachowuje się jako *E1* **`=`** *E1* *op* *e2*, ale *E1* jest oceniane tylko raz.

Przypisanie złożone do typu wyliczeniowego generuje komunikat o błędzie. Jeśli argument operacji po lewej stronie jest typu wskaźnika, prawy operand musi być typu wskaźnika lub musi być wyrażeniem stałym, które ma wartość 0. Gdy argument operacji po lewej stronie jest typu całkowitego, prawy operand nie może być typu wskaźnika.

## <a name="result-of-assignment-operators"></a>Wynik operatorów przypisania

Operatory przypisania zwracają wartość obiektu określonego przez lewy operand po przypisaniu. Typ wynikowy jest typem lewego operandu. Wynikiem wyrażenia przypisania jest zawsze l-wartość. Te operatory mają łączność od prawej do lewej. Lewy operand musi być modyfikowalną wartością l.

W standardzie ANSI C, wynik wyrażenia przypisania nie jest l-wartością. Oznacza to, że prawne wyrażenie języka C++ `(a += b) += c` nie jest dozwolone w języku C.

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami binarnymi](../cpp/expressions-with-binary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i łączność języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[operatory przypisania w języku C](../c-language/c-assignment-operators.md)
