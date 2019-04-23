---
title: Kompilator ostrzeżenie (poziom 3) C4570
ms.date: 11/04/2016
f1_keywords:
- C4570
helpviewer_keywords:
- C4570
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
ms.openlocfilehash: 386d7c210c77469d67a75d66f7d8ae35c105b3b0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777916"
---
# <a name="compiler-warning-level-3-c4570"></a>Kompilator ostrzeżenie (poziom 3) C4570

"type": nie jest jawnie zadeklarowana jako abstrakcyjna, ale ma funkcje abstrakcyjne

Typ, który zawiera [abstrakcyjne](../../extensions/abstract-cpp-component-extensions.md) funkcje powinien się być oznaczony jako abstrakcyjny.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4570.

```
// C4570.cpp
// compile with: /clr /W3 /c
ref struct X {   // C4570
// try the following line instead
// ref class X abstract {
   virtual void f() abstract;
};
```