---
title: Błąd kompilatora C3768
ms.date: 11/04/2016
f1_keywords:
- C3768
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
ms.openlocfilehash: e9c385fd178dc967e72f5e0ca7fab27b28ad962f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676750"
---
# <a name="compiler-error-c3768"></a>Błąd kompilatora C3768

> Nie można przyjąć adresu wirtualnej funkcji vararg w czystym kodzie zarządzanym

## <a name="remarks"></a>Uwagi

**/CLR: pure** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Podczas kompilowania za pomocą **/CLR: pure**, nie można przyjąć adresu wirtualnej `vararg` funkcji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3768:

```cpp
// C3768.cpp
// compile with: /clr:pure
struct A
{
   virtual void f(...);
};

int main()
{
   &(A::f);   // C3768
}
```