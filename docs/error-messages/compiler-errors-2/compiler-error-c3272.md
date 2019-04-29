---
title: Błąd kompilatora C3272
ms.date: 11/04/2016
f1_keywords:
- C3272
helpviewer_keywords:
- C3272
ms.assetid: 7cdf254d-f207-4116-a1bf-7386f3b82a6f
ms.openlocfilehash: 3e4348dcce0cfd04234b515877d788e5330f8e4c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365692"
---
# <a name="compiler-error-c3272"></a>Błąd kompilatora C3272

'symbol': symbol wymaga FieldOffset, ponieważ jest to składowa typu typename zdefiniowaną przez StructLayout(LayoutKind::Explicit)

Gdy `StructLayout(LayoutKind::Explicit)` obowiązuje, pola muszą być oznaczone `FieldOffset`.

Poniższy przykład spowoduje wygenerowanie C3272:

```
// C3272_2.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Explicit)]
ref struct X
{
   int data_;   // C3272
   // try the following line instead
   // [FieldOffset(0)] int data_;
};
```
