---
title: Ostrzeżenie kompilatora (poziom 4) C4208
ms.date: 11/04/2016
f1_keywords:
- C4208
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
ms.openlocfilehash: e15140bd2f0983bde64c89a054fd733d1ab902ac
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541866"
---
# <a name="compiler-warning-level-4-c4208"></a>Ostrzeżenie kompilatora (poziom 4) C4208

użyto niestandardowego rozszerzenia: delete [EXP]-EXP oceniono, ale zignorowano

Dzięki rozszerzeniom Microsoft (/ze) można usunąć tablicę przy użyciu wartości w nawiasach kwadratowych przy użyciu [operatora delete](../../cpp/delete-operator-cpp.md). Wartość jest ignorowana.

```cpp
// C4208.cpp
// compile with: /W4
int main()
{
   int * MyArray = new int[18];
   delete [18] MyArray;      // C4208
   MyArray = new int[18];
   delete [] MyArray;        // ok
}
```

Takie wartości są nieprawidłowe pod kątem zgodności ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).