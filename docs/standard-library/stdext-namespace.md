---
title: stdext — Przestrzeń nazw
ms.date: 09/06/2017
f1_keywords:
- stdext
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
ms.openlocfilehash: aeba486393e6b45481108f967f3de8eb73a0adea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468487"
---
# <a name="stdext-namespace"></a>stdext — Przestrzeń nazw

Elementy członkowskie [ \<hash_map >](../standard-library/hash-map.md) i [ \<hash_set >](../standard-library/hash-set.md) plików nagłówkowych nie są obecnie częścią standardu ISO C++. Dlatego te typy i elementy członkowskie zostały przeniesione z `std` przestrzeni nazw do obszaru nazw `stdext`, aby zachować zgodność ze standardem C++.

Podczas kompilowania za pomocą [/Ze](../build/reference/za-ze-disable-language-extensions.md), co jest ustawieniem domyślnym, kompilator wyświetla ostrzeżenie, korzystający z `std` dla elementów członkowskich \<hash_map > i \<hash_set > pliki nagłówkowe. Aby wyłączyć to ostrzeżenie, użyj [ostrzeżenie](../preprocessor/warning.md) pragmy.

Aby kompilator generuje błąd użycia `std` dla uczestników programu \<hash_map > i \<hash_set > pliki nagłówkowe z **/Ze**, Dodaj następujące dyrektywy, przed `#include` wszystkie pliki nagłówkowe standardowej biblioteki języka C++.

```cpp
#define _DEFINE_DEPRECATED_HASH_CLASSES 0
```

Podczas kompilowania za pomocą **/Za**, kompilator generuje błąd.

## <a name="see-also"></a>Zobacz też

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)

