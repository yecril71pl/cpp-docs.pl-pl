---
title: Błąd kompilatora C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: 5c11133fbf28cfb98de1367955c00c899e8b1042
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214532"
---
# <a name="compiler-error-c3646"></a>Błąd kompilatora C3646

> "specyfikator": nieznany specyfikator przesłonięcia

## <a name="remarks"></a>Uwagi

Kompilator znalazł token w pozycji, gdzie oczekiwano, aby znaleźć specyfikator przesłonięcia, ale token nie został rozpoznany przez kompilator.

Na przykład jeśli nierozpoznany *specyfikator* jest **_NOEXCEPT**, zastąp go słowem kluczowym **`noexcept`** .

Aby uzyskać więcej informacji, zobacz [specyfikatory przesłonięć](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3646 i przedstawia sposób jego rozwiązania:

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```
