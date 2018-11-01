---
title: Typy znaku
ms.date: 11/04/2016
helpviewer_keywords:
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
ms.openlocfilehash: 7ca87ec1cb11f8a00beb6f5eb670b3e292bb1f70
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619339"
---
# <a name="character-types"></a>Typy znaku

Stała liczba całkowita znak nie jest poprzedzony przez literę **L** ma typ `int`. Wartość całkowitą wartością stałą znaku zawierający pojedynczy znak jest wartością liczbową znaków interpretowana jako liczba całkowita. Na przykład, wartość liczbową znaków `a` jest 97 w zapisie dziesiętnym i 61 to sekundy w formacie szesnastkowym.

Syntaktycznie, "szerokich znaków stała" jest stałą znak poprzedzony literę **L**. Stała dwubajtowego znaku ma typ `wchar_t`, zdefiniowane w STDDEF typ liczby całkowitej. Plik nagłówkowy H. Na przykład:

```
char    schar =  'x';   /* A character constant          */
wchar_t wchar = L'x';   /* A wide-character constant for
                            the same character           */
```

Stałe znaki dwubajtowe są 16 bitów szeroki i określić elementy członkowski rozszerzonego wykonania zestawu znaków. Umożliwiają one express znaków alfabetów, które są zbyt duże, aby mogły być reprezentowane przez typ `char`. Zobacz [wielobajtowe i dwubajtowe znaki](../c-language/multibyte-and-wide-characters.md) Aby uzyskać więcej informacji na temat znaków dwubajtowych.

## <a name="see-also"></a>Zobacz też

[Stałe znakowe języka C](../c-language/c-character-constants.md)