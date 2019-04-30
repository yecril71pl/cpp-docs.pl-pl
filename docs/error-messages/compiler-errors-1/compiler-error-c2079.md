---
title: Błąd kompilatora C2079
ms.date: 11/04/2016
f1_keywords:
- C2079
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
ms.openlocfilehash: 68435610680e3b21415a1d9439a8133fd1e2557f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391962"
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