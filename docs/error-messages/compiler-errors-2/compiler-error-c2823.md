---
title: Błąd kompilatora C2823
ms.date: 11/04/2016
f1_keywords:
- C2823
helpviewer_keywords:
- C2823
ms.assetid: 982b1b35-1a7c-456e-b711-f80cfe2d571e
ms.openlocfilehash: c277437bdc4622e7ae8a63eb9b0a553e0079bc02
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225387"
---
# <a name="compiler-error-c2823"></a>Błąd kompilatora C2823

> szablon typedef jest niedozwolony

Szablony są niedozwolone w **`typedef`** definicjach.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2823 i pokazuje jeden ze sposobów rozwiązania tego problemu:

```cpp
// C2823.cpp
template<class T>
typedef struct x {
   T i;   // C2823 can't use T, specify data type and delete template
   int i;   // OK
} x1;
```
