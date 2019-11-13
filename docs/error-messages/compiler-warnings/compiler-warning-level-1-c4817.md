---
title: Ostrzeżenie kompilatora (poziom 1) C4817
ms.date: 11/04/2016
f1_keywords:
- C4817
helpviewer_keywords:
- C4817
ms.assetid: a68f5486-6940-4934-9f93-bfd4d71f92a9
ms.openlocfilehash: d729bdbf0f8379b2ffde80567ae4307d0a8dacd7
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052327"
---
# <a name="compiler-warning-level-1-c4817"></a>Ostrzeżenie kompilatora (poziom 1) C4817

"member": niedozwolone użycie "." w celu uzyskania dostępu do tego elementu członkowskiego; Kompilator zamieniono na "->"

Użyto nieprawidłowego operatora dostępu do elementu członkowskiego.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4817.

```cpp
// C4817.cpp
// compile with: /clr /W1
using namespace System;
int main() {
   array<Int32> ^ a = gcnew array<Int32>(100);
   Console::WriteLine( a.Length );   // C4817
   Console::WriteLine( a->Length );   // OK
}
```
