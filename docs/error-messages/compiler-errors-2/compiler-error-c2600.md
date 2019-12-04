---
title: Błąd kompilatora C2600
ms.date: 11/04/2016
f1_keywords:
- C2600
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
ms.openlocfilehash: b2d95460cadf03f9152599ef47ae703030326dd1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740744"
---
# <a name="compiler-error-c2600"></a>Błąd kompilatora C2600

"Function": nie można zdefiniować wygenerowanej przez kompilator specjalnej funkcji składowej (musi być najpierw zadeklarowana w klasie)

Zanim funkcje członkowskie, takie jak konstruktory lub destruktory, można zdefiniować dla klasy, muszą one być zadeklarowane w klasie. Kompilator może generować domyślne konstruktory i destruktory (o nazwie specjalne funkcje członkowskie), jeśli żadna z nich nie jest zadeklarowana w klasie. Jeśli jednak zdefiniujesz jedną z tych funkcji bez zgodnej deklaracji w klasie, kompilator wykryje konflikt.

Aby naprawić ten błąd, w deklaracji klasy Zadeklaruj każdą funkcję członkowską, która została zdefiniowana poza deklaracją klasy.

Poniższy przykład generuje C2600:

```cpp
// C2600.cpp
// compile with: /c
class C {};
C::~C() {}   // C2600

class D {
   D::~D();
};

D::~D() {}
```
