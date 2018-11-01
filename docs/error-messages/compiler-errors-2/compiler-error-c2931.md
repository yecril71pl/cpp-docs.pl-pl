---
title: Błąd kompilatora C2931
ms.date: 11/04/2016
f1_keywords:
- C2931
helpviewer_keywords:
- C2931
ms.assetid: 33430407-b149-4ba3-baf8-b0dae1ea3a5d
ms.openlocfilehash: 8fffa6e272da64ca7baa35af635b2b0a7d40c6f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661334"
---
# <a name="compiler-error-c2931"></a>Błąd kompilatora C2931

"class": typ klasy identyfikator ponownie definiowana jako funkcji składowej typu 'Identyfikator'

Nie można użyć klasy generyczny lub szablonu jako funkcję członkowską innej klasy.

Ten błąd może być spowodowany nawiasy klamrowe są nieprawidłowo dopasowywane.

Poniższy przykład spowoduje wygenerowanie C2931:

```
// C2931.cpp
// compile with: /c
template<class T>
struct TC { };
struct MyStruct {
   void TC<int>();   // C2931
};

struct TC2 { };
struct MyStruct2 {
   void TC2();
};
```

C2931 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C2931b.cpp
// compile with: /clr /c
generic<class T> ref struct GC {};
struct MyStruct {
   void GC<int>();   // C2931
   void GC2();   // OK
};
```