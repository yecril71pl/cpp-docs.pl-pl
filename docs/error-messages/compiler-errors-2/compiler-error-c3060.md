---
title: Błąd kompilatora C3060 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3060
dev_langs:
- C++
helpviewer_keywords:
- C3060
ms.assetid: 6282bb92-0546-4b59-9435-d3840bf93bdb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c053f7b92ae12b3e99792603cf7b3c5ac9b49227
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108602"
---
# <a name="compiler-error-c3060"></a>Błąd kompilatora C3060

"członek": funkcja zaprzyjaźniona nie może być zdefiniowana wewnątrz klasy przy użyciu kwalifikowanej nazwy (go może być tylko zadeklarowana)

Funkcja zaprzyjaźniona został zdefiniowany przy użyciu kwalifikowanej nazwy, co jest niedozwolone.

Poniższy przykład spowoduje wygenerowanie C3060:

```
// C3060.cpp
class A {
public:
   void func();
};

class C {
public:
   friend void A::func() { }   // C3060
   // Try the following line and the out of class definition:
   // friend void A::func();
};

// void A::func(){}
```