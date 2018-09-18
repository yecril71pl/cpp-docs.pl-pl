---
title: Błąd kompilatora C2815 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2815
dev_langs:
- C++
helpviewer_keywords:
- C2815
ms.assetid: d0256fd6-0721-4c99-b03c-52d96e77a613
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 192c991cfee9fb1925601719ea61c47c5227c753
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057664"
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