---
title: Błąd kompilatora C3132
ms.date: 11/04/2016
f1_keywords:
- C3132
helpviewer_keywords:
- C3132
ms.assetid: d54a3d12-336a-4ed0-ad4e-43cddac33b5e
ms.openlocfilehash: 1a97e04747cb92909380e66d1f4ea8ca62183054
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349883"
---
# <a name="compiler-error-c3132"></a>Błąd kompilatora C3132

"parametr funkcji": tablice parametrów można stosować tylko do formalnego argumentu typu "single-dimensional tablicy zarządzanej"

<xref:System.ParamArrayAttribute> Atrybut został zastosowany do parametru, który nie był tablicy jednowymiarowej.

Poniższy przykład spowoduje wygenerowanie C3132:

```
// C3132.cpp
// compile with: /clr /c
using namespace System;
void f( [ParamArray] Int32[,] );   // C3132
void g( [ParamArray] Int32[] );   // C3132

void h( [ParamArray] array<Char ^> ^ MyArray );   // OK
```