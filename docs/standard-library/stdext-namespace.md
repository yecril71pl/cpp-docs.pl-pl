---
title: stdext — Przestrzeń nazw
ms.date: 09/06/2017
f1_keywords:
- stdext
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
ms.openlocfilehash: d40f3f7a99db72784cc9a32a9c37064228597d34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412426"
---
# <a name="stdext-namespace"></a>stdext — Przestrzeń nazw

Elementy członkowskie [ \<hash_map >](../standard-library/hash-map.md) i [ \<hash_set >](../standard-library/hash-set.md) plików nagłówkowych nie są obecnie częścią ISO C++ standardowych. Dlatego te typy i elementy członkowskie zostały przeniesione z `std` przestrzeni nazw do obszaru nazw `stdext`, aby zachować zgodność ze standardem C++.

Podczas kompilowania za pomocą [/Ze](../build/reference/za-ze-disable-language-extensions.md), co jest ustawieniem domyślnym, kompilator wyświetla ostrzeżenie, korzystający z `std` dla elementów członkowskich \<hash_map > i \<hash_set > pliki nagłówkowe. Aby wyłączyć to ostrzeżenie, użyj [ostrzeżenie](../preprocessor/warning.md) pragmy.

Aby kompilator generuje błąd użycia `std` dla uczestników programu \<hash_map > i \<hash_set > pliki nagłówkowe z **/Ze**, Dodaj następujące dyrektywy, przed `#include` wszelkie C++ pliki nagłówkowe standardowej biblioteki.

```cpp
#define _DEFINE_DEPRECATED_HASH_CLASSES 0
```

Podczas kompilowania za pomocą **/Za**, kompilator generuje błąd.

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)
