---
title: Błąd kompilatora C2512
ms.date: 02/09/2018
f1_keywords:
- C2512
helpviewer_keywords:
- C2512
ms.assetid: 15206da9-1164-451a-b869-280e00711aad
ms.openlocfilehash: 16a1da0e882cd178c9e01737480d74eb23c7c38c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164829"
---
# <a name="compiler-error-c2512"></a>Błąd kompilatora C2512

> "*identyfikator*": nie niedostępny odpowiedni konstruktor domyślny

A *domyślnego konstruktora*, Konstruktor, który wymaga żadnych argumentów, nie jest dostępna dla określonej klasy, struktury lub Unii. Tylko wtedy, gdy znajdują się zdefiniowane przez użytkownika konstruktorów, kompilator dostarcza Konstruktor domyślny.

Jeśli podasz konstruktora, który przyjmuje parametr niż void, a chcesz zezwolić na klasy do utworzenia bez parametrów (na przykład, jako elementów tablicy), należy również podać domyślnego konstruktora. Konstruktor domyślny może być konstruktorem z wartościami domyślnymi dla wszystkich parametrów.

## <a name="example"></a>Przykład

Częstą przyczyną błędu C2512 jest podczas definiowania konstruktora klasy lub struktury, która przyjmuje argumenty, a następnie spróbujesz deklarować wystąpienia klasy lub struktury, bez żadnych argumentów. Na przykład `struct B` poniżej deklaruje Konstruktor, który wymaga `char *` argumentów, ale nie jedna, która nie przyjmuje żadnych argumentów. W `main`, wystąpienie B jest zadeklarowana, ale nie zostaną dostarczone argumenty. Kompilator generuje C2512, ponieważ nie można odnaleźć domyślnego konstruktora dla B.

```cpp
// C2512.cpp
// Compile with: cl /W4 c2512.cpp
// C2512 expected
struct B {
   B (char *) {}
   // Uncomment the following line to fix.
   // B() {}
};

int main() {
   B b;   // C2512 - This requires a default constructor
}
```

Możesz rozwiązać ten problem, definiując domyślnego konstruktora dla klasy lub struktury, takich jak `B() {}`, lub konstruktora, w którym wszystkie argumenty mają przypisane wartości domyślne, takie jak `B (char * = nullptr) {}`.
