---
title: Typy znaku
ms.date: 11/04/2016
helpviewer_keywords:
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
ms.openlocfilehash: 5b1306c70cdab423c8758bf3e6c9ac4e9d6507da
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226493"
---
# <a name="character-types"></a>Typy znaku

Stała znaku liczby całkowitej, która nie jest poprzedzona literą **L** , ma typ **`int`** . Wartość stałej znakowej liczby całkowitej zawierającej pojedynczy znak jest wartością numeryczną znaku interpretowanego jako liczba całkowita. Na przykład wartość liczbowa znaku `a` jest 97 w postaci dziesiętnej i 61 w formacie szesnastkowym.

Syntaktycznie "stała znakowa" to stała znakowa poprzedzona literą **L**. Stała znaku dwubajtowego ma typ **`wchar_t`** , a liczba całkowita zdefiniowana w STDDEF. H plik nagłówkowy. Na przykład:

```
char    schar =  'x';   /* A character constant          */
wchar_t wchar = L'x';   /* A wide-character constant for
                            the same character           */
```

Stałe o szerokim znaku są 16-bitowym i określają elementy członkowskie zestawu znaków wykonywania rozszerzonego. Umożliwiają one wyrażanie znaków w alfabecie, które są zbyt duże, aby były reprezentowane przez typ **`char`** . Zobacz [znaki wielobajtowe i szerokie,](../c-language/multibyte-and-wide-characters.md) Aby uzyskać więcej informacji o szerokich znakach.

## <a name="see-also"></a>Zobacz także

[Stałe znakowe języka C](../c-language/c-character-constants.md)
