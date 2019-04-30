---
title: Błąd kompilatora C3920
ms.date: 11/04/2016
f1_keywords:
- C3920
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
ms.openlocfilehash: d7163cf07a440a0afd1216b3e5cf665326ffb963
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386606"
---
# <a name="compiler-error-c3920"></a>Błąd kompilatora C3920

"operator": nie można definiować przyrostkowego inkrementacyjnego/dekrementacyjnego WinRT lub operator CLR wywołanie przyrostkowego operatora WinRT lub środowiska CLR będzie wywoływać odpowiedni prefiks WinRT, czy CLR — operator (op_Increment/op_Decrement), ale semantyka przyrostka

Środowisko uruchomieniowe Windows i środowiska CLR nie obsługują przyrostkowego operatora i operatory przyrostkowe zdefiniowanych przez użytkownika nie są dozwolone.  Można zdefiniować operator prefiksu i będzie można używać operatora prefiks dla operacji przed i po przyrostu.

Poniższy przykład generuje C3920 i pokazuje, jak go naprawić:

```
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