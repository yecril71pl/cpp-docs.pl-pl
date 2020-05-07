---
title: Testowanie znaków
ms.date: 11/04/2016
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
ms.openlocfilehash: b02d07ca2796e5088c3021f1ae8795ea92761943
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740099"
---
# <a name="character-testing"></a>Testowanie znaków

**ANSI 4.3.1** Zestawy `isalnum`znaków testowane przez, `isalpha`, `iscntrl` `islower` `isprint`,,, i funkcje `isupper`

Na poniższej liście opisano te funkcje, które są implementowane przez kompilator języka Microsoft C.

|Funkcja|Testy dla|
|--------------|---------------|
|`isalnum`|Znaki 0-9, A-Z, a-z ASCII 48-57, 65-90, 97-122|
|`isalpha`|Znaki A-Z, a-z ASCII 65-90, 97-122|
|`iscntrl`|ASCII 0 -31, 127|
|`islower`|Znaki a-z ASCII 97-122|
|`isprint`|Znaki A-Z, a-z, 0-9, interpunkcja, spacja ASCII 32-126|
|`isupper`|Znaki A-Z ASCII 65-90|

## <a name="see-also"></a>Zobacz też

[Funkcje bibliotek](../c-language/library-functions.md)
