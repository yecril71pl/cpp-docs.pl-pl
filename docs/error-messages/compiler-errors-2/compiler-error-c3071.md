---
title: Błąd kompilatora C3071 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3071
dev_langs:
- C++
helpviewer_keywords:
- C3071
ms.assetid: 69879e66-a60e-4058-9bbd-d5c5e2d8ee37
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f004de3ed133ea77d543014ae1adcdc4e1eddef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077805"
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