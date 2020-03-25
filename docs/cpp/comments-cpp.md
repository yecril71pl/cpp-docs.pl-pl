---
title: Komentarze (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
ms.openlocfilehash: 3326ad7d0b5118182a5d582061fd0c103986f232
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189757"
---
# <a name="comments-c"></a>Komentarze (C++)

Komentarz jest tekstem, który kompilator ignoruje, ale jest przydatny dla programistów. Komentarze są zwykle używane do dodawania adnotacji do kodu w przyszłości. Kompilator traktuje je jako biały znak. Możesz użyć komentarzy w testowaniu, aby niektóre wiersze kodu były nieaktywne; Jednakże dyrektywy preprocesora `#if`/`#endif` działały lepiej, ponieważ możesz otoczyć kod zawierający komentarze, ale nie możesz zagnieżdżać komentarzy.

C++ Komentarz jest zapisywana w jeden z następujących sposobów:

- `/*` (ukośnik, gwiazdka), po którym następuje jakakolwiek sekwencja znaków (w tym nowe wiersze), po której następuje `*/` znaków. Ta składnia jest taka sama jak ANSI C.

- `//` (dwa ukośniki), po którym następuje jakakolwiek sekwencja znaków. Nowy wiersz bezpośrednio poprzedzony ukośnikiem odwrotnym kończy tę formę komentarza. W związku z tym często nazywa się "jednowierszowym komentarzem".

Znaki komentarza (`/*`, `*/`i `//`) nie mają specjalnego znaczenia w obrębie znaku stałej, literału ciągu ani komentarza. Komentarze z użyciem pierwszej składni nie mogą być zagnieżdżane.

## <a name="see-also"></a>Zobacz też

[Konwencje leksykalne](../cpp/lexical-conventions.md)
