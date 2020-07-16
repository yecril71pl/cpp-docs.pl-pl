---
title: Operatory przesunięcia w lewo i w prawo ( &gt; &gt; i &lt; &lt; )
ms.date: 08/13/2018
f1_keywords:
- <<
- '>>'
helpviewer_keywords:
- << operator [C++], with specific objects
- left shift operators [C++]
- right shift operators [C++]
- bitwise-shift operators [C++]
- '>> operator'
- shift operators [C++]
- operators [C++], shift
ms.assetid: 25fa0cbb-5fdd-4657-8745-b35f7d8f1606
ms.openlocfilehash: 7cde299d305219f2bd0e53a9f19c2ca35a8c7b69
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404773"
---
# <a name="left-shift-and-right-shift-operators-gtgt-and-ltlt"></a>Operatory przesunięcia w lewo i w prawo ( &gt; &gt; i &lt; &lt; )

Operatory przesunięcia bitowego to operator przesunięcia w prawo ( **&gt;&gt;** ), który przenosi bity *przesunięcia* w prawo i operator przesunięcia w lewo ( **&lt;&lt;** ), który przenosi bity *przesunięcia* w lewo. <sup>1</sup>

## <a name="syntax"></a>Składnia

> *wyrażenie* `<<` przesunięcia *wyrażenie addytywne*\
> *wyrażenie* `>>` przesunięcia *wyrażenie addytywne*

## <a name="remarks"></a>Uwagi

> [!IMPORTANT]
> Poniższe opisy i przykłady są prawidłowe w systemie Windows dla architektury x86 i x64. Implementacja operatorów przesunięcia w lewo i przesunięcia w prawo jest znacznie inna w systemie Windows dla urządzeń ARM. Aby uzyskać więcej informacji, zobacz sekcję "operatory przesunięcia" wpisu w blogu [Hello ARM](https://devblogs.microsoft.com/cppblog/hello-arm-exploring-undefined-unspecified-and-implementation-defined-behavior-in-c/) .

## <a name="left-shifts"></a>Przesunięcia w lewo

Operator przesunięcia w lewo powoduje, że bity w *przesunięciu shift-expression* są przesuwane w lewo o liczbę pozycji określoną przez *dodatek*. Pozycje bitów, które zostały zwolnione w wyniku operacji przesunięcia, są wypełniane przez zera. Przesunięcie w lewo to przesunięcie logiczne (bity, które zostaną przesunięte poza koniec, są odrzucane, łącznie z bitem znaku). Aby uzyskać więcej informacji na temat rodzajów przesunięć bitowych, zobacz [bitowe przesunięcia](https://en.wikipedia.org/wiki/Bitwise_shift).

W poniższym przykładzie pokazano operacje przesunięcia w lewo przy użyciu liczb bez znaku. W przykładzie pokazano, co się dzieje z bitami, poprzez reprezentowanie wartości jako zestawu bitów. Aby uzyskać więcej informacji, zobacz [Klasa bitset](../standard-library/bitset-class.md).

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned short short1 = 4;
    bitset<16> bitset1{short1};   // the bitset representation of 4
    cout << bitset1 << endl;  // 0b00000000'00000100

    unsigned short short2 = short1 << 1;     // 4 left-shifted by 1 = 8
    bitset<16> bitset2{short2};
    cout << bitset2 << endl;  // 0b00000000'00001000

    unsigned short short3 = short1 << 2;     // 4 left-shifted by 2 = 16
    bitset<16> bitset3{short3};
    cout << bitset3 << endl;  // 0b00000000'00010000
}
```

Jeśli przesuniesz liczbę ze znakiem w lewo, tak że bit znaku zostanie objęty zmianą, wynik będzie nieokreślony. Poniższy przykład pokazuje, co się stanie, gdy 1 bit zostanie przesunięty w dół do pozycji bitu znaku.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short short1 = 16384;
    bitset<16> bitset1(short1);
    cout << bitset1 << endl;  // 0b01000000'00000000

    short short3 = short1 << 1;
    bitset<16> bitset3(short3);  // 16384 left-shifted by 1 = -32768
    cout << bitset3 << endl;  // 0b10000000'00000000

    short short4 = short1 << 14;
    bitset<16> bitset4(short4);  // 4 left-shifted by 14 = 0
    cout << bitset4 << endl;  // 0b00000000'00000000
}
```

## <a name="right-shifts"></a>Przesunięcia w prawo

Operator przesunięcia w prawo powoduje, że wzorzec bitowy w *przesunięciu shift-expression* zostanie przesunięty w prawo o liczbę pozycji określoną przez *dodatek*. W przypadku liczb bez znaku, pozycje bitów, które zostały zwolnione w wyniku operacji przesunięcia, są wypełniane przez zera. W przypadku liczb ze znakiem, bit znaku jest używany do wypełniania opuszczonych pozycji bitów. Innymi słowy, jeśli liczba jest dodatnia, używane jest 0, a jeśli liczba jest ujemna, używane jest 1.

> [!IMPORTANT]
> Wynik przesunięcia w prawo liczby ujemnej ze znakiem zależy od implementacji. Chociaż kompilator języka Microsoft C++ używa bitu znaku do wypełniania pozycji opuszczone bit, nie ma gwarancji, że inne implementacje również są takie same.

W tym przykładzie pokazano operacje przesunięcia w prawo przy użyciu liczb bez znaku:

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned short short11 = 1024;
    bitset<16> bitset11{short11};
    cout << bitset11 << endl;     // 0b00000100'00000000

    unsigned short short12 = short11 >> 1;  // 512
    bitset<16> bitset12{short12};
    cout << bitset12 << endl;     // 0b00000010'00000000

    unsigned short short13 = short11 >> 10;  // 1
    bitset<16> bitset13{short13};
    cout << bitset13 << endl;     // 0b00000000'00000001

    unsigned short short14 = short11 >> 11;  // 0
    bitset<16> bitset14{short14};
    cout << bitset14 << endl;     // 0b00000000'00000000
}
```

W kolejnym przykładzie pokazano operacje przesunięcia w prawo przy użyciu liczb dodatnich ze znakiem.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short short1 = 1024;
    bitset<16> bitset1(short1);
    cout << bitset1 << endl;     // 0b00000100'00000000

    short short2 = short1 >> 1;  // 512
    bitset<16> bitset2(short2);
    cout << bitset2 << endl;     // 0b00000010'00000000

    short short3 = short1 >> 11;  // 0
    bitset<16> bitset3(short3);
    cout << bitset3 << endl;     // 0b00000000'00000000
}
```

W następnym przykładzie pokazano operacje przesunięcia w prawo przy użyciu ujemnych liczb całkowitych ze znakiem.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short neg1 = -16;
    bitset<16> bn1(neg1);
    cout << bn1 << endl;  // 0b11111111'11110000

    short neg2 = neg1 >> 1; // -8
    bitset<16> bn2(neg2);
    cout << bn2 << endl;  // 0b11111111'11111000

    short neg3 = neg1 >> 2; // -4
    bitset<16> bn3(neg3);
    cout << bn3 << endl;  // 0b11111111'11111100

    short neg4 = neg1 >> 4; // -1
    bitset<16> bn4(neg4);
    cout << bn4 << endl;  // 0b11111111'11111111

    short neg5 = neg1 >> 5; // -1
    bitset<16> bn5(neg5);
    cout << bn5 << endl;  // 0b11111111'11111111
}
```

## <a name="shifts-and-promotions"></a>Przesunięcia i awansowania

Wyrażenia po obu stronach operatora przesunięcia muszą być typami całkowitoliczbowymi. Promocje integralne są wykonywane zgodnie z zasadami opisanymi w [standardowym konwersji](standard-conversions.md). Typ wyniku jest taki sam jak typ awansowanego *wyrażenia przesunięcia*.

W poniższym przykładzie zmienna typu **char** jest podwyższana do liczby **całkowitej**.

```cpp
#include <iostream>
#include <typeinfo>

using namespace std;

int main() {
    char char1 = 'a';

    auto promoted1 = char1 << 1;   // 194
    cout << typeid(promoted1).name() << endl;  // int

    auto promoted2 = char1 << 10;  // 99328
    cout << typeid(promoted2).name() << endl;  // int
}
```

## <a name="additional-details"></a>Dodatkowe szczegóły

Wynik operacji przesunięcia jest nieokreślony, jeśli *dodatek typu "* wartość ujemna" lub " *wyrażenie addytywne"* jest większe lub równe liczbie bitów w *wyrażeniu shift-expression*(promowany). Nie wykonano żadnej operacji przesunięcia, jeśli *dodatek typu wyrażenie* ma wartość 0.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned int int1 = 4;
    bitset<32> b1{int1};
    cout << b1 << endl;    // 0b00000000'00000000'00000000'00000100

    unsigned int int2 = int1 << -3;  // C4293: '<<' : shift count negative or too big, undefined behavior
    unsigned int int3 = int1 >> -3;  // C4293: '>>' : shift count negative or too big, undefined behavior
    unsigned int int4 = int1 << 32;  // C4293: '<<' : shift count negative or too big, undefined behavior
    unsigned int int5 = int1 >> 32;  // C4293: '>>' : shift count negative or too big, undefined behavior
    unsigned int int6 = int1 << 0;
    bitset<32> b6{int6};
    cout << b6 << endl;    // 0b00000000'00000000'00000000'00000100 (no change)
}
```

## <a name="footnotes"></a>Przypisy dolne

<sup>1</sup> poniżej znajduje się opis operatorów przesunięcia w specyfikacji ISO języka c++ 11 (INCITS/ISO/IEC 14882-2011 [2012]), sekcje 5.8.2 i 5.8.3.

Wartość `E1 << E2` jest `E1` przysuniętą do lewej `E2` pozycji bitów; opuszczone bity są wypełnione zerem. Jeśli `E1` ma typ bez znaku, wartość wyniku jest **E1 × 2**<sup>**E2**</sup>, a zmniejszenie modulo o jeden więcej niż wartość maksymalna, którą można przedstawić w typie wyniku. W przeciwnym razie, jeśli `E1` ma typ ze znakiem i wartość nieujemną, a **E1 × 2**<sup>**E2**</sup> można reprezentować w odpowiadającym typie niepodpisanym typu wyniku, wówczas ta wartość jest konwertowana na typ wyniku, jest wartością wynikową; w przeciwnym razie zachowanie jest niezdefiniowane.

Wartość `E1 >> E2` jest `E1` przysuniętą do prawej `E2` pozycji bitów. Jeśli `E1` ma typ bez znaku lub `E1` ma typ ze znakiem i wartość nieujemną, wartość wyniku jest integralną częścią ilorazu **E1/2**<sup>**E2**</sup>. Jeśli `E1` ma typ ze znakiem i wartość ujemną, wynikowa wartość jest definiowana przez implementację.

## <a name="see-also"></a>Zobacz też

[Wyrażenia z operatorami dwuargumentowymi](../cpp/expressions-with-binary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
