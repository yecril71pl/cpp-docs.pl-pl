---
title: Kompilator ostrzeżenie (poziom 3) C4538
ms.date: 11/04/2016
f1_keywords:
- C4538
helpviewer_keywords:
- C4538
ms.assetid: 747e3d51-b6d0-41c1-a726-7af3253b59d7
ms.openlocfilehash: e0f20c7b1d9f840bc272cd3b9d43f4872ac3f71d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779235"
---
# <a name="compiler-warning-level-3-c4538"></a>Kompilator ostrzeżenie (poziom 3) C4538

"type": kwalifikatory const/volatile dla tego typu nie są obsługiwane.

Słowo kluczowe kwalifikator została zastosowana do tablicy niepoprawnie. Aby uzyskać więcej informacji, zobacz [tablicy](../../extensions/arrays-cpp-component-extensions.md).

Poniższy przykład spowoduje wygenerowanie C4538:

```
// C4538.cpp
// compile with: /clr /W3 /LD
const array<int> ^f1();   // C4538
array<const int> ^f2();   // OK
```