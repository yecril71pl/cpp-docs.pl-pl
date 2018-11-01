---
title: Błąd narzędzi konsolidatora LNK2008
ms.date: 11/04/2016
f1_keywords:
- LNK2008
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
ms.openlocfilehash: 97bb2be18da5d166d1d5fba42e4ec8ce1f0439fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544225"
---
# <a name="linker-tools-error-lnk2008"></a>Błąd narzędzi konsolidatora LNK2008

Cel naprawy nie jest wyrównany symbol_name

LINK znaleziono cel naprawy w pliku obiektu, który nie został prawidłowo wyrównane.

Ten błąd może być spowodowany przez wyrównanie sekcji niestandardowej (na przykład #pragma [pakiet](../../preprocessor/pack.md)), [wyrównać](../../cpp/align-cpp.md) modyfikator, lub przy użyciu kodu języka zestawu, który modyfikuje wyrównanie sekcji.

Jeśli Twój kod nie korzysta z żadnego z powyższych, może to być spowodowane przez kompilator.