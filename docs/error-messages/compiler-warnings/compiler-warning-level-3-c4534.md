---
title: Kompilator ostrzeżenie (poziom 3) C4534 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- c4534
dev_langs:
- C++
helpviewer_keywords:
- C4534
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad85a6b9dff1715cbdce9738608f26c8680319d0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099814"
---
# <a name="compiler-warning-level-3-c4534"></a>Kompilator ostrzeżenie (poziom 3) C4534

"Konstruktor" nie będzie konstruktorem domyślnym dla klasy "class" z powodu argumentu domyślnego

Niezarządzane klasa może mieć konstruktora z parametrami, które mają przypisane wartości domyślne, a kompilator zostanie ona użyta jako domyślnego konstruktora. Klasa jest oznaczona za pomocą `value` — słowo kluczowe nie będzie używać konstruktora przy użyciu wartości domyślnych dla jego parametrów jako domyślnego konstruktora.

Aby uzyskać więcej informacji, zobacz [klas i struktur](../../windows/classes-and-structs-cpp-component-extensions.md).

Poniższy przykład spowoduje wygenerowanie C4534:

```
// C4534.cpp
// compile with: /W3 /clr /WX
value class MyClass {
public:
   int ii;
   MyClass(int i = 9) {   // C4534, will not be the default constructor
      i++;
   }
};

int main() {
   MyClass ^ xx = gcnew MyClass;
   xx->ii = 0;
}
```