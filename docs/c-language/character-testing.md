---
title: Testowanie znaków
ms.date: 11/04/2016
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
ms.openlocfilehash: b02d07ca2796e5088c3021f1ae8795ea92761943
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147194"
---
# <a name="character-testing"></a>Testowanie znaków

**ANSI 4.3.1** zestawów znaków sprawdzane pod kątem przez `isalnum`, `isalpha`, `iscntrl`, `islower`, `isprint`, i `isupper` funkcji

Na poniższej liście opisano te funkcje zaimplementowanego przez kompilator Microsoft C:.

|Funkcja|Testy|
|--------------|---------------|
|`isalnum`|Znaki 0 – 9, A-Z, a-z ASCII 65 – 90 48-57, 97 122|
|`isalpha`|Znaki A-Z, a-z ASCII 65 – 90, 97 122|
|`iscntrl`|ASCII 0 -31, 127|
|`islower`|A-z znaki ASCII 97-122.|
|`isprint`|Znaki A-Z, a – z, 0 - 9 i znak interpunkcyjny, miejsce ASCII 32 126|
|`isupper`|Znaki ASCII 65 – 90 A-Z|

## <a name="see-also"></a>Zobacz także

[Funkcje bibliotek](../c-language/library-functions.md)
