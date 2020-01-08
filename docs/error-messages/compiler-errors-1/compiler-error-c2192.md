---
title: Błąd kompilatora C2192
ms.date: 11/04/2016
f1_keywords:
- C2192
helpviewer_keywords:
- C2192
ms.assetid: a147197e-e72d-4620-939b-f9e08d7c7c12
ms.openlocfilehash: ab04ce47df110036cb0b55d2e24866b52fe74f2e
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301863"
---
# <a name="compiler-error-c2192"></a>Błąd kompilatora C2192

Deklaracja parametru "number" różni się

Funkcja języka C została zadeklarowana po raz drugi z inną listą parametrów. Język C nie obsługuje przeciążonych funkcji.

Poniższy przykład generuje C2192:

```c
// C2192.c
// compile with: /Za /c
void func( float, int );
void func( int, float );   // C2192, different parameter list
void func2( int, float );   // OK
```
