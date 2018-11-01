---
title: Błąd kompilatora C3071
ms.date: 11/04/2016
f1_keywords:
- C3071
helpviewer_keywords:
- C3071
ms.assetid: 69879e66-a60e-4058-9bbd-d5c5e2d8ee37
ms.openlocfilehash: 6960dbf62fd30b822f0d7c7a3c46a29a4115913f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428356"
---
# <a name="compiler-error-c3071"></a>Błąd kompilatora C3071

operator "operator" można stosować tylko do wystąpienia klasy ref lub typu wartościowego

Nie można używać operatora CLR na typ macierzysty. Operator może służyć klasy referencyjnej lub struktury ref (typu wartości), ale nie: Typ macierzysty takie jak int lub alias dla typu macierzystego, takich jak System::Int32. Te typy nie może zostać opakowany z kodu C++ w sposób, który odwołuje się do zmiennej natywnych, więc nie można używać operatora.

Aby uzyskać więcej informacji, zobacz [Tracking Reference Operator](../../windows/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3071.

```
// C3071.cpp
// compile with: /clr
class N {};
ref struct R {};

int main() {
   N n;
   %n;   // C3071

   R r;
   R ^ r2 = %r;   // OK
}
```