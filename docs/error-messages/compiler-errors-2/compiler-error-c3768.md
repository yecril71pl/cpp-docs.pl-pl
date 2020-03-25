---
title: Błąd kompilatora C3768
ms.date: 11/04/2016
f1_keywords:
- C3768
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
ms.openlocfilehash: 534be9e3873276313335ca921264be92c9259b93
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165746"
---
# <a name="compiler-error-c3768"></a>Błąd kompilatora C3768

> nie można przyjąć adresu wirtualnej funkcji vararg w czystym kodzie zarządzanym

## <a name="remarks"></a>Uwagi

**/CLR: Pure** kompilator Option jest przestarzały w programie visual Studio 2015 i nieobsługiwany w programie visual Studio 2017.

Podczas kompilowania z **/CLR: Pure**nie można przyjąć adresu wirtualnej funkcji `vararg`.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3768:

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
