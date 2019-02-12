---
title: Punkty sekwencji języka C
ms.date: 11/04/2016
helpviewer_keywords:
- sequence points
ms.assetid: c84885a5-4336-4eba-a643-058df4249903
ms.openlocfilehash: 13d6044269f60dc426a8b0b9b03463f387dfaa10
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152641"
---
# <a name="c-sequence-points"></a>Punkty sekwencji języka C

Między kolejnymi "punktami sekwencji" wartość obiektu może być modyfikowane tylko raz przez wyrażenie. Język C definiuje następujących punktów sekwencji:

- Lewy operand logicznego — i operatora (**&&**). Lewy operand logicznego — i operator jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi ukończenie przed kontynuowaniem. Jeśli lewy operand ma wartość false (0), to drugi operand nie jest oceniany.

- Lewy operand operatora logicznego OR (`||`). Lewy operand operatora logicznego OR jest obliczany całkowicie, wraz ze wszystkimi efektami ubocznymi ukończenie przed kontynuowaniem. Jeśli lewy operand ma wartość true (niezerową), to drugi operand nie jest oceniany.

- Lewy operand operatora przecinka. Lewy operand operatora "przecinek" jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi ukończenie przed kontynuowaniem. Oba operandy operatora przecinka są obliczane zawsze. Należy pamiętać, że operatora przecinka w wywołaniu funkcji nie gwarantuje kolejności oceny.

- Operator wywołania funkcji. Wszystkie argumenty funkcji są oceniane i ze wszystkimi efektami ubocznymi wykonaj przed wejściem do funkcji. Określono nie kolejności obliczania między argumentami.

- Pierwszy operand operatora warunkowego. Pierwszy operand operatora warunkowego jest obliczany całkowicie, a przed kontynuowaniem wykonaj ze wszystkimi efektami ubocznymi.

- Koniec pełnej inicjalizacji wyrażenia (to znaczy, wyrażenie, które nie jest częścią innego wyrażenia, taki jak koniec inicjalizacji w instrukcji deklaracji).

- Wyrażenie w instrukcji wyrażenia. Instrukcje wyrażeń składają się z opcjonalnego wyrażenia następuje średnik (**;**). Wyrażenie jest obliczane efektami ubocznymi i znajduje się punkt sekwencji zgodnie z tego okresu ewaluacji.

- Wyrażenie kontrolujące w wyborze (**Jeśli** lub `switch`) instrukcji. Wyrażenie jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi ukończyć przed wykonaniem kodu zależnego od wyboru.

- Wyrażenie kontrolujące `while` lub **czy** instrukcji. Wyrażenie jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi ukończyć przed wszystkimi instrukcjami w następnej iteracji `while` lub **czy** pętli są wykonywane.

- Każdy z trzech wyrażeń **dla** instrukcji. Wyrażenie jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi ukończyć przed wszystkimi instrukcjami w następnej iteracji **dla** pętli są wykonywane.

- Wyrażenie w `return` instrukcji. Wyrażenie jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi ukończenie sterowanie powraca do wywoływania funkcji.

## <a name="see-also"></a>Zobacz także

[Obliczanie wyrażeń](../c-language/expression-evaluation-c.md)
