---
title: Błąd narzędzi konsolidatora LNK2020
ms.date: 11/04/2016
f1_keywords:
- LNK2020
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
ms.openlocfilehash: 7290a90dfd92d84c4632e7f9dd38d36eccd4ac27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499859"
---
# <a name="linker-tools-error-lnk2020"></a>Błąd narzędzi konsolidatora LNK2020

Nierozpoznany token 'token'

Podobnie jak Wystąpił niezdefiniowany błąd zewnętrzny, z tą różnicą, że odwołanie jest za pomocą metadanych. W metadanych muszą być zdefiniowane wszystkie funkcje i dane.

Aby rozwiązać problem:

- Zdefiniuj Brak funkcję lub dane, lub

- W tym pliku obiektu biblioteki, w którym brakuje funkcję lub dane jest już zdefiniowany.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie LNK2020.

```
// LNK2020.cpp
// compile with: /clr /LD
ref struct A {
   A(int x);   // LNK2020
   static int f();   // LNK2020
};

// OK
ref struct B {
   B(int x) {}
   static int f() { return 0; }
};
```

## <a name="example"></a>Przykład

LNK2020 również wystąpi utworzyć zmienną typu zarządzanego szablonu, ale również tworzy wystąpienia typu.

Poniższy przykład spowoduje wygenerowanie LNK2020.

```
// LNK2020_b.cpp
// compile with: /clr

template <typename T>
ref struct Base {
   virtual void f1() {};
};

template <typename T>
ref struct Base2 {
   virtual void f1() {};
};

int main() {
   Base<int>^ p;   // LNK2020
   Base2<int>^ p2 = gcnew Base2<int>();   // OK
};
```