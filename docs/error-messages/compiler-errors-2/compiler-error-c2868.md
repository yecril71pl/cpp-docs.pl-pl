---
title: Błąd kompilatora C2868
ms.date: 11/04/2016
f1_keywords:
- C2868
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
ms.openlocfilehash: 4cb259ed0f43831226fb7e1a1ccf7b28bcef7819
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614776"
---
# <a name="compiler-error-c2868"></a>Błąd kompilatora C2868

> "*identyfikator*": Niedozwolona składnia dla deklaracji using; Oczekiwano kwalifikowanej nazwy

A [użycie — deklaracja](../../cpp/using-declaration.md) wymaga *kwalifikowana nazwa*, operatora zakresu (`::`) oddzielone sekwencji nazw przestrzeni nazw, klasy lub wyliczenia, która kończy się nazwa identyfikatora. Operator rozpoznawania pojedynczy zakres może służyć do wprowadzić nazwę z globalnej przestrzeni nazw.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2868 oraz pokazuje poprawne użycie:

```cpp
// C2868.cpp
class X {
public:
   int i;
};

class Y : X {
public:
   using X::i;   // OK
};

int main() {
   using X;   // C2868
}
```