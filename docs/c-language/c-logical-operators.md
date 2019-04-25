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

Operatory logiczne wykonać logiczny — i (**&&**) i logiczne OR (**||**) operacji.

## <a name="syntax"></a>Składnia

*logical-AND-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inclusive-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-AND-expression*  **&&**  *inclusive-OR-expression*

*logical-OR-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-AND-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*  **&#124;&#124;**  *logical-AND-expression*

## <a name="remarks"></a>Uwagi

Operatory logiczne nie wykonuje zwykle konwersje arytmetyczne. Zamiast tego należy ocenić ich każdy argument pod względem jego odpowiednik na 0. Wynik operacji logicznej jest równa 0 lub 1. Typ wyniku jest **int**.

Operatory logiczne języka C zostały opisane poniżej:

|Operator|Opis|
|--------------|-----------------|
|**&&**|Logiczny — i operator generuje wartość 1, jeśli oba operandy ma wartość różną od zera wartości. Jeśli jeden z operandów jest równa 0, wynik jest równy 0. Jeśli pierwszy argument logiczny — i operacji jest równa 0, drugi operand nie jest oceniany.|
|**&#124;&#124;**|Operator logiczny OR wykonuje operację włącznie lub na swoich argumentów. Wynikiem jest 0, jeśli oba operandy wartości 0. Jeśli jeden z operandów ma wartość różną od zera, wynik jest 1. Drugi argument nie jest oceniany, jeśli pierwszy argument operacji operatora logicznego OR ma wartość różną od zera.|

Argumenty operacji logiczny — i i wyrażenia logiczne OR są obliczane od lewej do prawej. Jeśli wartość pierwszego operandu jest wystarczające, aby ustalić wyniku operacji, drugi argument nie jest oceniany. Jest to tak zwane "zwarcia." Brak punktu sekwencji po pierwszy operand. Zobacz [punktów sekwencji](../c-language/c-sequence-points.md) Aby uzyskać więcej informacji.

## <a name="examples"></a>Przykłady

Poniższe przykłady ilustrują operatory logiczne:

```C
int w, x, y, z;

if ( x < y && y < z )
    printf( "x is less than z\n" );
```

W tym przykładzie **printf** funkcja jest wywoływana, aby wydrukować wiadomość, jeśli `x` jest mniejsza niż `y` i `y` jest mniejsza niż `z`. Jeśli `x` jest większa niż `y`, drugi operand (`y < z`) nie jest oceniany i nic nie zostanie wyświetlone. Należy pamiętać, że może to spowodować problemy w przypadkach, gdy drugi argument operacji ma efekty uboczne, które są trwa skorzystała z innego powodu.

```C
printf( "%d" , (x == w || x == y || x == z) );
```

W tym przykładzie Jeśli `x` jest równa albo `w`, `y`, lub `z`, drugi argument **printf** funkcja zwraca wartość true, a wartość 1, wydrukowaniu. W przeciwnym razie zwróci wartość false, a wartość 0, wydrukowaniu. Tak szybko, jak jeden z warunków jest spełniony, zakończenie oceny.

## <a name="see-also"></a>Zobacz także

- [Operator logiczny AND: &&](../cpp/logical-and-operator-amp-amp.md)
- [Logiczne OR — Operator:&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)
