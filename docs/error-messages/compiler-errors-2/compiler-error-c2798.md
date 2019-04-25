---
title: Błąd kompilatora C2798
ms.date: 11/04/2016
f1_keywords:
- C2798
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
ms.openlocfilehash: f3e8f0ac260e49866d1c654f89d34bf57a8ffbc1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152478"
---
# <a name="compiler-error-c2798"></a>Błąd kompilatora C2798

"super::member" jest niejednoznaczny

Wiele struktur dziedziczone zawierają elementu członkowskiego, do którego odwołuje się [super](../../cpp/super.md). Można naprawić błąd, wybierając:

- Usuwanie z listy dziedziczenia d. B1 i B2

- Zmiana nazwy elementu członkowskiego danych w B1 i B2.

Poniższy przykład spowoduje wygenerowanie C2798:

```
// C2798.cpp
struct B1 {
   int i;
};

struct B2 {
   int i;
};

struct D : B1, B2 {
   void g() {
      __super::i = 4; // C2798
   }
};
```