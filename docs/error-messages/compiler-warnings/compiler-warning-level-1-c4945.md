---
title: Ostrzeżenie kompilatora (poziom 1) C4945
ms.date: 11/04/2016
f1_keywords:
- C4945
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
ms.openlocfilehash: 15a78877dbe70a7f95674092984546219e6a1c78
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199128"
---
# <a name="compiler-warning-level-1-c4945"></a>Ostrzeżenie kompilatora (poziom 1) C4945

"symbol": nie można zaimportować symbolu z "Assembly2": ponieważ "symbol" został już zaimportowany z innego zestawu "assembly1"

Symbol został zaimportowany z przywoływanego zestawu, ale ten symbol został już zaimportowany z innego zestawu, do którego się odwołuje. Nie należy odwoływać się do jednego z zestawów lub uzyskać zmiany nazwy symbolu w jednym z zestawów.

Poniższe przykłady generują C4945.

```csharp
// C4945a.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

a następnie

```csharp
// C4945b.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

a następnie

```cpp
// C4945c.cpp
// compile with: /clr /LD /W1
#using "C4945a.dll"
#using "C4945b.dll"   // C4945
```
