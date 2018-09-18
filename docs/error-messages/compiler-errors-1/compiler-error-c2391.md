---
title: Błąd kompilatora C2391 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2391
dev_langs:
- C++
helpviewer_keywords:
- C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1201651ffc52dae7b8f184895f8005750ee4697e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102375"
---
# <a name="compiler-error-c2391"></a>Błąd kompilatora C2391

'Identyfikator': "friend" nie może zostać użyty podczas definicji typu

`friend` Deklaracja zawiera deklarację klasy ukończone. A `friend` deklaracji można określić funkcji składowej lub specyfikatorze typu złożonego, ale nie deklaracji klasy ukończone.

Poniższy przykład spowoduje wygenerowanie C2326:

```
// C2391.cpp
// compile with: /c
class D {
   void func( int );
};

class A {
   friend class B { int i; };   // C2391

   // OK
   friend class C;
   friend void D::func(int);
};
```