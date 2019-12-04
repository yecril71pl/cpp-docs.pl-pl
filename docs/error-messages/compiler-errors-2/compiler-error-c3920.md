---
title: Błąd kompilatora C3920
ms.date: 11/04/2016
f1_keywords:
- C3920
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
ms.openlocfilehash: 416752054f7397a058329e1ee4bdaef693dd0d28
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758466"
---
# <a name="compiler-error-c3920"></a>Błąd kompilatora C3920

"operator" ": nie można zdefiniować przyrostkowego przyrostu/zmniejszania WinRT lub operatora CLR wywołującego przyrostowy operator WinRT lub CLR wywoła odpowiadający mu prefiks WinRT lub CLR (op_Increment/op_Decrement), ale z semantyką przyrostkową

Środowisko wykonawcze systemu Windows i CLR nie obsługują operatora przyrostkowego i operatory przyrostkowe zdefiniowane przez użytkownika są niedozwolone.  Można zdefiniować operator prefiksu i operator prefiksu będzie używany dla operacji poprzedzających i po przyrost.

Poniższy przykład generuje C3920 i pokazuje, jak to naprawić:

```cpp
// C3920.cpp
// compile with: /clr /LD
public value struct V {
   static V operator ++(V me, int)
   // try the following line instead
   // static V operator ++(V me)
   {   // C3920
      me.m_i++;
      return me;
   }

   int m_i;
};
```
