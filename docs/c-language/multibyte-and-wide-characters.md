---
title: Znaki wielobajtowe i dwubajtowe
ms.date: 11/04/2016
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
ms.openlocfilehash: 0d573fac938f5e4d62c99c8cd6e676b96123a0c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232920"
---
# <a name="multibyte-and-wide-characters"></a>Znaki wielobajtowe i dwubajtowe

Znak wielobajtowy jest znakiem składa się z sekwencji bajtów jednego lub więcej. Każda sekwencja bajtów reprezentuje pojedynczy znak z zestawu znaków rozszerzonych. Znaki wielobajtowe są używane w zestawach znaków, takich jak Kanji.

Znaki dwubajtowe są kody znaków wielu języków, które są zawsze szerokiego 16 bitów. Typ dla stałych znaków jest `char`; dla znaków dwubajtowych, typ jest `wchar_t`. Znaki dwubajtowe są zawsze o stałym rozmiarze, przy użyciu znaków dwubajtowych upraszcza programowania, korzystając z zestawów znaków międzynarodowych.

Literał ciągów znaków dwubajtowych `L"hello"` staje się tablicy liczb całkowitych sześć typu `wchar_t`.

```
{L'h', L'e', L'l', L'l', L'o', 0}
```

Specyfikacja Unicode jest specyfikacja dla znaków dwubajtowych. Procedury biblioteki wykonawczej specyficznej dla tłumaczenie między znaki wielobajtowe i dwubajtowe obejmują `mbstowcs`, `mbtowc`, `wcstombs`, i `wctomb`.

## <a name="see-also"></a>Zobacz także

[Identyfikatory w języku C](../c-language/c-identifiers.md)
