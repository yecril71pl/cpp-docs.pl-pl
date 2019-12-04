---
title: Błąd kompilatora C3053
ms.date: 11/04/2016
f1_keywords:
- C3053
helpviewer_keywords:
- C3053
ms.assetid: ab9a25f3-e341-4f6e-8e69-069b4a963a64
ms.openlocfilehash: 07514dfb931dcb5bf45bb8526cd19cf19103a56f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761207"
---
# <a name="compiler-error-c3053"></a>Błąd kompilatora C3053

"symbol": "threadprivate" jest prawidłowy tylko dla elementów danych globalnych lub statycznych

Symbole przesyłane do [threadprivate](../../parallel/openmp/reference/threadprivate.md) muszą być globalne lub statyczne.

Poniższy przykład generuje C3053:

```cpp
// C3053.cpp
// compile with: /openmp
void Test() {
   int x, y;
   #pragma omp threadprivate(x, y)   // C3053
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```

Możliwe rozwiązanie:

```cpp
// C3053b.cpp
// compile with: /openmp /LD
int x, y;
#pragma omp threadprivate(x, y)

void Test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```
