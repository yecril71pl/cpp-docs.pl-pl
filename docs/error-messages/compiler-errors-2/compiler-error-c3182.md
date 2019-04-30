---
title: Błąd kompilatora C3182
ms.date: 11/04/2016
f1_keywords:
- C3182
helpviewer_keywords:
- C3182
ms.assetid: f3681266-308e-4990-a979-8eef8920e186
ms.openlocfilehash: 6866c7bbcee0a4097e490b344c79a6eec7f94570
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382420"
---
# <a name="compiler-error-c3182"></a>Błąd kompilatora C3182

"class": element członkowski deklaracji using lub deklaracja dostępu jest niedozwolona w ramach zarządzanej lub WinRTtype

A [przy użyciu](../../cpp/using-declaration.md) deklaracja jest nieprawidłowy w ramach wszystkich formularzy klas zarządzanych.

Poniższy przykład generuje C3182 i pokazuje, jak go naprawić.

```
// C3182a.cpp
// compile with: /clr /c
ref struct B {
   void mf(int) {
   }
};

ref struct D : B {
   using B::mf;   // C3182, delete to resolve
   void mf(char) {
   }
};
```
