---
title: Błąd kompilatora C2937
ms.date: 11/04/2016
f1_keywords:
- C2937
helpviewer_keywords:
- C2937
ms.assetid: 95671ca3-79f7-4b56-a5f2-a92296da1629
ms.openlocfilehash: f682cd6346d214f4173226d78301f563083ef607
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758375"
---
# <a name="compiler-error-c2937"></a>Błąd kompilatora C2937

"Class": Identyfikator klasy typu został ponownie zdefiniowany jako globalny element typedef

Nie można użyć klasy generycznej ani szablonu jako globalnego `typedef`.

Poniższy przykład generuje C2937:

```cpp
// C2937.cpp
// compile with: /c
template<class T>
struct TC { };
typedef int TC<int>;   // C2937
typedef TC<int> c;   // OK
```

C2937 może również wystąpić przy użyciu typów ogólnych:

```cpp
// C2937b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };
typedef int GC<int>;   // C2937
typedef GC<int> xx;   // OK
```
