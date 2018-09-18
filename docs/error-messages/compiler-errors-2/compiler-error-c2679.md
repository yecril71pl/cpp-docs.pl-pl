---
title: Błąd kompilatora C2679 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2679
dev_langs:
- C++
helpviewer_keywords:
- C2679
ms.assetid: 1a5f9d00-9190-4aa6-bc72-949f68ec136f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a01a79dfdff06c50b65bde33de62676e6df64a82
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069498"
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