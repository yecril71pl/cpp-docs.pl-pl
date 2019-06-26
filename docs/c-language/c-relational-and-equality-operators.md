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

Plik binarny relacyjne i operatory równości porównać ich pierwszego operandu w celu ich drugiego operandu, aby sprawdzić poprawność określonej relacji. Wynik wyrażenia relacyjne to 1, jeśli przetestowane relacji jest wartość PRAWDA, a 0, jeśli ma wartość false. Typ wyniku jest `int`.

**Składnia**

*relational-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie relacyjne* **&lt;** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie relacyjne* **>** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie relacyjne* **&lt; =** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie relacyjne* **>=** *shift-expression*

*wyrażenie równości*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie równości* **==** *wyrażenie relacyjne*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie równości* **! =** *wyrażenie relacyjne*

Operatory relacyjne i porównania testów się następująco:

|Operator|Relacja przetestowane|
|--------------|-------------------------|
|**&lt;**|Pierwszy operand mniejszy od drugiego operandu|
|**>**|Pierwszy argument operacji, które są większe od drugiego operandu|
|**&lt;=**|Pierwszy operand mniejsze niż lub równe do drugiego operandu|
|**>=**|Pierwszy operand większa lub równa wartości drugiego operandu|
|**==**|Pierwszy operand równą wartości drugiego operandu|
|**\!=**|Pierwszy argument operacji nie jest równa drugiego operandu|

Pierwsze cztery operatory w powyższej listy mają wyższy priorytet niż operatory równości (`==` i `!=`). Zapoznaj się z informacjami pierwszeństwo w tabeli [pierwszeństwo i kojarzenie operatorów C](../c-language/precedence-and-order-of-evaluation.md).

Argumenty operacji może mieć typu całkowitego, zmiennoprzecinkowego lub wskaźnika. Typy argumentów mogą być różne. Operatory relacyjne przeprowadzania zwykle konwersje arytmetyczne operandów typów całkowitych i zmiennoprzecinkowych. Ponadto można użyć następujących kombinacji argumentami o typach z relacyjne i operatory porównania:

- Zarówno argumenty operacji wszelkie relacyjnych lub operator równości, może być wskaźniki do tego samego typu. Dla równości (`==`) i nierówności (`!=`) operatorów, wynikiem porównania wskazuje, czy dwa wskaźniki adresów w tym samym miejscu pamięci. Aby uzyskać inne operatory relacyjne ( **\<** , **>** , **\<** =, i **>** =), wynik porównania wskazuje względne położenie adresów pamięci dwóch obiektów wskazywanych. Operatory relacyjne porównać tylko przesunięcia.

   Porównanie wskaźników jest zdefiniowana tylko dla części tego samego obiektu. Jeśli wskaźników odnoszą się do elementów członkowskich w tablicy, wynik porównania jest odpowiednikiem porównania odpowiednich indeksów dolnych. Adres pierwszego elementu tablicy "poniżej" adres po ostatnim elemencie. W przypadku struktur wskaźniki do elementów członkowskich struktury zadeklarowane w dalszej części są "większe niż" wskaźników do elementów członkowskich zadeklarowanych wcześniej w strukturze. Wskaźniki do elementów członkowskich Unii w tym samym są równe.

- Wartość wskaźnika można porównać do wyrażenia wartości stałej 0 dla równości (`==`) i nierówności (`!=`). Wskaźnik o wartości 0 jest nazywany "null" wskaźnika; oznacza to nie wskazuje lokalizacji w pamięci prawidłowe.

- Operatory porównania, wykonaj te same reguły jako operatory relacyjne, ale zezwala na dodatkowe możliwości: wskaźnik można porównać do stałego wyrażenia typu całkowitego, z wartością 0 lub wskaźnik do `void`. Jeśli dwa wskaźniki są oba wskaźniki o wartości null, porównaj jako równe. Operatory porównania Porównaj segmentu i przesunięcia.

## <a name="examples"></a>Przykłady

Poniższe przykłady ilustrują relacyjne i operatory równości.

```C
int x = 0, y = 0;
if ( x < y )
```

Ponieważ `x` i `y` są równe, wyrażenie w tym przykładzie daje wartość 0.

```C
char array[10];
char *p;

for ( p = array; p < &array[10]; p++ )
    *p = '\0';
```

Fragment, w tym przykładzie ustawia każdego elementu `array` ze stałą znaku null.

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

Te instrukcje deklarują zmienną wyliczenie o nazwie `col` ze znacznikiem `color`. W dowolnym momencie zmienna może zawierać wartość 0, 1 lub 2, który reprezentuje jeden z elementów zestawu wyliczenie `color`: kolor czerwony, biały lub zielonego, odpowiednio. Jeśli `col` zawiera 0 po **Jeśli** instrukcja jest wykonywana, dowolnej instrukcji w zależności od **Jeśli** zostaną wykonane.

## <a name="see-also"></a>Zobacz także

[Operatory relacyjne: \<, >, \<= i > =](../cpp/relational-operators-equal-and-equal.md)<br/>
[Operatory porównania: == i !=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)
