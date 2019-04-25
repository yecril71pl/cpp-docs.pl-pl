---
title: Błąd kompilatora C2815
ms.date: 11/04/2016
f1_keywords:
- C2815
helpviewer_keywords:
- C2815
ms.assetid: d0256fd6-0721-4c99-b03c-52d96e77a613
ms.openlocfilehash: ab6708e7ae0a56bd71adebad4fb42d6ea9abe116
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175410"
---
# <a name="compiler-error-c2815"></a>Błąd kompilatora C2815

"operator delete": pierwszy formalny parametr musi być "void *", ale zostało użyte "param"

Dowolny zdefiniowany przez użytkownika [operatora delete](../../standard-library/new-operators.md#op_delete) funkcji, należy wykonać pierwszy formalny parametr typu `void *`.

Poniższy przykład spowoduje wygenerowanie C2815:

```
// C2815.cpp
// compile with: /c
class CMyClass {
public:
   void mf1(int *a);
   void operator delete(CMyClass *);   // C2815
   void operator delete(void *);
};
```