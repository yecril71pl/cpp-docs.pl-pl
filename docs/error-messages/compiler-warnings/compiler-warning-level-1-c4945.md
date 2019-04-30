---
title: Kompilator ostrzeżenie (poziom 1) C4945
ms.date: 11/04/2016
f1_keywords:
- C4945
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
ms.openlocfilehash: 62dfbaed28f1afcdedb41d83158dfe4e8e0f61b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384169"
---
# <a name="compiler-warning-level-1-c4945"></a>Kompilator ostrzeżenie (poziom 1) C4945

'symbol': nie można zaimportować symbolu z "assembly2": ponieważ "symbol" został już zaimportowany z innego zestawu "assembly1"

Symbol został zaimportowany z przywoływanym zestawie, ale tego symbolu został już zaimportowany z innego zestawu odwołania. Nie odwoływać się do jednego z zestawów lub uzyskać nazwę symbolu zmienione w jednym z zestawów.

Poniższe przykłady Generowanie C4945.

```
// C4945a.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

Następnie wyszukaj maszynę

```
// C4945b.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

Następnie wyszukaj maszynę

```
// C4945c.cpp
// compile with: /clr /LD /W1
#using "C4945a.dll"
#using "C4945b.dll"   // C4945
```