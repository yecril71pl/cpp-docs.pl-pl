---
title: Błąd kompilatora C2571 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2571
dev_langs:
- C++
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30cc078251d0511da77e08690db275a788973ffb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067938"
---
# <a name="compiler-error-c2571"></a>Błąd kompilatora C2571

'Funkcja': funkcja wirtualna nie może być w Unii "union"

Unii jest zadeklarowana za pomocą funkcji wirtualnej. Można zadeklarować funkcję wirtualną tylko w klasie lub strukturze.  Możliwe rozwiązania:

1. Zmień Unii klasy lub struktury.

1. Ustaw funkcję niewirtualne.

Poniższy przykład spowoduje wygenerowanie C2571:

```
// C2571.cpp
// compile with: /c
union A {
   virtual void func1();   // C2571
   void func2();   // OK
};
```