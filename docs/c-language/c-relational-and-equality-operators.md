---
title: Operatory relacyjne i porównania języka C
ms.date: 10/18/2018
helpviewer_keywords:
- relational operators, syntax
- equality operator
- operators [C], equality
- equality operator, syntax
- operators [C], relational
ms.assetid: c89a3815-a65e-4e0d-8333-0e8dc7fdb30b
ms.openlocfilehash: 25e9bb65492e0c4b100ecd7a800491d238b1dd38
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400529"
---
# <a name="c-relational-and-equality-operators"></a>Operatory relacyjne i porównania języka C

Operatory Binary relacyjne i równości porównują swój pierwszy operand z drugim operandem, aby przetestować prawidłowość określonej relacji. Wynik wyrażenia relacyjnego to 1, jeśli przetestowana relacja ma wartość true i 0, jeśli ma wartość false. Typ wyniku to `int`.

**Obowiązuje**

*wyrażenie relacyjne*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie przesunięcia*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**&lt;** wyrażenie *przesunięcia* w postaci *relacyjnej*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**>** wyrażenie *przesunięcia* w postaci *relacyjnej*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;wyrażenie *przesunięcia* w postaci *relacyjnej* ** &lt; **<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**>=** wyrażenie *przesunięcia* w postaci *relacyjnej*

*wyrażenie równości*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie relacyjne*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;wyrażenie *równości wyrażenia* **==** *relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie równości* **! =** *wyrażenie relacyjne*

Operatory relacyjne i porównania testują następujące relacje:

|Operator|Przetestowano relację|
|--------------|-------------------------|
|**&lt;**|Pierwszy operand krótszy niż drugi operand|
|**>**|Pierwszy operand jest większy niż drugi operand|
|**&lt;=**|Pierwszy operand jest mniejszy niż lub równy drugiemu operandowi|
|**>=**|Pierwszy operand jest większy lub równy drugiemu operandowi|
|**==**|Pierwszy operand równy drugiemu operandowi|
|**!=**|Pierwszy operand nie jest równy drugiemu operandowi|

Pierwsze cztery operatory z powyższej listy mają wyższy priorytet niż operatory równości (`==` i `!=`). Zobacz informacje o pierwszeństwie w [pierwszeństwie tabeli i łączność operatory języka C](../c-language/precedence-and-order-of-evaluation.md).

Operandy mogą mieć typ całkowity, zmiennoprzecinkowy lub wskaźnik. Typy operandów mogą być różne. Operatory relacyjne wykonują typowe konwersje arytmetyczne dla operacji typu całkowitego i zmiennoprzecinkowego. Ponadto można użyć następujących kombinacji typów operandów z operatorami relacyjnymi i równości:

- Oba operandy operatora relacyjnego lub równości mogą być wskaźnikami do tego samego typu. Dla operatorów równości (`==`) i nierówności (`!=`) wynik porównania wskazuje, czy dwa wskaźniki dotyczą tej samej lokalizacji pamięci. W przypadku innych operatorów relacyjnych**\<**( **>**, **\<**, = i **>**=) wynik porównania wskazuje względne położenie dwóch adresów pamięci obiektów wskazywanych przez. Operatory relacyjne porównują tylko przesunięcia.

   Porównanie wskaźników jest zdefiniowane tylko dla części tego samego obiektu. Jeśli wskaźniki odwołują się do elementów członkowskich tablicy, porównanie jest równoważne porównaniu z odpowiednimi indeksami dolnymi. Adres pierwszego elementu tablicy jest mniejszy niż adres ostatniego elementu. W przypadku struktur wskaźniki do składowych struktury zadeklarowanych później są wskaźnikami "większe niż" do członków zadeklarowanych wcześniej w strukturze. Wskaźniki do elementów członkowskich tego samego związku są równe.

- Wartość wskaźnika można porównać do stałej wartości 0 dla równości (`==`) lub nierówności (`!=`). Wskaźnik o wartości 0 jest nazywany wskaźnikiem "null"; oznacza to, że nie wskazuje prawidłowej lokalizacji w pamięci.

- Operatory równości stosują te same reguły, co operatory relacyjne, ale zezwalają na dodatkowe możliwości: wskaźnik można porównać do stałego wyrażenia całkowitego z wartością 0 lub do wskaźnika `void`. Jeśli dwa wskaźniki są wskaźnikami o wartości null, są one porównywane jako równe. Operatory równości porównują segment i przesunięcia.

## <a name="examples"></a>Przykłady

W poniższych przykładach przedstawiono operatory relacyjne i porównania.

```C
int x = 0, y = 0;
if ( x < y )
```

Ponieważ `x` i `y` są równe, wyrażenie w tym przykładzie zwraca wartość 0.

```C
char array[10];
char *p;

for ( p = array; p < &array[10]; p++ )
    *p = '\0';
```

Fragment w tym przykładzie ustawia każdy element `array` do stałej znakowej o wartości null.

```C
enum color { red, white, green } col;
   .
   .
   .
   if ( col == red )
   .
   .
   .
```

Te instrukcje deklarują zmienną wyliczenia o `col` nazwie za pomocą `color`tagu. W dowolnym momencie zmienna może zawierać wartość całkowitą 0, 1 lub 2, która reprezentuje jeden z elementów zestawu `color`wyliczenia: kolor czerwony, biały lub zielony odpowiednio. Jeśli `col` zawiera wartość 0, gdy zostanie wykonana instrukcja **if** , wszystkie instrukcje w zależności od **if** zostaną wykonane.

## <a name="see-also"></a>Zobacz też

[Operatory relacyjne \<:, > \<, = i >=](../cpp/relational-operators-equal-and-equal.md)<br/>
[Operatory równości: = = i! =](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)
