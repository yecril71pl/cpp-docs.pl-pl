---
title: Ostrzeżenie kompilatora C4693
ms.date: 10/25/2017
f1_keywords:
- C4693
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
ms.openlocfilehash: cac5918eb4a1689fd215e07272958eeca48247ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311323"
---
# <a name="compiler-warning-c4693"></a>Ostrzeżenie kompilatora C4693

> "class": zapieczętowana klasa abstrakcyjna nie może mieć żadnych składowych wystąpienia "Test"

Jeśli typ jest oznaczony [zapieczętowanego](../../extensions/sealed-cpp-component-extensions.md) i [abstrakcyjne](../../extensions/abstract-cpp-component-extensions.md), może mieć tylko statyczne elementy członkowskie.

To ostrzeżenie zostanie automatycznie podwyższony do błędu. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4693.

```cpp
// C4693.cpp
// compile with: /clr /c
public ref class Public_Ref_Class sealed abstract {
public:
   void Test() {}   // C4693
   static void Test2() {}   // OK
};
```