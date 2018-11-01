---
title: Hierarchia i kolejność ocen
ms.date: 11/04/2016
helpviewer_keywords:
- associativity of operators [C++]
- precedence [C++], operators
- data binding [C++], operator precedence
- operators [C++], precedence
ms.assetid: 201f7864-0c51-4c55-9d6f-39c5d013bcb0
ms.openlocfilehash: 1b14f7a7d0c1d682c641ab441dc3e40c23688392
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463261"
---
# <a name="precedence-and-order-of-evaluation"></a>Hierarchia i kolejność ocen

Pierwszeństwo i kojarzenie operatorów C wpływa na grupowanie i oceny operandu w wyrażeniach. Kolejność ma znaczenie, tylko wtedy, gdy istnieją inne operatory o priorytecie wyższą lub niższą. Wyrażenia z operatorami o wyższym priorytecie są obliczane jako pierwsze. Pierwszeństwo można również opisać za pomocą słowa "wiązanie." Operatory o wyższym priorytecie mówi się, że ma większego powiązania.

W poniższej tabeli przedstawiono pierwszeństwo i kojarzenie (kolejność, w której argumenty operacji są obliczane) operatorów języka C, lista je według pierwszeństwa od najwyższego do najniższego. W przypadku, gdy pojawią się ze sobą kilka operatorów, mają równe pierwszeństwo i są obliczane zgodnie z ich łączność. Operatory w tabeli są opisane w sekcjach, począwszy od [przyrostkowe operatory](../c-language/postfix-operators.md). Pozostała część tej sekcji zawiera ogólne informacje o pierwszeństwo i łączność.

## <a name="precedence-and-associativity-of-c-operators"></a>Pierwszeństwo i kojarzenie operatorów języka C

|Symbol <sup>1</sup>|Typ operacji|Łączność|
|-------------|-----------------------|-------------------|
|**\[ ] ( ) . ->**<br /><br />**++** **--** (przyrostkowe)|Wyrażenie|Od lewej do prawej|
**Operator sizeof & \* + - ~!**<br /><br />**++ —** (prefiks)|Jednoargumentowy|Od prawej do lewej|
|*rzutowaniach typu*|Jednoargumentowy|Od prawej do lewej|
|**\* / %**|Mnożenia|Od lewej do prawej|
|**+ -**|Dodatku|Od lewej do prawej|
|**\<\< >>**|Operatory przesunięcia bitowego|Od lewej do prawej|
|**\< > \<= >=**|Relacyjne|Od lewej do prawej|
|**== !=**|Równość|Od lewej do prawej|
|**&**|Bitwise-AND|Od lewej do prawej|
|**^**|Bitwise-exclusive-OR|Od lewej do prawej|
|**&#124;**|Bitwise-inclusive-OR|Od lewej do prawej|
|**&&**|Logiczny — i|Od lewej do prawej|
|**&#124;&#124;**|Logiczne OR|Od lewej do prawej|
|**? :**|Wyrażenia warunkowego|Od prawej do lewej|
|**= \*= /= %=**<br /><br /> **+= -= \<\<= >>= &=**<br /><br /> **^= &#124;=**|Przypisanie proste i złożone <sup>2</sup>|Od prawej do lewej|
|**,**|Kolejne oceny|Od lewej do prawej|

1. Operatory są wymienione w kolejności malejącej. Jeśli wiele operatorów są wyświetlane w tym samym wierszu lub w grupie, mają równy priorytet.

1. Wszystkie operatory proste i złożone przypisania mają równy priorytet.

Wyrażenie może zawierać kilka operatorów o równy priorytet. Gdy tych operatorów pojawią się na tym samym poziomie w wyrażeniu, ocena będzie kontynuowane zgodnie z łączność operatora od prawej do lewej lub od lewej do prawej. Kierunek oceny nie ma wpływu na wyniki wyrażeń, które zawierają więcej niż jeden mnożenia (<strong>\*</strong>), dodanie (**+**), lub dane binarne bitowe (**&**, **&#124;**, lub **^**) — operator na tym samym poziomie. Kolejność operacji nie jest zdefiniowany przez język. Kompilator jest bezpłatny do oceny takiego wyrażenia w dowolnej kolejności, kompilator może zagwarantować spójne wyniki.

Tylko obliczania sekwencyjnego (**,**), to logiczny — i (**&&**), logiczne OR (**||**), wyrażenia warunkowego (**?:** ), i operatory wywołania funkcji stanowią punktów sekwencji i w związku z tym gwarantuje określonej kolejności obliczania dla ich operandami. Operator wywołania funkcji to zestaw nawiasów po identyfikator funkcji. Operator obliczania sekwencyjnego (**,**) jest gwarantowane do oceny swoich argumentów od lewej do prawej. (Zwróć uwagę, że operatora przecinka w wywołaniu funkcji nie jest taka sama jak operator obliczania sekwencyjnego i nie zapewnia takiego gwarancji). Aby uzyskać więcej informacji, zobacz [punktów sekwencji](../c-language/c-sequence-points.md).

Operatory logiczne gwarantuje również oceny operandy od lewej do prawej. Jednak umożliwiają podawanie wartości najmniejszej liczby operandów potrzebne do określenia wynik wyrażenia. Jest to nazywane "ocena zwarcia". W związku z tym niektóre operandy wyrażenia nie może być oceniany. Na przykład w wyrażeniu

`x && y++`

drugi operand `y++`, jest oceniane tylko wtedy, gdy `x` ma wartość true (niezerową). W efekcie `y` nie jest zwiększana, gdy `x` ma wartość false (0).

## <a name="examples"></a>Przykłady

Na poniższej liście przedstawiono, jak kompilator automatycznie wiąże kilka przykładowych wyrażeń:

|Wyrażenie|Powiązanie automatyczne|
|----------------|-----------------------|
|& b &#124; &#124; c|(& (b). &#124; &#124; c|
|= b &#124; &#124; c|= (b &#124; &#124; c).|
|q & & r &#124; &#124; s--|(q & & r) &#124; &#124; s--|

W pierwszym wyrażeniu operatora testu koniunkcji — i operatora (**&**) mają wyższy priorytet niż operator logiczny OR (**||**), więc `a & b` formularzy pierwszy argument operacji operator logiczny lub operacji.

W drugim wyrażeniu operator logiczny OR (**||**) mają wyższy priorytet niż operator przypisania prostego (**=**), więc `b || c` są grupowane jako prawostronny operand przypisania. Należy zauważyć, że wartość przypisana do `a` jest równa 0 lub 1.

Trzeci wyrażenie pokazuje poprawnie sformułowany wyrażenie, które może powodować nieoczekiwany wynik. Logiczny — i operatora (**&&**) mają wyższy priorytet niż operator logiczny OR (**||**), więc `q && r` są grupowane jako argument. Ponieważ operatorów logicznych gwarantuje oceny argumentów od lewej do prawej, `q && r` jest oceniany przed `s--`. Jednak jeśli `q && r` ma wartość różną od zera, `s--` nie jest oceniany i `s` nie zostanie zmniejszona. Jeśli nie zmniejszanie `s` mogłoby spowodować problem w programie `s--` powinny się wyświetlać jako pierwszy argument operacji wyrażenia, lub `s` powinny być wraz z przydzielaniem osobnych operacji.

Poniższe wyrażenie jest niedozwolone i tworzy komunikat diagnostyczny w czasie kompilacji:

|Niedozwolone wyrażenie|Domyślnie, grupowanie|
|------------------------|----------------------|
|p == 0? p += 1: p += 2|(p == 0? p += 1: p) += 2|

W tym wyrażeniu operator równości (**==**) ma najwyższy priorytet, więc `p == 0` są grupowane jako argument. Operator wyrażenia warunkowego (**?:**) następnej najwyższy priorytet. Pierwszy argument operacji jest `p == 0`, a drugim argumentem `p += 1`. Jednak ostatni argument operacji operatora wyrażenia warunkowego jest uważany za `p` zamiast `p += 2`, ponieważ tego wystąpienia `p` dokładniej wiąże operator wyrażenia warunkowego niż jego operator przypisania złożone. Występuje błąd składni, ponieważ `+= 2` nie ma lewostronny operand. Należy użyć nawiasów, aby zapobiegać błędom tego rodzaju i przedstawić bardziej czytelny kod. Na przykład wystarczą nawiasów pokazany poniżej poprawiać i wyjaśnienia w poprzednim przykładzie:

`( p == 0 ) ? ( p += 1 ) : ( p += 2 )`

## <a name="see-also"></a>Zobacz też

[Operatory języka C](../c-language/c-operators.md)
