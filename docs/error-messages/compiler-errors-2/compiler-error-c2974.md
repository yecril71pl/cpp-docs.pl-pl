---
title: Błąd kompilatora C2974 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2974
dev_langs:
- C++
helpviewer_keywords:
- C2974
ms.assetid: 1b444260-f2bf-48d7-ab1e-35573d8c4a0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 478639ee1eccf841361e8e7e880ac33669d69e1e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100489"
---
# <a name="compiler-error-c2974"></a>Błąd kompilatora C2974

Nieprawidłowy typ argumentu "number", typ oczekiwany

Argument generyczny lub szablonu jest niezgodna z deklaracją generyczny lub szablonu. Typ powinny być wyświetlane w nawiasach kątowych. Sprawdź definicję generyczny lub szablonu, aby znaleźć poprawne typy.

Poniższy przykład spowoduje wygenerowanie C2974:

```
// C2974.cpp
// C2974 expected
template <class T>
struct TC {};

template <typename T>
void tf(T){}

int main() {
   // Delete the following 2 lines to resolve
   TC<1>* tc;
   tf<"abc">("abc");

   TC<int>* tc;
   tf<const char *>("abc");
}
```

C2974 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C2974b.cpp
// compile with: /clr
// C2974 expected
using namespace System;
generic <class T>
ref struct GCtype {};

generic <typename T>
void gf(T){}

int main() {
   // Delete the following 2 lines to resolve
   GCtype<"a">^ gc;
   gf<"a">("abc");

   // OK
   GCtype<int>^ gc;
   gf<String ^>("abc");
}
```