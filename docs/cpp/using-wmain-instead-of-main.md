---
title: Korzystanie z wmain zamiast main
ms.date: 11/04/2016
f1_keywords:
- wmain
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
ms.openlocfilehash: f47d7219a54b197ec59f109cf08879774b48e6f7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857219"
---
# <a name="using-wmain-instead-of-main"></a>Korzystanie z wmain zamiast main

**Microsoft Specific**

W modelu programowania Unicode można zdefiniować wersję o szerokim znaku funkcji `main`. Użyj **wmain** zamiast `main`, jeśli chcesz napisać kod przenośny, który jest zgodny ze specyfikacją Unicode.

Należy zadeklarować formalne parametry do **wmain** przy użyciu podobnego formatu do `main`. Następnie można przekazywać argumenty o szerokim znaku oraz, opcjonalnie, wskaźnik środowiska do programu. Parametry *argv* i *envp* do **wmain** są typu `wchar_t*`.

Jeśli program używa funkcji `main`, środowisko znaków wielobajtowych jest tworzone przez system operacyjny podczas uruchamiania programu. Dwubajtowa kopia środowiska jest tworzona tylko wtedy, gdy jest to konieczne (na przykład przez wywołanie [_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md) lub funkcji [_wputenv](../c-runtime-library/reference/putenv-wputenv.md) ). Podczas pierwszego wywołania do `_wputenv`lub pierwszego wywołania `_wgetenv`, jeśli środowisko MBCS już istnieje, jest tworzone odpowiednie środowisko ciągu znaków dwubajtowych, a następnie wskazywane przez `_wenviron` zmienną globalną, która jest wersją znaku dwubajtowego `_environ` zmiennej globalnej. W tym momencie dwie kopie środowiska (MBCS i Unicode) istnieją jednocześnie i są obsługiwane przez system operacyjny przez cały czas trwania programu.

Podobnie, jeśli program używa funkcji **wmain** , środowisko MBCS (ASCII) jest tworzone podczas pierwszego wywołania do `_putenv` lub `getenv`i jest wskazywane przez zmienną globalną `_environ`.

Aby uzyskać więcej informacji na temat środowiska MBCS, zobacz [zestawy znaków jednobajtowych i](../c-runtime-library/single-byte-and-multibyte-character-sets.md) wielobajtowych w *dokumentacji biblioteki wykonawczej.*

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[main: uruchamianie programu](../cpp/main-program-startup.md)