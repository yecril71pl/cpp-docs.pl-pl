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
ms.openlocfilehash: 1cd26eea35da463211b144e98faa0636f5204f6f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="character-types"></a>Typy znaku
Stała znakowa całkowitą nie poprzedzony literą **L** ma typ `int`. Wartość stała znakowa liczba całkowita zawierająca pojedynczy znak jest wartością liczbową znaku interpretowane jako liczba całkowita. Na przykład wartość liczbową znaku `a` 97 dziesiętnie i 61 w formacie szesnastkowym.  
  
 Składnia, "szerokich znaków stała" jest stałą znak poprzedzony literą **L**. Szerokich znaków stała ma typ `wchar_t`, integer — typ zdefiniowany w STDDEF. Plik nagłówka H. Na przykład:  
  
```  
char    schar =  'x';   /* A character constant          */  
wchar_t wchar = L'x';   /* A wide-character constant for   
                            the same character           */  
```  
  
 Stałe znaków dwubajtowych 16 bitów szerokości i określić członkami zestaw znaków wykonania rozszerzonej. Umożliwiają one express znaków w małych liter, które są za duże, aby mogły być reprezentowane przez typ `char`. Zobacz [wielobajtowe i dwubajtowe znaki](../c-language/multibyte-and-wide-characters.md) Aby uzyskać więcej informacji na temat znaki dwubajtowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe znakowe języka C](../c-language/c-character-constants.md)