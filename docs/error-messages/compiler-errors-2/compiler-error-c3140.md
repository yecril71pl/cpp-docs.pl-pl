---
title: Błąd kompilatora C3140
ms.date: 11/04/2016
f1_keywords:
- C3140
helpviewer_keywords:
- C3140
ms.assetid: 122f8943-fac3-4db8-a3a8-2c5d19233de6
ms.openlocfilehash: e7dde3eb27c018502225ea3bc45e4bee7c699379
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374966"
---
# <a name="compiler-error-c3140"></a>Błąd kompilatora C3140

nie może mieć wiele atrybutów "module" w tej samej jednostce kompilacyjnej

[Modułu](../../windows/module-cpp.md) atrybut może zostać zdefiniowany tylko jeden raz na projekt.

Poniższy przykład spowoduje wygenerowanie C3140:

```
// C3140.cpp
// compile with: /c
[emitidl];
[module(name = "MyLibrary")];
[module(name = "MyLibrary2")];   // C3140
```