---
title: Kompilator ostrzeżenie (poziom 1) C4103
ms.date: 11/04/2016
f1_keywords:
- C4103
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
ms.openlocfilehash: 15d7403d461467e33b7e89957821a311179d33a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577817"
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