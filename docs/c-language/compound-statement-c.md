---
title: Instrukcja złożona (C)
ms.date: 11/04/2016
helpviewer_keywords:
- compound statements
- statements, compound
ms.assetid: 32d1bf86-cbbc-42a9-ba3a-1be1c6c7754c
ms.openlocfilehash: 42d4c1d21c3e98dfc0281a47a35e033852f8de18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312573"
---
# <a name="compound-statement-c"></a>Instrukcja złożona (C)

Instrukcja złożona (nazywana również "blokiem") jest zwykle wyświetlana jako treść innej instrukcji, takiej jak instrukcja **if** . [Deklaracje i typy](../c-language/declarations-and-types.md) opisują formę i znaczenie deklaracji, które mogą być wyświetlane w nagłówku złożonej instrukcji.

## <a name="syntax"></a>Składnia

*instrukcja złożona*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *deklaracji*<sub>opt</sub> *instrukcji SELECT-list*<sub>opt</sub> **}**

*Deklaracja-lista*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*oświadczeń*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Deklaracja *listy deklaracji* *declaration*

*Lista instrukcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Merge*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcja-list —* *instrukcja*

Jeśli istnieją deklaracje, muszą one znajdować się przed wszelkimi instrukcjami. Zakres każdego identyfikatora zadeklarowanego na początku złożonej instrukcji rozciąga się od punktu deklaracji do końca bloku. Jest on widoczny w bloku, chyba że deklaracja tego samego identyfikatora istnieje w bloku wewnętrznym.

Identyfikatory w instrukcji złożonej są przypuszczalnie **stosowane** , chyba że jawnie zadeklarowano inaczej **static**przy użyciu funkcji `extern` **register**, static lub, Except `extern`. Można opuścić `extern` specyfikator w deklaracjach funkcji, a funkcja nadal będzie `extern`.

Magazyn nie jest przydzielony i Inicjalizacja jest niedozwolona, jeśli zmienna lub funkcja jest zadeklarowana w instrukcji złożonej z `extern`klasą magazynu. Deklaracja odnosi się do zmiennej zewnętrznej lub funkcji zdefiniowanej w innym miejscu.

Zmienne zadeklarowane w bloku ze słowem kluczowym **autolub** **register** są ponownie przydzieloną i, w razie potrzeby, inicjowane przy każdym wprowadzeniu złożonej instrukcji. Te zmienne nie są zdefiniowane po zakończeniu złożonej instrukcji. Jeśli zmienna zadeklarowana wewnątrz bloku ma atrybut **static** , zmienna jest inicjowana po rozpoczęciu wykonywania programu i utrzymuje jego wartość w całym programie. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) , aby uzyskać informacje o **statycznym**.

Ten przykład ilustruje złożone instrukcje:

```
if ( i > 0 )
{
    line[i] = x;
    x++;
    i--;
}
```

W tym przykładzie, jeśli `i` jest większa niż 0, wszystkie instrukcje wewnątrz instrukcji złożonej są wykonywane w kolejności.

## <a name="see-also"></a>Zobacz też

[Instrukcje](../c-language/statements-c.md)
