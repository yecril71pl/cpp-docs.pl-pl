---
title: Błąd kompilatora C3270
ms.date: 11/04/2016
f1_keywords:
- C3270
helpviewer_keywords:
- C3270
ms.assetid: 70e6e76b-7415-48f5-a61e-2ed50caf08e4
ms.openlocfilehash: 91656ee893f2ad7b3f0c53cb157cd9faf129e4c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366046"
---
# <a name="compiler-error-c3270"></a>Błąd kompilatora C3270

"field": atrybut FieldOffset należy używać tylko w kontekście StructLayout(Explicit), w tym przypadku jest wymagana

Pole zostało oznaczone **FieldOffset**, który jest dozwolony tylko w przypadku **StructLayout(Explicit)** jest aktywna.

Poniższy przykład spowoduje wygenerowanie C3270:

```
// C3270_2.cpp
// compile with: /clr /c
using namespace System::Runtime::InteropServices;

[ StructLayout(LayoutKind::Sequential) ]
// try the following line instead
// [ StructLayout(LayoutKind::Explicit) ]
public value struct MYUNION
{
   [FieldOffset(0)] int a;   // C3270
   // ...
};
```
