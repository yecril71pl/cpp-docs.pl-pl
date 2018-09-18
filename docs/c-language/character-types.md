---
title: Znakowe typy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c62633d8c7532f15d725018d80f045cf3a37838
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081003"
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