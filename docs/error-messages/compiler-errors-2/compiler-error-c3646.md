---
title: Błąd kompilatora C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: 04ff1d026c97c56611f8b786d8a7254db711e4a8
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769039"
---
# <a name="compiler-error-c3646"></a>Błąd kompilatora C3646

> "specyfikatora": nieznany specyfikator przesłonięcia

## <a name="remarks"></a>Uwagi

Tokenu można znaleźć kompilatora w miejscu, w którym ją Oczekiwano znalezienia specyfikator przesłonięcia, ale token nie został rozpoznany przez kompilator.

Na przykład jeśli rozpoznane *specyfikator* jest **_NOEXCEPT**, zastąp ją ze słowem kluczowym **noexcept**.

Aby uzyskać więcej informacji, zobacz [zastąpienie specyfikatorów](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3646 i pokazuje sposób, aby rozwiązać ten problem:

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```