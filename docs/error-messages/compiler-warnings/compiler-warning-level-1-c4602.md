---
title: Ostrzeżenie kompilatora (poziom 1) C4602
ms.date: 11/04/2016
f1_keywords:
- C4602
helpviewer_keywords:
- C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
ms.openlocfilehash: 7cacadea560dc5a68d396ac607deb3a5a3c236ee
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965915"
---
# <a name="compiler-warning-level-1-c4602"></a>Ostrzeżenie kompilatora (poziom 1) C4602

\#pragma pop_macro: "Nazwa makra" nie ma wcześniejszych #pragma push_macro dla tego identyfikatora

Jeśli używasz [pop_macro](../../preprocessor/pop-macro.md) dla określonego makra, musisz najpierw przesłać tę nazwę makra do [push_macro](../../preprocessor/push-macro.md). Na przykład poniższy przykład generuje C4602:

```cpp
// C4602.cpp
// compile with: /W1
int main()
{
   #pragma pop_macro("x")   // C4602 x is not on the stack
}
```