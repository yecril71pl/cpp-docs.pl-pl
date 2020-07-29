---
title: Ostrzeżenie kompilatora (poziom 1) C4540
ms.date: 11/04/2016
f1_keywords:
- C4540
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
ms.openlocfilehash: 13935e7eebdf3e7b7e89fad8c55d410cf2788e4d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230652"
---
# <a name="compiler-warning-level-1-c4540"></a>Ostrzeżenie kompilatora (poziom 1) C4540

dynamic_cast używany do konwersji na niedostępną lub niejednoznaczną podstawę; test czasu wykonywania zakończy się niepowodzeniem ("type1" na "type2")

Użyto **`dynamic_cast`** do konwersji z jednego typu na drugi. Kompilator ustalił, że rzutowanie będzie zawsze kończyć się niepowodzeniem (zwraca **wartość null**), ponieważ klasa bazowa jest niedostępna ( **`private`** na przykład) lub niejednoznaczna (występuje więcej niż raz w hierarchii klasy, na przykład).

Poniżej przedstawiono przykład tego ostrzeżenia. Klasa **B** jest pochodną klasy **A**. Program używa **`dynamic_cast`** do rzutowania z klasy **b** (klasy pochodnej) do klasy **A**, która zawsze zakończy się niepowodzeniem, ponieważ Klasa **B** jest **`private`** i w związku z tym jest niedostępna. Zmiana dostępu do **elementu** na **`public`** spowoduje rozwiązanie tego ostrzeżenia.

```cpp
// C4540.cpp
// compile with: /W1

struct A {
   virtual void g() {}
};

struct B : private A {
   virtual void g() {}
};

int main() {
   B b;
   A * ap = dynamic_cast<A*>(&b);   // C4540
}
```
