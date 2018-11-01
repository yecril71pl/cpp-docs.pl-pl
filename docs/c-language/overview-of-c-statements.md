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
ms.openlocfilehash: 906beb7c5c2edfc448daadb1f4c5a111f7877b91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613723"
---
# <a name="overview-of-c-statements"></a>Przegląd instrukcji C

Instrukcji C składają się z tokenów, wyrażenia i inne instrukcje. Instrukcja, który wchodzi w skład składnikiem innej instrukcji jest nazywany "treść" otaczającej instrukcji. W tej sekcji omówiono każdy typ instrukcji podanych w następującej składni.

## <a name="syntax"></a>Składnia

*Instrukcja*: [etykietą instrukcji](../c-language/goto-and-labeled-statements-c.md)

[Compound-statement](../c-language/compound-statement-c.md)

[Instrukcja wyrażeń](../c-language/expression-statement-c.md)

[Wybór — instrukcja](../c-language/if-statement-c.md)

[instrukcji iteracji](../c-language/do-while-statement-c.md)

[Instrukcja skoku](../c-language/break-statement-c.md)

[Spróbuj except — instrukcja](../c-language/try-except-statement-c.md)

/ * Microsoft Specific \* / [try finally instrukcji](../c-language/try-finally-statement-c.md)  / \* Specific firmy Microsoft \*/

Często treść instrukcji jest "instrukcję złożonego". Instrukcja złożona składa się z innych instrukcji, które może zawierać słowa kluczowe. Instrukcja złożona sterujący jest ujęty w nawiasy klamrowe (**{}**). Inne instrukcje C zakończona średnikiem (**;**). Średnik jest terminator instrukcji.

Instrukcja wyrażeń zawiera wyrażenie C, który może zawierać operacji arytmetycznych lub operatorów logicznych wprowadzona w [wyrażenia i przydziały](../c-language/expressions-and-assignments.md). Instrukcja o wartości null jest pustą instrukcję.

Każda instrukcja języka C można rozpocząć etykietą identyfikujące składający się z nazwy i dwukropka. Ponieważ tylko `goto` instrukcji rozpoznaje etykiety instrukcji, etykiet instrukcji zostały omówione z `goto`. Zobacz [goto i Labeled — instrukcje](../c-language/goto-and-labeled-statements-c.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Instrukcje](../c-language/statements-c.md)