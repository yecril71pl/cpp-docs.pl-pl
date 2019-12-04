---
title: Błąd kompilatora C2364
ms.date: 11/04/2016
f1_keywords:
- C2364
helpviewer_keywords:
- C2364
ms.assetid: 4f550571-94b5-42ca-84cb-663fecbead44
ms.openlocfilehash: fb019d729bc100296742b15ba95460fe0e404673
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759883"
---
# <a name="compiler-error-c2364"></a>Błąd kompilatora C2364

"Type": niedozwolony typ dla atrybutu niestandardowego

Argumenty nazwane dla atrybutów niestandardowych są ograniczone do czasu kompilacji. Na przykład typy całkowite (int, char itp.), system:: Type ^ i system:: Object ^.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2364.

```cpp
// c2364.cpp
// compile with: /clr /c
using namespace System;

[attribute(AttributeTargets::All)]
public ref struct ABC {
public:
   // Delete the following line to resolve.
   ABC( Enum^ ) {}   // C2364
   ABC( int ) {}   // OK
};
```
