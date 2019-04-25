---
title: Błąd kompilatora C3126
ms.date: 11/04/2016
f1_keywords:
- C3126
helpviewer_keywords:
- C3126
ms.assetid: e72658a3-5d85-4a31-89a4-dbc3d475973d
ms.openlocfilehash: 92f01bd9a04d6350b348d734281855bb86b350d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300664"
---
# <a name="compiler-error-c3126"></a>Błąd kompilatora C3126

Nie można zdefiniować związku "union" wewnątrz typu zarządzanego "type"

Unia nie może być zdefiniowana wewnątrz typu zarządzanego.

Poniższy przykład spowoduje wygenerowanie C3126:

```
// C3126_2.cpp
// compile with: /clr /c
ref class Test
{
   union x
   {   // C3126
      int a;
      int b;
   };
};
```
