---
title: Ostrzeżenie (poziomy 2 i 4) kompilatora — od C4200 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4200
dev_langs:
- C++
helpviewer_keywords:
- C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 34e0befb93db742bb2d132b2092414a1a167b87b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100724"
---
# <a name="compiler-warning-levels-2-and-4-c4200"></a>Ostrzeżenie (poziomy 2 i 4) kompilatora — od C4200

użyto niestandardowego rozszerzenia: tablica o rozmiarze zero w struct/union

Wskazuje, że struktura lub Unia zawiera tablicę o rozmiarze zero.

Deklaracja tablicy o rozmiarze zero jest rozszerzeniem firmy Microsoft. To powoduje, że ostrzeżenia poziomu 2, gdy plik C++ jest kompilowany i ostrzeżenia poziomu 4 podczas kompilowania pliku C. Kompilacji języka C++ udostępnia też to ostrzeżenie: "Nie można wygenerować operatora domyślnego elementu ctor kopiowania lub przypisania kopiowania po UDT zawiera zerowy rozmiar tablicy." Ten przykład generuje ostrzeżenie — od C4200:

```cpp
// C4200.cpp
// compile by using: cl /W4 c4200.cpp
struct A {
    int a[0];  // C4200
};
int main() {
}
```

To rozszerzenie niestandardowe jest często używane do kodu interfejsu ze strukturami danych zewnętrznych, które mają o zmiennej długości. Jeśli ten scenariusz ma zastosowanie do kodu, możesz wyłączyć to ostrzeżenie:

## <a name="example"></a>Przykład

```cpp
// C4200b.cpp
// compile by using: cl /W4 c4200a.cpp
#pragma warning(disable : 4200)
struct A {
    int a[0];
};
int main() {
}
```