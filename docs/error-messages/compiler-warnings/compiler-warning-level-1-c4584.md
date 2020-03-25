---
title: Ostrzeżenie kompilatora (poziom 1) C4584
ms.date: 11/04/2016
f1_keywords:
- C4584
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
ms.openlocfilehash: fa736e8dbab775fcd6cdffc467aee1312004fa60
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162156"
---
# <a name="compiler-warning-level-1-c4584"></a>Ostrzeżenie kompilatora (poziom 1) C4584

"Class1": Klasa bazowa "'klasa" jest już klasą bazową "class3"

Zdefiniowana Klasa dziedziczy z dwóch klas, z których jedna dziedziczy po drugiej. Na przykład:

```cpp
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

W takim przypadku ostrzeżenie powinno zostać wystawione w klasie C, ponieważ dziedziczy zarówno z klasy A, jak i klasy B, która dziedziczy również z klasy A. To ostrzeżenie służy jako przypomnienie, że należy w pełni zakwalifikować się do użycia elementów członkowskich z tych klas podstawowych lub błąd kompilatora zostanie wygenerowany ze względu na niejednoznaczność, do której odwołuje się członek klasy.
