---
title: Typy znaku
ms.date: 11/04/2016
helpviewer_keywords:
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
ms.openlocfilehash: f894114d4e980b11edf55c4d4b7c4e60af396fb1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312638"
---
# <a name="character-types"></a>Typy znaku

Stała znaku liczby całkowitej, która nie jest poprzedzona **L** literą L `int`, ma typ. Wartość stałej znakowej liczby całkowitej zawierającej pojedynczy znak jest wartością numeryczną znaku interpretowanego jako liczba całkowita. Na przykład wartość liczbowa znaku `a` jest 97 w postaci dziesiętnej i 61 w formacie szesnastkowym.

Syntaktycznie "stała znakowa" to stała znakowa poprzedzona literą **L**. Stała znaku dwubajtowego ma typ `wchar_t`, a liczba całkowita zdefiniowana w STDDEF. H plik nagłówkowy. Przykład:

```
char    schar =  'x';   /* A character constant          */
wchar_t wchar = L'x';   /* A wide-character constant for
                            the same character           */
```

Stałe o szerokim znaku są 16-bitowym i określają elementy członkowskie zestawu znaków wykonywania rozszerzonego. Umożliwiają one wyrażanie znaków w alfabecie, które są zbyt duże, aby były reprezentowane przez typ `char`. Zobacz [znaki wielobajtowe i szerokie,](../c-language/multibyte-and-wide-characters.md) Aby uzyskać więcej informacji o szerokich znakach.

## <a name="see-also"></a>Zobacz też

[Stałe znakowe języka C](../c-language/c-character-constants.md)
