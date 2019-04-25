---
title: Błąd kompilatora C2710
ms.date: 11/04/2016
f1_keywords:
- C2710
helpviewer_keywords:
- C2710
ms.assetid: a2a6bb5b-86ad-4a6c-acd0-e2bef8464e0e
ms.openlocfilehash: 54d501d43652bb8e54092d44042a9525ef6f708f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160916"
---
# <a name="compiler-error-c2710"></a>Błąd kompilatora C2710

"konstruowania": "__declspec(modifier)" można stosować tylko do funkcji zwracającej wskaźnik

Funkcja, której wartość zwracana jest wskaźnikiem typu jest tylko konstrukcji, do którego `modifier` mogą być stosowane.

Poniższy przykład spowoduje wygenerowanie C2710:

```
// C2710.cpp
__declspec(restrict) void f();   // C2710
// try the following line instead
__declspec(restrict) int * g();
```