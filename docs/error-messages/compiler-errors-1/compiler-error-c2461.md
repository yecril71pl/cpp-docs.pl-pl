---
title: Błąd kompilatora C2461
ms.date: 11/04/2016
f1_keywords:
- C2461
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
ms.openlocfilehash: e8f82ed4ce8ad77a22961a42c8e9a256e6f647db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535138"
---
# <a name="compiler-error-c2461"></a>Błąd kompilatora C2461

> "*klasy*": składni konstruktora brakuje parametrów formalnych

Konstruktor dla klasy nie określono żadnych parametrów formalnych. Deklaracja konstruktora, należy określić formalnej listy parametrów. Lista może być pusta.

Aby rozwiązać ten problem, Dodaj parę nawiasów po zadeklarowaniu *klasy*:: **klasy*.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak naprawić C2461:

```cpp
// C2461.cpp
// compile with: /c
class C {
   C::C;     // C2461
   C::C();   // OK
};
```