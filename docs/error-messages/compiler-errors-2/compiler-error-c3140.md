---
title: Błąd kompilatora C3140
ms.date: 11/04/2016
f1_keywords:
- C3140
helpviewer_keywords:
- C3140
ms.assetid: 122f8943-fac3-4db8-a3a8-2c5d19233de6
ms.openlocfilehash: 672930d8c1d864c8ee5c2a08daca663bd29df167
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506149"
---
# <a name="compiler-error-c3140"></a>Błąd kompilatora C3140

nie można mieć wielu atrybutów "module" w tej samej jednostce kompilacji

Atrybut [modułu](../../windows/attributes/module-cpp.md) można zdefiniować tylko raz dla każdego projektu.

Poniższy przykład generuje C3140:

```cpp
// C3140.cpp
// compile with: /c
[emitidl];
[module(name = "MyLibrary")];
[module(name = "MyLibrary2")];   // C3140
```
