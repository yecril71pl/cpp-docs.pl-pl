---
title: Błąd kompilatora C2794 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2794
dev_langs:
- C++
helpviewer_keywords:
- C2794
ms.assetid: d508191c-9044-4c6a-9119-4bca668c0b93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c81e8dcfde2a24c4a827406c3e499c12e891b2f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068016"
---
# <a name="compiler-error-c2794"></a>Błąd kompilatora C2794

'Funkcja': nie jest elementem Członkowskim wszelkie bezpośredniej lub pośredniej klasy bazowej "class"

Próbowano użyć [super](../../cpp/super.md) wywołanie funkcji nieistniejącego elementu członkowskiego.

Poniższy przykład spowoduje wygenerowanie C2794

```
// C2794.cpp
struct B {
   void mf();
};

struct D : B {
   void mf() {
      __super::f();  // C2794
   }
};
```