---
title: Błąd kompilatora C2679
ms.date: 11/04/2016
f1_keywords:
- C2679
helpviewer_keywords:
- C2679
ms.assetid: 1a5f9d00-9190-4aa6-bc72-949f68ec136f
ms.openlocfilehash: de5613c306eb12bc11d45e868f502ca04d0a62e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501269"
---
# <a name="compiler-error-c2679"></a>Błąd kompilatora C2679

plik binarny 'operator': znaleziono żadnego operatora, który przyjmuje prawostronny operand typu "type" (lub nie jest dopuszczalne konwersja)

Użycie operatora, możesz go przeciążenia dla określonego typu lub zdefiniuj konwersji na typ, dla którego zdefiniowano operator.

Poniższy przykład spowoduje wygenerowanie C2679:

```
// C2679.cpp
class C {
public:
   C();   // no constructor with an int argument
} c;

class D {
public:
   D(int) {}
   D(){}
} d;

int main() {
   c = 10;   // C2679
   d = 10;   // OK
}
```