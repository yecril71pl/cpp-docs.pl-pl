---
title: Błąd kompilatora C2702 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2702
dev_langs:
- C++
helpviewer_keywords:
- C2702
ms.assetid: 6def15d4-9a8d-43e7-ae35-42d7cb57c27e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cbec8fe50c87cfc609cad5098779bc22ddae84cb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061243"
---
# <a name="compiler-error-c2702"></a>Błąd kompilatora C2702

__except mogą nie są wyświetlane w bloku

Program obsługi wyjątku (`__try`/`__except`) nie mogą być zagnieżdżone wewnątrz `__finally` bloku.

Poniższy przykład spowoduje wygenerowanie C2702:

```
// C2702.cpp
// processor: x86 IPF
int Counter;
int main() {
   __try {}
   __finally {
      __try {}   // C2702
      __except( Counter ) {}   // C2702
   }
}
```