---
title: Komentarze (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
ms.openlocfilehash: a90d9d37e69cb2e8be4ab18f77026fdce1221307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506109"
---
# <a name="comments-c"></a>Komentarze (C++)

Komentarz to tekst, który Kompilator ignoruje, ale jest to przydatne dla programistów. Komentarze są zwykle używane do Dodawanie adnotacji do kodu do użytku w przyszłości. Kompilator traktuje je jako biały znak. Komentarze w zakresie testowania można użyć do dezaktywowania pewnych linii kodu; jednak `#if` / `#endif` dyrektywy preprocesora usprawnieniu to ponieważ można otoczyć kod, który zawiera komentarze, ale nie można zagnieździć komentarzy.

Komentarz C++ są zapisywane w jednym z następujących sposobów:

- `/*` (Ukośnika, gwiazdka) znaki, po których dowolnej sekwencji znaków (łącznie z nowych wierszy), a następnie `*/` znaków. Ta składnia jest taka sama jak ANSI C.

- `//` Znaków (dwa ukośniki), a następnie przez dowolną sekwencję znaków. Ta forma komentarz kończy się znakiem nowego wiersza nie od razu poprzedzone znakiem ukośnika odwrotnego. W związku z tym często jest nazywane "komentarz jednowierszowy".

Znaki komentarza (`/*`, `*/`, i `//`) mają nie specjalne znaczenie w w obrębie stałej znaku literał ciągu lub Dodaj komentarz. Komentarze przy użyciu składni pierwszy, dlatego nie mogą być zagnieżdżone.

## <a name="see-also"></a>Zobacz także

[Konwencje leksykalne](../cpp/lexical-conventions.md)