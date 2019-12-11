---
title: Ostrzeżenie kompilatora (poziom 3) C4570
ms.date: 11/04/2016
f1_keywords:
- C4570
helpviewer_keywords:
- C4570
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
ms.openlocfilehash: 13767cdbd34c72953568181c15ad33119bf5179a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991931"
---
# <a name="compiler-warning-level-3-c4570"></a>Ostrzeżenie kompilatora (poziom 3) C4570

"Type": nie jest jawnie zadeklarowany jako abstrakcyjny, ale ma funkcje abstrakcyjne

Typ, który zawiera funkcje [abstrakcyjne](../../extensions/abstract-cpp-component-extensions.md) , powinien być oznaczony jako abstrakcyjny.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4570.

```cpp
// C4570.cpp
// compile with: /clr /W3 /c
ref struct X {   // C4570
// try the following line instead
// ref class X abstract {
   virtual void f() abstract;
};
```
