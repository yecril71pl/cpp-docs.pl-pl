---
title: Błąd kompilatora C2344
ms.date: 11/04/2016
f1_keywords:
- C2344
helpviewer_keywords:
- C2344
ms.assetid: a84c7b37-c84e-4345-8691-c23abb2dc193
ms.openlocfilehash: d1ba3a0f975dbc96c9c6ca51a8dac89b5a614572
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188175"
---
# <a name="compiler-error-c2344"></a>Błąd kompilatora C2344

align(#): wyrównanie musi być potęgą liczby dwa

Korzystając z [wyrównać](../../cpp/align-cpp.md) — słowo kluczowe, wartość należy przekazać musi być potęgą liczby dwa.

Na przykład poniższy kod generuje C2344, ponieważ 3 nie jest potęgą liczby dwa:

```
// C2344.cpp
// compile with: /c
__declspec(align(3)) int a;   // C2344
__declspec(align(4)) int b;   // OK
```