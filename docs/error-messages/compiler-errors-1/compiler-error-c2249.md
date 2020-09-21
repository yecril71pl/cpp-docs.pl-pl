---
title: Błąd kompilatora C2249
ms.date: 11/04/2016
f1_keywords:
- C2249
helpviewer_keywords:
- C2249
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
ms.openlocfilehash: ac396fe5fa3505311f5a45ebb49dae283e35248c
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741420"
---
# <a name="compiler-error-c2249"></a>Błąd kompilatora C2249

"member": brak dostępnej ścieżki umożliwiającej dostęp do składowej zadeklarowanej w wirtualnej podstawowej "Class"

`member`Jest dziedziczona z niepublicznej **`virtual`** klasy podstawowej lub struktury.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C2249.

```cpp
// C2249.cpp
class A {
private:
   void privFunc( void ) {};
public:
   void pubFunc( void ) {};
};

class B : virtual public A {} b;

int main() {
   b.privFunc();    // C2249, private member of A
   b.pubFunc();    // OK
}
```

C2249 może również wystąpić, jeśli próbujesz przypisać strumień z standardowej biblioteki języka C++ do innego strumienia.  Poniższy przykład generuje C2249.

```cpp
// C2249_2.cpp
#include <iostream>
using namespace std;
int main() {
   cout = cerr;   // C2249
   #define cout cerr;   // OK
}
```
