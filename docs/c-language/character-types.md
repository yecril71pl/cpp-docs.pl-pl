---
title: Typy znaku
ms.date: 11/04/2016
helpviewer_keywords:
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
ms.openlocfilehash: f894114d4e980b11edf55c4d4b7c4e60af396fb1
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151588"
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

## <a name="see-also"></a>Zobacz także

[Stałe znakowe języka C](../c-language/c-character-constants.md)
