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

Znak wielobajtowy jest znakiem składającym się z sekwencji z co najmniej jednego bajtu. Każda sekwencja bajtów reprezentuje pojedynczy znak w rozszerzonym zestawie znaków. Znaki wielobajtowe są używane w zestawach znaków, takich jak kanji.

Znaki dwubajtowe są wielojęzycznymi kodami znaków, które są zawsze o 16 bitów. Typem dla stałych znaków jest `char`; w przypadku znaków dwubajtowych typem `wchar_t`jest. Ze względu na to, że znaki dwubajtowe są zawsze stałym rozmiarem, używanie znaków dwubajtowych upraszcza programowanie przy użyciu międzynarodowych zestawów znaków

Literał `L"hello"` ciągu znaków dwubajtowych jest tablicą sześciu liczb całkowitych typu `wchar_t`.

```
{L'h', L'e', L'l', L'l', L'o', 0}
```

Specyfikacja Unicode jest specyfikacją dla znaków dwubajtowych. Procedury biblioteki wykonawczej do translacji między znakami wielobajtowymi i szerokimi `mbstowcs`obejmują `mbtowc`, `wcstombs`,, `wctomb`i.

## <a name="see-also"></a>Zobacz też

[Identyfikatory w języku C](../c-language/c-identifiers.md)
