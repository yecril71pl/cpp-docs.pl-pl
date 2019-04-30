---
title: Błąd kompilatora C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: 2b76fa91d739e9cc89251aaf56aa9b196e62a68d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406733"
---
# <a name="compiler-error-c3072"></a>Błąd kompilatora C3072

Nie można zastosować operatora "operator" do wystąpienia klasy ref

Użyj jednoargumentowego "`operator` " operator do konwertowania wystąpienia klasy ref dla typu uchwytu

Typ CLR wymaga operatorów CLR, nie Operatorzy lokalny (lub standardowa).  Aby uzyskać więcej informacji, zobacz [Tracking Reference Operator](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3072.

```
// C3072.cpp
// compile with: /clr
ref class R {};

int main() {
   R r1;
   R^ r2 = &r1;   // C3072
   R^ r3 = %r1;   // OK
}
```