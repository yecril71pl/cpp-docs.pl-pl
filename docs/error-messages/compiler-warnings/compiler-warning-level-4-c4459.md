---
title: Kompilator ostrzeżenie (poziom 4) C4459
ms.date: 11/04/2016
f1_keywords:
- C4459
helpviewer_keywords:
- C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
ms.openlocfilehash: 0cbab7c7cca1fc88bb99210262be45c56b6be7a8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585071"
---
# <a name="compiler-warning-level-4-c4459"></a>Kompilator ostrzeżenie (poziom 4) C4459

> Deklaracja "*identyfikator*" powoduje ukrycie deklaracji globalnej

Deklaracja *identyfikator* w zakresie lokalnym ukrywa deklarację o takiej samej nazwie *identyfikator* w zakresie globalnym. To ostrzeżenie informuje o tym, który odwołuje się do *identyfikator* w tym zakresie rozpoznać lokalnie zadeklarowanych wersji, a nie wersja globalna, która może być lub może nie być zgodne z zamiarami użytkownika. Ogólnie rzecz biorąc zalecamy zminimalizować użycie zmiennych globalnych jako dobrą praktykę. Aby zminimalizować zanieczyszczeniu globalnej przestrzeni nazw, firma Microsoft zaleca korzystanie z nazwanego przestrzeni nazw dla zmiennych globalnych.

To ostrzeżenie jest nowe w programie Visual Studio 2015 w programie Visual C++ wersja kompilatora godziny 18.00. Aby pominąć ostrzeżenia z danej wersji kompilatora lub później, podczas migracji kodu, należy użyć [/WV: 18](../../build/reference/compiler-option-warning-level.md) — opcja kompilatora.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4459:

```cpp
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() {
    int global_or_local; // warning C4459
    global_or_local = 2;
}
```

Jednym ze sposobów, aby rozwiązać ten problem jest utworzenia przestrzeni nazw usługi globalne, ale używa `using` dyrektywy do przenoszą tej przestrzeni nazw do zakresu, dzięki czemu wszystkie odwołania musi używać jednoznaczną kwalifikowane nazwy:

```cpp
// C4459_namespace.cpp
// compile with: cl /W4 /EHsc C4459_namespace.cpp
namespace globals {
    int global_or_local = 1;
}

int main() {
    int global_or_local; // OK
    global_or_local = 2;
    globals::global_or_local = 3;
}
```
