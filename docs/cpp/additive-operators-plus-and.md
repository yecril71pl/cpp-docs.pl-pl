---
title: 'Operatory dodawania: + i -'
ms.date: 11/04/2016
f1_keywords:
- +
- '-'
helpviewer_keywords:
- operators [C++], addition
- subtraction operator [C++], additive operators
- + operator [C++], additive operators
- additive operators [C++]
- arithmetic operators [C++], additive operators
- '- operator [C++], additive operators in C++'
ms.assetid: d4afafe7-e201-4c69-a649-37f17756e784
ms.openlocfilehash: 2601debb0a21c4ab9cdcedb25b26085a1aff0a1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370193"
---
# <a name="additive-operators--and--"></a>Operatory dodawania: + i -

## <a name="syntax"></a>Składnia

```
expression + expression
expression - expression
```

## <a name="remarks"></a>Uwagi

Operatorami dodatków są:

- Dodatek**+**( )

- Odejmowanie**-**( )

Te operatory dwuargumentowe mają łączność od lewej do prawej.

Operatory dodatków przyjmują argumenty typów arytmetycznych lub wskaźników. Wynikiem dodania (**+**) operator jest suma operands. Wynikiem operatora odejmowania**-**( ) jest różnica między operandami. Jeśli jeden lub oba argumenty są wskaźnikami, muszą być wskaźnikami do obiektów, a nie do funkcji. Jeśli oba argumenty są wskaźnikami, wyniki nie są znaczące, chyba że oba są wskaźnikami do obiektów w tej samej tablicy.

Operatorzy dodatków przyjmują opery typów *arytmetycznych,* *integralnych*i *skalarnych.* Są one zdefiniowane w poniższej tabeli.

### <a name="types-used-with-additive-operators"></a>Typy stosowane z operatorami dodatków

|Typ|Znaczenie|
|----------|-------------|
|*Arytmetyczne*|Typy integralne i pływające są zbiorczo nazywane typami "arytmetycznymi".|
|*Integralną*|Typy char i int wszystkich rozmiarów (długie, krótkie) i wyliczenia są typami "integralnymi".|
|*Wartość skalarna*|Skalarne operandy są operandami typu arytmetycznego lub wskaźnikowego.|

Kombinacje prawne dla tych podmiotów to:

*arytmetyka* + *arytmetyczna*

*skalarna* + *integralna*

*integralny* + *skalarny*

*arytmetyka* - *arytmetyczna*

*skalarna* - *skalarna*

Należy zauważyć, że dodawanie i odejmowanie nie są równoważne operacje.

Jeśli oba argumenty mają typ arytmetyczny, konwersje opisane w [konwersjach standardowych](standard-conversions.md) są stosowane do argumentów, a wynik jest typu przekonwertowanego.

## <a name="example"></a>Przykład

```cpp
// expre_Additive_Operators.cpp
// compile with: /EHsc
#include <iostream>
#define SIZE 5
using namespace std;
int main() {
   int i = 5, j = 10;
   int n[SIZE] = { 0, 1, 2, 3, 4 };
   cout  << "5 + 10 = " << i + j << endl
         << "5 - 10 = " << i - j << endl;

   // use pointer arithmetic on array

   cout << "n[3] = " << *( n + 3 ) << endl;
}
```

## <a name="pointer-addition"></a>Dodanie wskaźnika

Jeśli jeden z argumentów w operacji dodawania jest wskaźnikiem do tablicy obiektów, drugi musi być typu integralnego. Wynikiem jest wskaźnik, który jest tego samego typu co oryginalny wskaźnik i który wskazuje na inny element tablicy. Następujący fragment kodu ilustruje tę koncepcję:

```cpp
short IntArray[10]; // Objects of type short occupy 2 bytes
short *pIntArray = IntArray;

for( int i = 0; i < 10; ++i )
{
    *pIntArray = i;
    cout << *pIntArray << "\n";
    pIntArray = pIntArray + 1;
}
```

Chociaż wartość całkowita 1 `pIntArray`jest dodawana do , nie oznacza "dodać 1 do adresu"; oznacza to raczej "dostosować wskaźnik do punktu do następnego obiektu w tablicy", `sizeof( int )`który dzieje się 2 bajty (lub) od.

> [!NOTE]
> Kod formularza `pIntArray = pIntArray + 1` jest rzadko spotykany w programach C++; aby wykonać przyrost, te formularze są `pIntArray++` `pIntArray += 1`preferowane: lub .

## <a name="pointer-subtraction"></a>Odejmowanie wskaźnika

Jeśli oba argumenty są wskaźnikami, wynikiem odejmowania jest różnica (w elementach tablicy) między operandami. Wyrażenie odejmowania daje podpisany integralny `ptrdiff_t` wynik typu (zdefiniowany w standardzie obejmują plik \<stddef.h>).

Jeden z operandów może być typu integralnego, o ile jest to drugi operand. Wynik odejmowania jest tego samego typu co oryginalny wskaźnik. Wartość odejmowania jest wskaźnikiem do (*n* - *i*) th elementu tablicy, gdzie *n* jest elementem wskazanym przez oryginalny wskaźnik *i* i jest integralną wartością drugiego operandu.

## <a name="see-also"></a>Zobacz też

[Wyrażenia z operatorami dwuargumentowymi](../cpp/expressions-with-binary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory dodawania języka C](../c-language/c-additive-operators.md)
