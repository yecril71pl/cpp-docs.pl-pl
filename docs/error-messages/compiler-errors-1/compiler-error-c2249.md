---
title: Błąd kompilatora C2249 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2249
dev_langs:
- C++
helpviewer_keywords:
- C2249
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb9c73ca311b767d9fdb50dd55a832cf8fcc2a4b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089895"
---
# <a name="compiler-error-c2249"></a>Błąd kompilatora C2249

"członek": Brak dostępnej ścieżki, uzyskania dostępu do składowej zadeklarowanej w wirtualnej podstawowej "class"

`member` Jest dziedziczony z nonpublic `virtual` klasy bazowej lub struktury.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2249.

```
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

## <a name="example"></a>Przykład

C2249 może również wystąpić, jeśli użytkownik próbuje przypisać strumień od standardowej biblioteki języka C++ do innego strumienia.  Poniższy przykład spowoduje wygenerowanie C2249.

```
// C2249_2.cpp
#include <iostream>
using namespace std;
int main() {
   cout = cerr;   // C2249
   #define cout cerr;   // OK
}
```