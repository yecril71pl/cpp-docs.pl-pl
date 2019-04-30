---
title: Inkrementacja i dekrementacja wskaźników
ms.date: 11/04/2016
helpviewer_keywords:
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
ms.openlocfilehash: cdaee3d13a8ceab47f62100953a0eb6e51bfc255
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410658"
---
# <a name="incrementing-and-decrementing-pointers"></a>Inkrementacja i dekrementacja wskaźników

Użyj następujących wskazówek:

- Wskaż bajty wiodące, nie końcu bajtów. Nie jest zwykle bezpieczne wskaźnika na bajt. Jest to zwykle bezpieczniejsze skanować ciąg do przodu, a nie w odwrotnej kolejności.

- Istnieją wskaźnika inkrementacyjnego/dekrementacyjnego funkcje i makra dostępne, które przenieść cały znaków:

    ```cpp
    sz1++;
    ```

   staje się:

    ```cpp
    sz1 = _mbsinc( sz1 );
    ```

   `_mbsinc` i `_mbsdec` funkcje poprawnie zwiększyć i zmniejszyć w `character` jednostki, niezależnie od rozmiaru znaków.

- Dekrementuje należy wskaźnik porównanie ciągu, tak jak poniżej:

    ```cpp
    sz2--;
    ```

   staje się:

    ```cpp
    sz2 = _mbsdec( sz2Head, sz2 );
    ```

   Alternatywnie wskaźnik głównego może być nieprawidłowy znak w ciągu, tak, aby:

    ```cpp
    sz2Head < sz2
    ```

   Konieczne jest posiadanie wskaźnik do znanego, nieprawidłowy bajt.

- Możesz chcieć zachować wskaźnik do poprzedniego znaku na szybsze wywołań `_mbsdec`.

## <a name="see-also"></a>Zobacz także

[Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)<br/>
[Indeksy bajtowe](../text/byte-indices.md)
