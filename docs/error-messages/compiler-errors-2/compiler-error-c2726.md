---
title: Błąd kompilatora C2726
ms.date: 11/04/2016
f1_keywords:
- C2726
helpviewer_keywords:
- C2726
ms.assetid: f0191bb7-c175-450b-bf09-a3213db96d09
ms.openlocfilehash: d0ade9317c996bb3432e7a4626fc930a3d5df349
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208392"
---
# <a name="compiler-error-c2726"></a>Błąd kompilatora C2726

"gcnew" można używać tylko do utworzenia obiektu z zarządzanego lub typu WinRT

Nie można utworzyć wystąpienia typu natywnego w stosie zebranych elementów bezużytecznych.

Poniższy przykład generuje C2726 i pokazuje, jak go naprawić:

```
// C2726.cpp
// compile with: /clr
using namespace System;
class U {};
ref class V {};
value class W {};

int main() {
   U* pU = gcnew U;    // C2726
   U* pU2 = new U;   // OK
   V^ p2 = gcnew V;   // OK
   W p3;   // OK

}
```
