---
title: Kompilator ostrzeżenie (poziom 1) C4945 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4945
dev_langs:
- C++
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 48797667c880bcd441065da3651adabdb955b52b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027521"
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