---
title: "C2512 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2512
dev_langs:
- C++
helpviewer_keywords:
- C2512
ms.assetid: 15206da9-1164-451a-b869-280e00711aad
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 57dbb542eee7e893253e6c3bdd3410c605a8d2db
ms.sourcegitcommit: 8ae12a602244a5853e941e5e8806e3545d876844
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2018
---
# <a name="compiler-error-c2512"></a>C2512 błąd kompilatora

> "*identyfikator*": nie niedostępny odpowiedni konstruktor domyślny  

A *domyślnego konstruktora*, konstruktora, który wymaga bez argumentów nie jest dostępna dla określonej klasy, struktury lub związku. Kompilator udostępnia domyślny konstruktor tylko wtedy, gdy znajdują się ma konstruktorów zdefiniowanych przez użytkownika.

Jeśli podasz konstruktora, który przyjmuje parametr inny niż void, a chcesz zezwolić na klasie ma zostać utworzony bez parametrów (na przykład jako elementy tablicy), musisz także podać konstruktora domyślnego. Domyślny konstruktor może być konstruktora z wartościami domyślnymi dla wszystkich parametrów.

## <a name="example"></a>Przykład

Jest częstą przyczyną błędu C2512 podczas definiowania konstruktora klasy lub struktury, która przyjmuje argumenty, a następnie spróbujesz Zadeklaruj wystąpienie klasy lub struktury bez żadnych argumentów. Na przykład `struct B` poniżej deklaruje konstruktora, który wymaga `char *` argumentu, ale nie taki, który nie przyjmuje żadnych argumentów. W `main`, zadeklarowano wystąpienia b, ale nie podano argumentu. Kompilator generuje C2512, ponieważ nie można odnaleźć domyślnego konstruktora dla B.

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

Można rozwiązać ten problem, definiując domyślnego konstruktora dla struktury lub klasy, takich jak `B() {}`, lub konstruktora, w którym wszystkie argumenty mają przypisane wartości domyślne, takie jak `B (char * = nullptr) {}`.
