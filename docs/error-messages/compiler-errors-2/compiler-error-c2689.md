---
title: Błąd kompilatora C2689 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2689
dev_langs:
- C++
helpviewer_keywords:
- C2689
ms.assetid: b5216fba-524d-4194-9168-26e9dc5210ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fedb865a1c0c6e1bbefc94c03549936951b84e17
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099895"
---
# <a name="compiler-error-c2689"></a>Błąd kompilatora C2689

'Funkcja': funkcja zaprzyjaźniona nie może być zdefiniowana w ramach lokalnej klasy

Można zadeklarować, ale definiuje funkcja zaprzyjaźniona klasy lokalnej.

Poniższy przykład spowoduje wygenerowanie C2689:

```
// C2689.cpp
// compile with: /c
void g() {
   void f2();
   class X {
      friend void f2(){}   // C2689
      friend void f2();   // OK
   };
}
```