---
title: Błąd kompilatora C3204
ms.date: 11/04/2016
f1_keywords:
- C3204
helpviewer_keywords:
- C3204
ms.assetid: 06e578da-0262-48c8-b2ae-be1cd6d28884
ms.openlocfilehash: 72b9f4fe926b617d7c5b3538fb9d3281e1d95a5f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738703"
---
# <a name="compiler-error-c3204"></a>Błąd kompilatora C3204

nie można wywołać elementu "_alloca" z wewnątrz bloku catch

Ten błąd występuje, gdy używasz wywołania do [_alloca](../../c-runtime-library/reference/alloca.md) z wewnątrz bloku catch.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3204:

```cpp
// C3204.cpp
// compile with: /EHsc
#include <malloc.h>

void ShowError(void)
{
   try
   {
   }
   catch(...)
   {
      _alloca(1);   // C3204
   }
}
```
