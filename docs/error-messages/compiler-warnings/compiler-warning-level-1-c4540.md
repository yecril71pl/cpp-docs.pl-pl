---
title: Kompilator ostrzeżenie (poziom 1) C4540 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4540
dev_langs:
- C++
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e3f553bd1f910c7b17e079dc1f03664c78383e3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042770"
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