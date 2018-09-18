---
title: Korzystanie z wmain zamiast main | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- wmain
dev_langs:
- C++
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 274065ac3d753b744813a1fc88804ea26d44487d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104377"
---
# <a name="using-wmain-instead-of-main"></a>Korzystanie z wmain zamiast main

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

W modelu programowania Unicode, można zdefiniować wersja znaków dwubajtowych `main` funkcji. Użyj **wmain** zamiast `main` Jeśli chcesz tworzyć przenośny kod, który jest zgodna ze specyfikacją Unicode.

Możesz deklarować Parametry formalne dla **wmain** formacie podobne do `main`. Możesz następnie przekazać argumenty znaków dwubajtowych i, opcjonalnie, wskaźnik znaku dwubajtowego środowiska do programu. *Argv* i *envp* parametry **wmain** typu `wchar_t*`.

Jeśli program używa `main` funkcji środowiska znak wielobajtowy jest tworzony przez system operacyjny w momencie uruchamiania programu. Tworzona jest kopia znaków dwubajtowych, środowiska, tylko wtedy, gdy jest to wymagane (na przykład przez wywołanie [_wgetenv —](../c-runtime-library/reference/getenv-wgetenv.md) lub [_wputenv —](../c-runtime-library/reference/putenv-wputenv.md) funkcji). W pierwszym wywołaniu `_wputenv`, lub na pierwsze wywołanie `_wgetenv` Jeśli istnieje już środowisko MBCS, odpowiednie środowisko ciąg znaków dwubajtowych jest tworzony i następnie jest wskazywany przez `_wenviron` zmiennej globalnej, czyli znaków dwubajtowych Wersja `_environ` zmiennej globalnej. W tym momencie dwie kopie środowiska (MBCS i Unicode) mogły współistnieć i są obsługiwane przez system operacyjny w całym cyklu życia programu.

Podobnie jeśli program używa **wmain** , środowisko MBCS (ASCII) zostanie utworzona funkcja w pierwszym wywołaniu `_putenv` lub `getenv`i jest wskazywany przez `_environ` zmiennej globalnej.

Aby uzyskać więcej informacji na temat środowiska MBCS, zobacz [zestawów znaków wielobajtowych i jednobajtowych](../c-runtime-library/single-byte-and-multibyte-character-sets.md) w *odwołanie do biblioteki wykonawczej.*

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[main: uruchamianie programu](../cpp/main-program-startup.md)