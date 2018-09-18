---
title: Błąd kompilatora C2911 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2911
dev_langs:
- C++
helpviewer_keywords:
- C2911
ms.assetid: 83c7c01a-ab6a-4179-9fb0-289a9ec8d44e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c242e72ab4f13f56644b9ab73c2a168e0591012d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041184"
---
# <a name="compiler-error-c2911"></a>Błąd kompilatora C2911

'składowa': nie może być zadeklarowane lub zdefiniowane w bieżącym zakresie

Wewnątrz przestrzeni nazw, klasy lub funkcji można zdefiniować tylko członkiem tej samej przestrzeni nazw, klasy lub funkcji lub elementu członkowskiego, która jest ujęta w tej samej przestrzeni nazw, klasy lub funkcji.

Poniższy przykład spowoduje wygenerowanie C2911:

```
// C2911.cpp
struct A;

namespace M {
   struct D;
}

namespace N {
   struct C;

   namespace O {
      struct B;
   }

   // in N
   struct ::A {};   // C2911  A is member of global NS
   struct O::B{};   // OK B is in O, O is inside of N
   struct C {};     // OK C is member of N
   struct M::D {};  // C2911 D is member of M, M not enclosed by N
}
```