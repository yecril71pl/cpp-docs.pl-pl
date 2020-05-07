---
title: Operatory logiczne języka C
ms.date: 06/14/2018
helpviewer_keywords:
- logical operators, expression sequence points
- logical operators, C
- logical AND operator
- '|| operator'
- operators [C], logical
- short-circuit evaluation
- '&& operator'
- logical OR operator
ms.assetid: c0a4e766-ad56-4300-bf76-b28dc0e19b43
ms.openlocfilehash: 5df0c0f16bdf298c47a6a0699ec10c7392ab84ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326589"
---
# <a name="c-logical-operators"></a>Operatory logiczne języka C

Operatory logiczne wykonują operacje logiczne-i**&&**() i logiczne-lub**||**().

## <a name="syntax"></a>Składnia

*wyrażenie logiczne-and-Expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie włączne-lub-*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie koniunkcji logicznej i wyrażenia***&&***włącznie z* wyrażeniem or    

*wyrażenie logiczne or*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie logiczne-AND-Expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;wyrażenie *logiczne-and-* Expression **&#124;&#124;** *logiczne i wyrażenie*    

## <a name="remarks"></a>Uwagi

Operatory logiczne nie wykonują zwykłych konwersji arytmetycznych. Zamiast tego sprawdzają każdy operand w warunkach równoważności równy 0. Wynikiem operacji logicznej jest 0 lub 1. Typ wyniku to **int**.

Operatory logiczne języka C są opisane poniżej:

|Operator|Opis|
|--------------|-----------------|
|**&&**|Operator logiczny AND tworzy wartość 1, jeśli oba operandy mają wartości niezerowe. Jeśli oba operandy są równe 0, wynik wynosi 0. Jeśli pierwszy operand operacji logicznej i jest równy 0, drugi operand nie jest obliczany.|
|**&#124;&#124;**|Operator logiczny OR wykonuje operację włączania lub dla jego operandów. Wynik jest równy 0, jeśli oba operandy mają 0 wartości. Jeśli każdy operand ma wartość różną od zera, wynikiem jest 1. Jeśli pierwszy operand operacji logicznej OR ma wartość różną od zera, drugi operand nie jest obliczany.|

Argumenty operacji logicznej i logicznej są oceniane od lewej do prawej. Jeśli wartość pierwszego operandu jest wystarczająca do określenia wyniku operacji, drugi operand nie jest obliczany. Jest to tzw. "Ocena krótkoterminowa". Po pierwszym operandzie istnieje punkt sekwencji. Zobacz [punkty sekwencji](../c-language/c-sequence-points.md) , aby uzyskać więcej informacji.

## <a name="examples"></a>Przykłady

Poniższe przykłady ilustrują operatory logiczne:

```C
int w, x, y, z;

if ( x < y && y < z )
    printf( "x is less than z\n" );
```

W tym przykładzie funkcja **printf** jest wywoływana, aby wydrukować komunikat, jeśli `x` jest mniejszy `y` niż i `y` jest mniejszy niż. `z` Jeśli `x` jest większy niż `y`, drugi operand (`y < z`) nie jest szacowany i niczego nie wydrukowane. Należy zauważyć, że może to spowodować problemy w przypadkach, gdy drugi operand ma efekty uboczne, które są używane z jakiegoś innego powodu.

```C
printf( "%d" , (x == w || x == y || x == z) );
```

W tym przykładzie, jeśli `x` jest `w`równe albo `y`,, lub `z`, drugi argument funkcji **printf** ma wartość true, a wartość 1 jest drukowana. W przeciwnym razie zostanie wyznaczona wartość false i zostanie wydrukowany wynik 0. Gdy tylko jeden z warunków zwróci wartość true, ocena zostanie przerwana.

## <a name="see-also"></a>Zobacz też

- [Operator logiczny AND: &&](../cpp/logical-and-operator-amp-amp.md)
- [Operator logiczny OR:  &#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)
