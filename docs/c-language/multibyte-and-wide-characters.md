---
title: Znaki wielobajtowe i dwubajtowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- character data types [C]
- Unicode [C++], wide character set
- types [C], character
- characters [C++], wide
- international applications [C++], character display
- multibyte characters [C++]
- wide characters [C++]
- characters [C++], codes
- character codes [C++], wide
- character codes [C++], multibyte
ms.assetid: 1943c469-200d-4724-b18f-781d70520f9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc259a75ab12352a7d0029241496aea22803152a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384203"
---
# <a name="multibyte-and-wide-characters"></a>Znaki wielobajtowe i dwubajtowe
Znaków wielobajtowych jest składane sekwencji bajtów co najmniej jeden znak. Każdej sekwencji bajtów reprezentuje jeden znak w zestawie znaków rozszerzonych. Znaki wielobajtowe są używane w zestawów znaków, takich jak Kanji.  
  
 Znaki dwubajtowe są kody znaków wielu języków, które są zawsze szeroki 16 bitów. Typ dla stałe znakowe jest `char`; znaki dwubajtowe, jest typu `wchar_t`. Ponieważ znaki dwubajtowe są zawsze o stałym rozmiarze, przy użyciu znaki dwubajtowe upraszcza programowanie z użyciem zestawu znaków międzynarodowych.  
  
 Literał całej znaków ciągu `L"hello"` staje się tablicę sześciu liczb całkowitych typu `wchar_t`.  
  
```  
{L'h', L'e', L'l', L'l', L'o', 0}  
```  
  
 Specyfikacja Unicode jest ze specyfikacją znaki dwubajtowe. Procedury biblioteki wykonawczej dla tłumaczenie między znaki wielobajtowe i dwubajtowe obejmują `mbstowcs`, `mbtowc`, `wcstombs`, i `wctomb`.  
  
## <a name="see-also"></a>Zobacz też  
 [Identyfikatory w języku C](../c-language/c-identifiers.md)