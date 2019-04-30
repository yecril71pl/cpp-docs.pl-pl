---
title: Błąd kompilatora C2272
ms.date: 11/04/2016
f1_keywords:
- C2272
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
ms.openlocfilehash: 1a5a1e47a721cb6edd795012cc45943e63708936
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388894"
---
# <a name="compiler-error-c2272"></a>Błąd kompilatora C2272

'Funkcja': Modyfikatory niedozwolone dla statycznych funkcji składowych

A `static` składowa jest zadeklarowana za pomocą specyfikatora model pamięci, takich jak [const](../../cpp/const-cpp.md) lub [volatile](../../cpp/volatile-cpp.md), i takie modyfikatorów nie są dozwolone w `static` funkcji elementów członkowskich.

Poniższy przykład spowoduje wygenerowanie C2272:

```
// C2272.cpp
// compile with: /c
class CMyClass {
public:
   static void func1() const volatile;   // C2272  func1 is static
   void func2() const volatile;   // OK
};
```