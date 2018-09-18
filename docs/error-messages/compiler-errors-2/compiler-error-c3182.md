---
title: Błąd kompilatora C3182 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3182
dev_langs:
- C++
helpviewer_keywords:
- C3182
ms.assetid: f3681266-308e-4990-a979-8eef8920e186
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 722f95b41f9f5ec467af25ccf927631590f90e45
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110224"
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
