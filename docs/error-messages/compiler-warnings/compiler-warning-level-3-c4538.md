---
title: Kompilator ostrzeżenie (poziom 3) C4538
ms.date: 11/04/2016
f1_keywords:
- C4538
helpviewer_keywords:
- C4538
ms.assetid: 747e3d51-b6d0-41c1-a726-7af3253b59d7
ms.openlocfilehash: 81634ed45ad7d09a35f8399774920f6445628dee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569367"
---
# <a name="compiler-warning-level-3-c4538"></a>Kompilator ostrzeżenie (poziom 3) C4538

"type": kwalifikatory const/volatile dla tego typu nie są obsługiwane.

Słowo kluczowe kwalifikator została zastosowana do tablicy niepoprawnie. Aby uzyskać więcej informacji, zobacz [tablicy](../../windows/arrays-cpp-component-extensions.md).

Poniższy przykład spowoduje wygenerowanie C4538:

```
// C4538.cpp
// compile with: /clr /W3 /LD
const array<int> ^f1();   // C4538
array<const int> ^f2();   // OK
```