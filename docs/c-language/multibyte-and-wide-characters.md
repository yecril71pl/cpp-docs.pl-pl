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
ms.openlocfilehash: 2522761389a7f97acf4157683f8fce19e94429d8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100534"
---
# <a name="multibyte-and-wide-characters"></a>Znaki wielobajtowe i dwubajtowe

Znak wielobajtowy jest znakiem składa się z sekwencji bajtów jednego lub więcej. Każda sekwencja bajtów reprezentuje pojedynczy znak z zestawu znaków rozszerzonych. Znaki wielobajtowe są używane w zestawach znaków, takich jak Kanji.

Znaki dwubajtowe są kody znaków wielu języków, które są zawsze szerokiego 16 bitów. Typ dla stałych znaków jest `char`; dla znaków dwubajtowych, typ jest `wchar_t`. Znaki dwubajtowe są zawsze o stałym rozmiarze, przy użyciu znaków dwubajtowych upraszcza programowania, korzystając z zestawów znaków międzynarodowych.

Literał ciągów znaków dwubajtowych `L"hello"` staje się tablicy liczb całkowitych sześć typu `wchar_t`.

```
{L'h', L'e', L'l', L'l', L'o', 0}
```

Specyfikacja Unicode jest specyfikacja dla znaków dwubajtowych. Procedury biblioteki wykonawczej specyficznej dla tłumaczenie między znaki wielobajtowe i dwubajtowe obejmują `mbstowcs`, `mbtowc`, `wcstombs`, i `wctomb`.

## <a name="see-also"></a>Zobacz też

[Identyfikatory w języku C](../c-language/c-identifiers.md)