---
title: Błąd kompilatora C2768
ms.date: 11/04/2016
f1_keywords:
- C2768
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
ms.openlocfilehash: bcc801bb5802598e936d577f08729214bb7e13a1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759792"
---
# <a name="compiler-error-c2768"></a>Błąd kompilatora C2768

"Function": niedozwolone użycie argumentów jawnego szablonu

Kompilator nie może określić, czy definicja funkcji powinna być jawną specjalizacją szablonu funkcji, czy też jeśli definicja funkcji miała być dla nowej funkcji.

Ten błąd został wprowadzony w programie Visual Studio .NET 2003 w ramach ulepszeń zgodności kompilatora.

Poniższy przykład generuje C2768:

```cpp
// C2768.cpp
template<typename T>
void f(T) {}

void f<int>(int) {}   // C2768

// an explicit specialization
template<>
void f<int>(int) {}

// global nontemplate function overload
void f(int) {}
```
