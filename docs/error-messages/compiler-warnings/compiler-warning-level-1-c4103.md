---
title: Kompilator ostrzeżenie (poziom 1) C4103 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4103
dev_langs:
- C++
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1942acc2d9c5c274806e06127f9f98d4bfcb5077
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085540"
---
# <a name="compiler-warning-level-1-c4103"></a>Kompilator ostrzeżenie (poziom 1) C4103

"filename": wyrównanie zmieniono po dołączeniu nagłówka, może to być spowodowane brakiem elementu #pragma pack(pop)

Pakowanie wpływa na układ klas, a często, jeśli pakowania zmian w plikach nagłówkowych, mogą wystąpić problemy.

Użyj #pragma [pakiet](../../preprocessor/pack.md)(pop) przed zamknięciem pliku nagłówka, aby rozwiązać tego ostrzeżenia.

Poniższy przykład spowoduje wygenerowanie C4103:

```
// C4103.h
#pragma pack(push, 4)

// defintions and declarations

// uncomment the following line to resolve
// #pragma pack(pop)
```

Następnie wyszukaj maszynę

```
// C4103.cpp
// compile with: /LD /W1
#include "c4103.h"   // C4103
```