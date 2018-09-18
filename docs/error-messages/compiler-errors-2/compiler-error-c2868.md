---
title: Błąd kompilatora C2868 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2868
dev_langs:
- C++
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2de22b34f9dc564ef89d7776af86718af70d51eb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037869"
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