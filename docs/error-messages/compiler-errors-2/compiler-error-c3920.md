---
title: Błąd kompilatora C3920 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3920
dev_langs:
- C++
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b85638907f350eb3545a858f1319e56b2459f09
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112710"
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