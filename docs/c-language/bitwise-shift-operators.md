---
title: Operatory przesunięcia bitowego
ms.date: 10/18/2018
helpviewer_keywords:
- operators [C++], bitwise
- shift operators, bitwise
- bitwise-shift operators
- operators [C++], shift
ms.assetid: d0485785-5c72-47e1-a7c0-0adde03ade23
ms.openlocfilehash: d0873e3975e69bbfac01d437006561f0bf88ee31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485361"
---
# <a name="bitwise-shift-operators"></a>Operatory przesunięcia bitowego

Operatory przesunięcia shift ich pierwszego operandu w lewo (**&lt;&lt;**) lub w prawo (**>>**) przez liczbę pozycji określa drugiego operandu.

## <a name="syntax"></a>Składnia

*SHIFT-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*SHIFT-expression* **&lt; &lt;** *additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*SHIFT-expression* **>>** *additive-expression*

Oba operandy muszą być wartości całkowitych. Te operatory wykonywać popularne konwersje arytmetyczne; Typ wyniku jest typem lewego operandu po konwersji.

Dla leftward przesunięcia odpowiednich pozycje opuszczonych bitów są ustawione na 0. Dla rightward przesunięcia pozycje opuszczonych bitów po lewej stronie są wypełnione w zależności od typu pierwszego operandu po konwersji. Jeśli typ jest `unsigned`, są one ustawione na 0. W przeciwnym razie są wypełnione przy użyciu kopii bitu znaku. Dla operatorów przesunięcia w lewo bez przepełnienia, instrukcja

```C
expr1 << expr2
```

jest odpowiednikiem mnożenia przez wartość 2<sup>Wyr2</sup>. Dla operatorów przesunięcia w prawo

```C
expr1 >> expr2
```

jest odpowiednikiem dzielenie przez 2<sup>Wyr2</sup> Jeśli `expr1` jest podpisany lub ma wartość nieujemną.

Wynik operacji przesunięcia jest niezdefiniowana, jeśli drugi argument jest ujemna, czy prawy operand jest większa lub równa szerokości w bitach promowanego operandu po lewej stronie.

Ponieważ konwersje wykonywane przez shift operatory nie są oferowane dla przepełnienia lub warunków niedomiaru, informacje mogą zostać utracone, jeśli wynik operacji przesunięcia nie może być przedstawiony w typie pierwszego operandu po konwersji.

```C
unsigned int x, y, z;

x = 0x00AA;
y = 0x5500;

z = ( x << 8 ) + ( y >> 8 );
```

W tym przykładzie `x` zostanie przesunięty w lewo pozycje osiem i `y` jest przesuniętych bezpośrednio osiem pozycji. Przesuniętych wartości są dodawane, dzięki czemu 0xAA55 i przypisane do `z`.

Przesunięcie wartości ujemnej po prawej stronie daje połowa wartość pierwotną, zaokrąglona w dół. Na przykład -253 (binarne 11111111 00000011) przesunięte tworzy odpowiednie jeden bit -127 (binarne 11111111 10000001). Dodatnią 253 przesunięcia w prawo do produkcji +126.

Przesunięcia w prawo zachować bitu znaku. Liczba całkowita ze znakiem przenosi bezpośrednio, ustaw pozostaje najbardziej znaczący bit. Gdy liczbą całkowitą bez znaku przenosi bezpośrednio, najbardziej znaczący bit jest wyczyszczone.

## <a name="see-also"></a>Zobacz też

[Operatory przesunięcia w lewo i w prawo (>> i <<)](../cpp/left-shift-and-right-shift-operators-input-and-output.md)