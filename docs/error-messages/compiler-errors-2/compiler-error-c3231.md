---
title: Błąd kompilatora C3231 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3231
dev_langs:
- C++
helpviewer_keywords:
- C3231
ms.assetid: fe5dc352-e634-45fa-9534-3da176294c98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57727fbd71314201ec76119d37ab9c73b01d471d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097318"
---
# <a name="compiler-error-c3231"></a>Błąd kompilatora C3231

"argument": argument typu szablonu nie można użyć parametru typu ogólnego

Szablony są tworzone w czasie kompilacji, ale typy ogólne są tworzone w czasie wykonywania. W związku z tym nie jest możliwe wygenerować kod ogólny, który można wywołać tego szablonu, ponieważ nie można utworzyć wystąpienia szablonu w czasie wykonywania, gdy na koniec jest znany typ ogólny.

Poniższy przykład spowoduje wygenerowanie C3231:

```
// C3231.cpp
// compile with: /clr /LD
template <class T> class A;

generic <class T>
ref class C {
   void f() {
      A<T> a;   // C3231
   }
};
```