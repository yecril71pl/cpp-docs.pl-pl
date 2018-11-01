---
title: Błąd kompilatora C2814
ms.date: 11/04/2016
f1_keywords:
- C2814
helpviewer_keywords:
- C2814
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
ms.openlocfilehash: 6562e8a0968f83a0e7e968b538b4d94dc1047fa5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474857"
---
# <a name="compiler-error-c2814"></a>Błąd kompilatora C2814

"członek": typ natywny nie może być zagnieżdżony w zarządzanej lub WinRT wpisz "type"

## <a name="example"></a>Przykład

Typ macierzysty nie mogą być zagnieżdżone w typie CLR lub WinRT. Poniższy przykład generuje C2814 i pokazuje, jak go naprawić.

```
// C2814.cpp
// compile with: /clr /c
ref class A {
   class B {};   // C2814
   ref class C {};   // OK
};
```
