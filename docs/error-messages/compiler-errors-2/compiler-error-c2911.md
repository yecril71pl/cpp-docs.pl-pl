---
title: Błąd kompilatora C2911
ms.date: 11/04/2016
f1_keywords:
- C2911
helpviewer_keywords:
- C2911
ms.assetid: 83c7c01a-ab6a-4179-9fb0-289a9ec8d44e
ms.openlocfilehash: 59061ab8126e3ba45c0b456bb4428652cab8a7e9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761104"
---
# <a name="compiler-error-c2911"></a>Błąd kompilatora C2911

"member": nie można zadeklarować ani zdefiniować w bieżącym zakresie

Wewnątrz przestrzeni nazw, klasy lub funkcji można zdefiniować tylko składową tego samego obszaru nazw, klasy lub funkcji lub elementu członkowskiego, który jest ujęty w tę samą przestrzeń nazw, klasę lub funkcję.

Poniższy przykład generuje C2911:

```cpp
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
