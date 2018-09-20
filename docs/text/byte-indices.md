---
title: Indeksy bajtowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11f7f78e87ddd40fd3cf85fc294e8fadac5dbe45
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423796"
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