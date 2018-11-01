---
title: Błąd kompilatora C3553
ms.date: 11/04/2016
f1_keywords:
- C3553
helpviewer_keywords:
- C3553
ms.assetid: 7f84bf37-6419-4ad3-ab30-64266100b930
ms.openlocfilehash: 219592f2403904f9923e84bfd4539a22cddd02de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543432"
---
# <a name="compiler-error-c3553"></a>Błąd kompilatora C3553

> decltype oczekuje wyrażenia nie typu

`decltype()` — Słowo kluczowe wymaga wyrażenia jako argument, a nie nazwę typu. Na przykład ostatnią instrukcję w następujący fragment kodu powoduje błąd C3553.

```cpp
int x = 0;
decltype(x+1);
decltype(int); // C3553
```