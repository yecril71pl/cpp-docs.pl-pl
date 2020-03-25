---
title: Błąd kompilatora C2461
ms.date: 11/04/2016
f1_keywords:
- C2461
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
ms.openlocfilehash: 3d290bd2288f76d0ddefa2057e3e01c9edc3cbc7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205325"
---
# <a name="compiler-error-c2461"></a>Błąd kompilatora C2461

> "*Class*": w składni konstruktora brakuje parametrów formalnych

Konstruktor dla klasy nie określa żadnych formalnych parametrów. Deklaracja konstruktora musi określać formalną listę parametrów. Lista może być pusta.

Aby rozwiązać ten problem, Dodaj parę nawiasów po deklaracji *klasy* *::*.*

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
