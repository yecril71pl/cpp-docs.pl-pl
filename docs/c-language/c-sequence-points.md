---
title: Punkty sekwencji języka C
ms.date: 11/04/2016
helpviewer_keywords:
- sequence points
ms.assetid: c84885a5-4336-4eba-a643-058df4249903
ms.openlocfilehash: 0147f51063127cb26ce8caf70bc46eadc87b8d3e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226519"
---
# <a name="c-sequence-points"></a>Punkty sekwencji języka C

Między kolejnymi "punktami sekwencji" wartość obiektu może być modyfikowana tylko raz przez wyrażenie. Język C definiuje następujące punkty sekwencji:

- Lewy argument operacji operatora logicznego AND ( **&&** ). Lewy operand operatora logicznego AND jest całkowicie oszacowany i wszystkie efekty uboczne zostały zakończone przed kontynuowaniem. Jeśli argument operacji po lewej stronie zwróci wartość false (0), drugi operand nie jest obliczany.

- Lewy argument operacji operatora logicznego OR ( `||` ). Lewy operand operatora logicznego OR jest w pełni oceniany i wszystkie efekty uboczne zostały zakończone przed kontynuowaniem. Jeśli argument operacji po lewej stronie zwraca wartość true (niezerowa), drugi operand nie jest oceniany.

- Lewy operand operatora przecinka. Lewy operand operatora przecinka jest obliczany całkowicie i wszystkie efekty uboczne zostały zakończone przed kontynuowaniem. Oba operandy operatora przecinka są obliczane zawsze. Należy zauważyć, że operator przecinka w wywołaniu funkcji nie gwarantuje kolejności oceny.

- Operator wywołania funkcji. Wszystkie argumenty funkcji są oceniane i wszystkie efekty uboczne zakończone przed wejściem do funkcji. Nie określono kolejności oceny między argumentami.

- Pierwszy operand operatora warunkowego. Pierwszy operand operatora warunkowego jest w pełni oceniany i wszystkie efekty uboczne zakończone przed kontynuowaniem.

- Koniec pełnego wyrażenia inicjowania (czyli wyrażenie, które nie jest częścią innego wyrażenia, takiego jak koniec inicjalizacji w instrukcji deklaracji).

- Wyrażenie w instrukcji wyrażenia. Instrukcje wyrażenia składają się z opcjonalnego wyrażenia, po którym następuje średnik (**;**). Wyrażenie jest oceniane pod kątem efektów ubocznych i istnieje punkt sekwencji po tej ocenie.

- Wyrażenie kontrolne w instrukcji Selection ( **`if`** lub **`switch`** ). Wyrażenie jest obliczane całkowicie i wszystkie efekty uboczne zakończone przed wykonaniem kodu zależnego od zaznaczenia.

- Wyrażenie kontrolne **`while`** **`do`** instrukcji or. Wyrażenie jest obliczane w całości i wszystkie efekty uboczne zostały zakończone przed wykonaniem jakichkolwiek instrukcji w następnej **`while`** iteracji **`do`** pętli or.

- Każdy z trzech wyrażeń **`for`** instrukcji. Wyrażenia są obliczane w całości i wszystkie efekty uboczne są wykonywane przed wykonaniem jakichkolwiek instrukcji w następnej iteracji **`for`** pętli.

- Wyrażenie w **`return`** instrukcji. Wyrażenie jest obliczane w całości i wszystkie efekty uboczne zakończone przed powracaniem do funkcji wywołującej.

## <a name="see-also"></a>Zobacz także

[Obliczanie wyrażeń](../c-language/expression-evaluation-c.md)
