---
title: Błąd narzędzi konsolidatora LNK2008 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2008
dev_langs:
- C++
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18eda06e7f133ada4de1b7ec28ac21be205a71f7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086814"
---
# <a name="linker-tools-error-lnk2008"></a>Błąd narzędzi konsolidatora LNK2008

Cel naprawy nie jest wyrównany symbol_name

LINK znaleziono cel naprawy w pliku obiektu, który nie został prawidłowo wyrównane.

Ten błąd może być spowodowany przez wyrównanie sekcji niestandardowej (na przykład #pragma [pakiet](../../preprocessor/pack.md)), [wyrównać](../../cpp/align-cpp.md) modyfikator, lub przy użyciu kodu języka zestawu, który modyfikuje wyrównanie sekcji.

Jeśli Twój kod nie korzysta z żadnego z powyższych, może to być spowodowane przez kompilator.