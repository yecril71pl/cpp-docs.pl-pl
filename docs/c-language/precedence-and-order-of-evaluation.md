---
title: Hierarchia i kolejność ocen
ms.date: 07/11/2019
helpviewer_keywords:
- associativity of operators [C++]
- precedence [C++], operators
- data binding [C++], operator precedence
- operators [C++], precedence
ms.assetid: 201f7864-0c51-4c55-9d6f-39c5d013bcb0
ms.openlocfilehash: c1a5feb4552dd43b26263ebd3080e18adef6cb32
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211739"
---
# <a name="precedence-and-order-of-evaluation"></a>Hierarchia i kolejność ocen

Pierwszeństwo i łączność operatorów języka C wpływają na grupowanie i ocenę operandów w wyrażeniach. Pierwszeństwo operatora ma znaczenie tylko wtedy, gdy obecne są inne operatory o wyższym lub niższym priorytecie. Wyrażenia z operatorami o wyższym priorytecie są oceniane jako pierwsze. Pierwszeństwo można także opisać w wyrazie "Binding". Operatory o wyższym priorytecie są określane jako mające ściślejsze powiązanie.

Poniższa tabela podsumowuje pierwszeństwo i łączność (kolejność, w jakiej operandy są oceniane) operatorów języka C, wymieniając je w kolejności pierwszeństwa od najwyższego do najniższego. Gdy kilka operatorów występuje razem, mają one równy priorytet i są oceniane zgodnie z ich łączność. Operatory w tabeli są opisane w sekcjach zaczynających się od [operatorów przyrostkowych](../c-language/postfix-operators.md). Pozostała część tej sekcji zawiera ogólne informacje o pierwszeństwie i łączność.

## <a name="precedence-and-associativity-of-c-operators"></a>Pierwszeństwo i łączność operatorów języka C

| Symbol <sup>1</sup> | Typ operacji | Łączność |
|-------------|-----------------------|-------------------|
| `[` `]` `(` `)` `.` `->`<br/>`++``--`(przyrostkowo) | Wyrażenie | Od lewej do prawej |
| **`sizeof`** `&` `*` `+` `-` `~` `!`<br/>`++``--`(prefiks) | Jednoargumentowy | Od prawej do lewej |
| *typecasts* | Jednoargumentowy | Od prawej do lewej |
| `*` `/` `%` | Mnożenie | Od lewej do prawej |
| `+` `-` | Dodawanie | Od lewej do prawej |
| `<<` `>>` | Przesunięcie bitowe | Od lewej do prawej |
| `<` `>` `<=` `>=` | Relacyjne | Od lewej do prawej |
| `==` `!=` | Równość | Od lewej do prawej |
| `&` | Bitowe i | Od lewej do prawej |
| `^` | Bitowe wykluczające lub | Od lewej do prawej |
| `|` | Bitowe lub | Od lewej do prawej |
| `&&` | Koniunkcja logiczna | Od lewej do prawej |
| `||` | Logiczne-lub | Od lewej do prawej |
| `? :` | Wyrażenie warunkowe | Od prawej do lewej |
| `=` `*=` `/=` `%=`<br/>`+=` `-=` `<<=` `>>=` `&=`<br/>`^=` `|=` | Proste i złożone przypisanie <sup>2</sup> | Od prawej do lewej |
| `,` | Ocena sekwencyjna | Od lewej do prawej |

<sup>1</sup> operatory są wymienione w kolejności malejącej według pierwszeństwa. Jeśli w tym samym wierszu lub grupie występuje kilka operatorów, mają one równy priorytet.

<sup>2</sup> wszystkie operatory proste i złożone przypisanie mają równy priorytet.

Wyrażenie może zawierać kilka operatorów o równym priorytecie. Gdy kilka takich operatorów pojawia się na tym samym poziomie w wyrażeniu, szacowanie postępuje zgodnie z łączność operatora, od prawej do lewej lub od lewej do prawej. Kierunek obliczania nie ma wpływu na wyniki wyrażeń, które zawierają więcej niż jeden operator mnożenia ( `*` ), dodawanie ( `+` ) lub binarny bitowy ( `&` , `|` lub `^` ) na tym samym poziomie. Kolejność operacji nie jest zdefiniowana przez język. Kompilator jest bezpłatny do oszacowania takich wyrażeń w dowolnej kolejności, jeśli kompilator może zagwarantować spójny wynik.

Tylko operatory sekwencyjne ( `,` ), logiczne-i (), logiczne- `&&` lub () `||` , warunkowego wyrażenia ( `? :` ) i wywołania funkcji stanowią punkty sekwencji i w związku z tym gwarantują określoną kolejność obliczeń dla argumentów operacji. Operator wywołania funkcji jest zestaw nawiasów po identyfikatorze funkcji. Operator sekwencyjnej oceny ( `,` ) jest gwarantowany do oceny jego operandów od lewej do prawej. (Operator przecinek w wywołaniu funkcji nie jest taki sam jak operator sekwencyjnej oceny i nie zapewnia takiego zagwarantowania). Aby uzyskać więcej informacji, zobacz [punkty sekwencji](c-sequence-points.md).

Operatory logiczne gwarantują również ocenę ich operandów od lewej do prawej. Jednak oceńą najmniejszą liczbę operandów, które trzeba wykonać, aby określić wynik wyrażenia. Jest to tzw. Ocena "krótkiego obwodu". W rezultacie niektóre operandy wyrażenia mogą nie zostać ocenione. Na przykład, w wyrażeniu

`x && y++`

drugi operand `y++` jest oceniany tylko wtedy, gdy `x` ma wartość true (niezerowa). W tym `y` przypadku nie jest zwiększana, jeśli `x` ma wartość false (0).

## <a name="examples"></a>Przykłady

Na poniższej liście przedstawiono sposób, w jaki kompilator automatycznie wiąże kilka przykładowych wyrażeń:

| Wyrażenie | Automatyczne powiązanie |
|----------------|-----------------------|
| `a & b || c` | `(a & b) || c` |
| `a = b || c` | `a = (b || c)` |
| `q && r || s--` | `(q && r) || s--` |

W pierwszym wyrażeniu operator koniunkcji ( `&` ) ma wyższy priorytet niż operator logiczny or ( `||` ), więc `a & b` tworzy pierwszy operand operacji logicznej or.

W drugim wyrażeniu operator logiczny OR ( `||` ) ma wyższy priorytet niż operator przypisywania prostego ( `=` ), więc `b || c` jest zgrupowany jako argument operacji po prawej stronie w przypisaniu. Należy pamiętać, że wartość przypisana do `a` jest równa 0 lub 1.

Trzecie wyrażenie pokazuje poprawnie sformułowane wyrażenie, które może generować nieoczekiwany wynik. Operator logiczny AND ( `&&` ) ma wyższy priorytet niż operator logiczny or ( `||` ), więc `q && r` jest zgrupowany jako operand. Ponieważ operatory logiczne gwarantują ocenę operandów od lewej do prawej, `q && r` są oceniane przed `s--` . Jednakże, jeśli ma `q && r` wartość różną od zera, `s--` nie jest oceniane i `s` nie jest zmniejszany. Jeśli zmniejszenie nie spowoduje zmniejszenia `s` problemu w programie, `s--` powinien pojawić się jako pierwszy operand wyrażenia lub `s` w oddzielnym operacji.

Następujące wyrażenie jest niedozwolone i generuje komunikat diagnostyczny w czasie kompilacji:

| Niedozwolone wyrażenie | Grupowanie domyślne |
|------------------------|----------------------|
| `p == 0 ? p += 1: p += 2` | `( p == 0 ? p += 1 : p ) += 2` |

W tym wyrażeniu operator równości ( `==` ) ma najwyższy priorytet, więc `p == 0` jest zgrupowany jako operand. Operator wyrażenia warunkowego ( `? :` ) ma następny najwyższy priorytet. Jego pierwszy operand to `p == 0` , a drugi operand to `p += 1` . Jednak ostatni operand operatora wyrażenia warunkowego jest uznawany za `p` zamiast `p += 2` , ponieważ to wystąpienie `p` wiąże się ściśle z operatorem wyrażenia warunkowego niż do operatora przypisania złożonego. Wystąpił błąd składniowy, ponieważ nie `+= 2` ma operandu po lewej stronie. Należy użyć nawiasów, aby zapobiec błędom tego rodzaju i utworzyć bardziej czytelny kod. Można na przykład użyć nawiasów, jak pokazano poniżej, aby poprawić i wyjaśnić poprzedni przykład:

`( p == 0 ) ? ( p += 1 ) : ( p += 2 )`

## <a name="see-also"></a>Zobacz także

[Operatory języka C](c-operators.md)
