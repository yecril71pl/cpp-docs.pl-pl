---
title: Ostrzeżenie kompilatora C4430
ms.date: 11/04/2016
f1_keywords:
- C4430
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
ms.openlocfilehash: 091d988a5af277e78a2954eb5b0b95bc64c56069
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165265"
---
# <a name="compiler-warning-c4430"></a>Ostrzeżenie kompilatora C4430

brak specyfikatora typu — zakładany int. Uwaga: C++ nie obsługuje funkcji default-int

Ten błąd może być wygenerowany jako wynik zgodności kompilatora, który został wykonany dla programu Visual Studio 2005: wszystkie deklaracje muszą jawnie określać typ; wartość int nie jest już założono.

C4430 jest zawsze wystawiony jako błąd.  To ostrzeżenie można wyłączyć za pomocą `#pragma warning` lub **/WD**; Aby uzyskać więcej informacji, zobacz [Ostrzeżenie](../../preprocessor/warning.md) lub [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżenia)](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C4430.

```cpp
// C4430.cpp
// compile with: /c
struct CMyClass {
   CUndeclared m_myClass;  // C4430
   int m_myClass;  // OK
};

typedef struct {
   POINT();   // C4430
   // try the following line instead
   // int POINT();
   unsigned x;
   unsigned y;
} POINT;
```
