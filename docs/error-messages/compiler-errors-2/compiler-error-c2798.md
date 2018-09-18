---
title: Błąd kompilatora C2798 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2798
dev_langs:
- C++
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88241989d54e1a068b226b59091a381f531dee9e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028860"
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