---
title: Inkrementacja i dekrementacja wskaźników | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e220c138ebcbb9010aef78931b07c2b04b095ea7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447667"
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

## <a name="see-also"></a>Zobacz też

[Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)<br/>
[Indeksy bajtowe](../text/byte-indices.md)