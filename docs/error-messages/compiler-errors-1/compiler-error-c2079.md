---
title: Błąd kompilatora C2079 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2079
dev_langs:
- C++
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ddea9a8651a62f7cbb857e1d53962142471c2cb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032188"
---
# <a name="compiler-error-c2079"></a>Błąd kompilatora C2079

'Identyfikator' używa Niezdefiniowana klasa/struct/union "name"

Określony identyfikator jest niezdefiniowany klasy, struktury lub Unii.

Ten błąd może być spowodowany przez inicjowanie anonimowej Unii.

Poniższy przykład spowoduje wygenerowanie C2079:

```
// C2079.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   std::ifstream g;   // C2079
}
```

Możliwe rozwiązanie:

```
// C2079b.cpp
// compile with: /EHsc
#include <fstream>
int main( ) {
   std::ifstream g;
}
```

C2079 może również wystąpić, jeśli użytkownik podejmie próbę zadeklarować obiekt na stosie typu, w których deklaracją do przodu, który znajduje się tylko w zakresie.

```
// C2079c.cpp
class A;

class B {
   A a;   // C2079
};

class A {};
```

Możliwe rozwiązanie:

```
// C2079d.cpp
// compile with: /c
class A;
class C {};

class B {
   A * a;
   C c;
};

class A {};
```