---
title: Indeksy bajtowe
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
ms.openlocfilehash: 4e19868e5297e1c1615efabde2aee418bc53c51e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448818"
---
# <a name="byte-indices"></a>Indeksy bajtowe

Użyj następujących wskazówek:

- Praca z indeksem bytewise na ciąg stanowi problem podobne do tych powodowanego przez wskaźnik manipulacji. Rozważmy następujący przykład, które skanuje ciąg znak ukośnika odwrotnego:

    ```cpp
    while ( rgch[ i ] != '\\' )
        i++;
    ```

   To może indeksować bajt, nie bajtem wiodącym, i dlatego nie może wskazywać na `character`.

- Użyj [_mbclen —](../c-runtime-library/reference/mbclen-mblen-mblen-l.md) funkcję, aby rozwiązać problem poprzedniego:

    ```cpp
    while ( rgch[ i ] != '\\' )
        i += _mbclen ( rgch + i );
    ```

   To prawidłowo indeksuje do bajtem wiodącym, dlatego aby `character`. `_mbclen` Funkcja określa rozmiar znaków (1 lub 2 bajtów).

## <a name="see-also"></a>Zobacz też

[Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)<br/>
[Ostatni znak w ciągu](../text/last-character-in-a-string.md)