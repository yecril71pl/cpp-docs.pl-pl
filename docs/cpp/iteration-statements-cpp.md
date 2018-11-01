---
title: Instrukcje iteracji (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
ms.openlocfilehash: 72f81e2fc58a31db0c4cd3f77ba182bd8b8152a4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644942"
---
# <a name="iteration-statements-c"></a>Instrukcje iteracji (C++)

Instrukcje iteracji spowodować instrukcji (lub instrukcje złożone) do wykonania, zero lub więcej razy, z zastrzeżeniem niektórych kryteriów zakończenia pętli. Jeśli te instrukcje są instrukcje złożone, są one wykonywane w kolejności, chyba że albo [podziału](../cpp/break-statement-cpp.md) instrukcji lub [nadal](../cpp/continue-statement-cpp.md) napotkania instrukcji.

C++ zapewnia cztery instrukcje iteracji — [podczas](../cpp/while-statement-cpp.md), [czy](../cpp/do-while-statement-cpp.md), [dla](../cpp/for-statement-cpp.md), i [for z zakresem](../cpp/range-based-for-statement-cpp.md). Każda z tych iteracje do momentu jego zakończenia wyrażenie ma zero (false), lub zakończenia pętli jest wymuszone za pomocą **podziału** instrukcji. Poniższa tabela zawiera podsumowanie tych instrukcji i działań; każdy jest szczegółowo omówione w kolejnych sekcjach.

### <a name="iteration-statements"></a>Instrukcje iteracji

|Instrukcja|Oceniona|Inicjalizacja|Inkrementacja|
|---------------|------------------|--------------------|---------------|
|**while**|Góry pętli|Nie|Nie|
|**do**|Dołu pętli|Nie|Nie|
|**for**|Góry pętli|Tak|Tak|
|**for z zakresem**|Góry pętli|Tak|Tak|

Część instrukcji w instrukcji iteracji nie może być deklaracji. Jednak może być instrukcji złożonej zawierającej deklaracji.

## <a name="see-also"></a>Zobacz także

[Przegląd instrukcji C++](../cpp/overview-of-cpp-statements.md)