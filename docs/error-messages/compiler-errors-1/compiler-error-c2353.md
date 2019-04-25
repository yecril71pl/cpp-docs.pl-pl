---
title: Błąd kompilatora C2353
ms.date: 11/04/2016
f1_keywords:
- C2353
helpviewer_keywords:
- C2353
ms.assetid: d57f8f77-d9b1-4bba-a940-87ec269ad183
ms.openlocfilehash: 3cfcb544349adc0b7b4e13472f70aac382f958fd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302855"
---
# <a name="compiler-error-c2353"></a>Błąd kompilatora C2353

Specyfikacja wyjątku nie jest dozwolone.

Specyfikacje wyjątków nie są dozwolone dla funkcji składowych klas zarządzanych.

Poniższy przykład spowoduje wygenerowanie C2353:

```
// C2353.cpp
// compile with: /clr /c
ref class X {
   void f() throw(int);   // C2353
   void f();   // OK
};
```