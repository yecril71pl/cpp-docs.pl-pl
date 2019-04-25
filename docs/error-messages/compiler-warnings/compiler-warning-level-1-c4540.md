---
title: Kompilator ostrzeżenie (poziom 1) C4540
ms.date: 11/04/2016
f1_keywords:
- C4540
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
ms.openlocfilehash: 86f6cd866f7708277ebba436ba7c076086dc9c8c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160708"
---
# <a name="compiler-warning-level-1-c4540"></a>Kompilator ostrzeżenie (poziom 1) C4540

dynamic_cast użyty do konwertowania do niedostępnej lub niejednoznacznej podstawy; czasu wykonywania, test zakończy się niepowodzeniem ('Typ1' na 'Typ2')

Możesz użyć `dynamic_cast` do konwertowania z jednego typu na inny. Kompilator ustalić, czy rzutowanie będzie zawsze kończy się niepowodzeniem (zwracają **NULL**), ponieważ klasa bazowa jest niedostępna (`private`, na przykład) lub niejednoznaczny (występuje więcej niż raz w hierarchii klas dla wystąpienia).

Poniżej przedstawiono przykład to ostrzeżenie. Klasa **B** pochodzi od klasy **A**. Program używa `dynamic_cast` rzutować z klasy **B** (klasy pochodnej) do klasy **A**, które będą zawsze się niepowodzeniem, ponieważ klasy **B** jest `private` i w związku z tym niedostępne. Zmienianie dostępu z **A** do **publicznych** rozwiąże to ostrzeżenie.

```
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