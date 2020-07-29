---
title: Operatory przesunięcia bitowego
ms.date: 10/18/2018
helpviewer_keywords:
- operators [C++], bitwise
- shift operators, bitwise
- bitwise-shift operators
- operators [C++], shift
ms.assetid: d0485785-5c72-47e1-a7c0-0adde03ade23
ms.openlocfilehash: a8a72a8657daec39bb042fea744b5f97d3b34009
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226532"
---
# <a name="bitwise-shift-operators"></a>Operatory przesunięcia bitowego

Operatory przesunięcia przesuwają swój pierwszy operand w lewo ( **&lt;&lt;** ) lub prawą ( **>>** ) o liczbę pozycji określanych przez drugiego operandu.

## <a name="syntax"></a>Składnia

*wyrażenie przesunięcia*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie addytywne*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie* **&lt;&lt;** przesunięcia *wyrażenie addytywne*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie* **>>** przesunięcia *wyrażenie addytywne*

Oba operandy muszą być wartościami całkowitymi. Operatory te wykonują zwykle konwersje arytmetyczne; Typ wyniku jest typem lewego operandu po konwersji.

W przypadku zmian leftward, bity opuszczone w prawo są ustawione na 0. W przypadku rightward Shift opuszczone lewe bity są wypełniane na podstawie typu pierwszego operandu po konwersji. Jeśli typ ma wartość **`unsigned`** , są ustawione na 0. W przeciwnym razie są wypełniane jako kopie bitu znaku. Dla operatorów przesunięcia w lewo bez przepełnienia, instrukcja

```C
expr1 << expr2
```

jest równoznaczne z mnożeniem przez 2<sup>expr2</sup>. Dla operatorów przesunięcia w prawo,

```C
expr1 >> expr2
```

jest odpowiednikiem dzielenia przez 2<sup>expr2</sup> , jeśli `expr1` jest niepodpisana lub ma nieujemną wartość.

Wynik operacji przesunięcia jest nieokreślony, jeśli drugi operand jest ujemny lub jeśli prawy operand jest większy lub równy szerokości w bitach najbardziej wynoszącego lewego operandu.

Ponieważ konwersje wykonywane przez operatory przesunięcia nie zapewniają dla warunków przeciążenia lub niedopełnienia, informacje mogą zostać utracone, jeśli wynik operacji przesunięcia nie może być reprezentowany w typie pierwszego operandu po konwersji.

```C
unsigned int x, y, z;

x = 0x00AA;
y = 0x5500;

z = ( x << 8 ) + ( y >> 8 );
```

W tym przykładzie `x` przesuwane są lewe osiem pozycji i `y` przesuwane są odpowiednie osiem pozycji. Przesunięte wartości są dodawane, dające 0xAA55 i przypisane do `z` .

Przesunięcie wartości ujemnej na prawo daje połowę wartości oryginalnej, zaokrąglonej w dół. Na przykład-253 (binarny 11111111 00000011) przesunięcie w prawo o jeden bit wygeneruje-127 (binarny 11111111 10000001). Pozytywna 253 przesunie się bezpośrednio do produkcji + 126.

Prawy Shift zachowuje bit znaku. Gdy liczba całkowita ze znakiem zostanie przesunięta w prawo, to najbardziej znaczący bit pozostaje ustawiony. Gdy liczba całkowita bez znaku zostaje przesunięta w prawo, najbardziej znaczący bit jest wyczyszczony.

## <a name="see-also"></a>Zobacz także

[Operatory przesunięcia w lewo i w prawo (>> i <<)](../cpp/left-shift-and-right-shift-operators-input-and-output.md)
