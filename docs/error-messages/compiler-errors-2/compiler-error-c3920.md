---
title: Błąd kompilatora C3920
ms.date: 11/04/2016
f1_keywords:
- C3920
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
ms.openlocfilehash: e3c37cba4b7df2df9e9784b3a1afb8dbf9c8e8d9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491731"
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