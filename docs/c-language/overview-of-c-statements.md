---
title: Przegląd instrukcji C
ms.date: 11/04/2016
helpviewer_keywords:
- semicolon, in C statements
- statements, C
- semicolon
- statements, about statements
- Visual C, statements
ms.assetid: 0d49837a-5399-4881-b60c-af5f4e9720de
ms.openlocfilehash: 1b5863a021fd74bb80162d589af7c2a1a5b36f9b
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147051"
---
# <a name="overview-of-c-statements"></a>Przegląd instrukcji C

Instrukcji C składają się z tokenów, wyrażenia i inne instrukcje. Instrukcja, który wchodzi w skład składnikiem innej instrukcji jest nazywany "treść" otaczającej instrukcji. W tej sekcji omówiono każdy typ instrukcji podanych w następującej składni.

## <a name="syntax"></a>Składnia

*Instrukcja*: [etykietą instrukcji](../c-language/goto-and-labeled-statements-c.md)

[compound-statement](../c-language/compound-statement-c.md)

[expression-statement](../c-language/expression-statement-c.md)

[selection-statement](../c-language/if-statement-c.md)

[iteration-statement](../c-language/do-while-statement-c.md)

[Instrukcja skoku](../c-language/break-statement-c.md)

[try-except-statement](../c-language/try-except-statement-c.md)

/ * Microsoft Specific \* / [try finally instrukcji](../c-language/try-finally-statement-c.md)  / \* Specific firmy Microsoft \*/

Często treść instrukcji jest "instrukcję złożonego". Instrukcja złożona składa się z innych instrukcji, które może zawierać słowa kluczowe. Instrukcja złożona sterujący jest ujęty w nawiasy klamrowe (**{}**). Inne instrukcje C zakończona średnikiem (**;**). Średnik jest terminator instrukcji.

Instrukcja wyrażeń zawiera wyrażenie C, który może zawierać operacji arytmetycznych lub operatorów logicznych wprowadzona w [wyrażenia i przydziały](../c-language/expressions-and-assignments.md). Instrukcja o wartości null jest pustą instrukcję.

Każda instrukcja języka C można rozpocząć etykietą identyfikujące składający się z nazwy i dwukropka. Ponieważ tylko `goto` instrukcji rozpoznaje etykiety instrukcji, etykiet instrukcji zostały omówione z `goto`. Zobacz [goto i Labeled — instrukcje](../c-language/goto-and-labeled-statements-c.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

[Instrukcje](../c-language/statements-c.md)
