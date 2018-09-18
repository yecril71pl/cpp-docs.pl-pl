---
title: Kompilator ostrzeżenie (poziom 1) C4669 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4669
dev_langs:
- C++
helpviewer_keywords:
- C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f96bcf40b1fbc989daceabc810d019d1bb9aa98
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060863"
---
# <a name="compiler-warning-level-1-c4669"></a>Kompilator ostrzeżenie (poziom 1) C4669

Instrukcja "cast": niebezpieczna konwersja: "class" to zarządzana lub obiekt typu WinRT

Rzutowanie zawiera Windows Runtime lub typ zarządzany. Kompilator wykonuje rzutowanie, wykonując kopię operacja jeden wskaźnik do innego, ale zapewnia, żadne inne sprawdzanie. Aby rozwiązać tego ostrzeżenia, nie Rzutuj klasy zawierające zarządzanych członków lub typów środowiska wykonawczego Windows.

Poniższy przykład generuje C4669 i pokazuje, jak go naprawić:

```
// C4669.cpp
// compile with: /clr /W1
ref struct A {
   int i;
   Object ^ pObj;   // remove the managed member to fix the warning
};

ref struct B {
   int j;
};

int main() {
   A ^ a = gcnew A;
   B ^ b = reinterpret_cast<B ^>(a);   // C4669
}
```