---
title: Błąd kompilatora C3230 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3230
dev_langs:
- C++
helpviewer_keywords:
- C3230
ms.assetid: 5ec53f25-59f6-4801-81e7-7b68bf04994d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f74e17b1dec3aba78a38d993da81995d00c93784
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065605"
---
# <a name="compiler-error-c3230"></a>Błąd kompilatora C3230

'Funkcja': argument typu szablonu dla "template" nie może zawierać parametru typu generycznego: "param"

Szablony są tworzone w czasie kompilacji, ale typy ogólne są tworzone w czasie wykonywania. W związku z tym nie jest możliwe wygenerować kod ogólny, który można wywołać tego szablonu, ponieważ nie można utworzyć wystąpienia szablonu w czasie wykonywania, gdy na koniec jest znany typ ogólny.

Poniższy przykład spowoduje wygenerowanie C3230:

```
// C3230.cpp
// compile with: /clr /LD
template <class S>
void f(S t);

generic <class U>
ref class C {
   void f1(U x) {
      f(x);   // C3230
   }
};
```