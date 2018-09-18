---
title: Testowanie znaków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2c558c5d32f75561d5722a656450d5f18f5166a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084942"
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

## <a name="see-also"></a>Zobacz też

[Funkcje bibliotek](../c-language/library-functions.md)