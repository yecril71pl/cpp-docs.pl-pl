---
title: Błąd kompilatora C3284
ms.date: 11/04/2016
f1_keywords:
- C3284
helpviewer_keywords:
- C3284
ms.assetid: e582f316-e9db-4d27-9c70-fdfa737a9d5f
ms.openlocfilehash: 9606ff5916e4c6971ec44a9d277bb980701ed169
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757556"
---
# <a name="compiler-error-c3284"></a>Błąd kompilatora C3284

ograniczenia dla parametru generycznego "Function" funkcji muszą być zgodne z ograniczeniami dla parametru generycznego "parameter" funkcji "Function"

Wirtualna funkcja ogólna musi używać tych samych ograniczeń co funkcja wirtualna o tej samej nazwie i zestawie argumentów w klasie bazowej.

Poniższy przykład generuje C3284:

```cpp
// C3284.cpp
// compile with: /clr /c
// C3284 expected
public interface class IGettable {
   int Get();
};

public interface class B {
   generic<typename T>
   where T : IGettable
   virtual int mf(T t);
};

public ref class D : public B {
public:
   generic<typename T>
   // Uncomment the following line to resolve.
   // where T : IGettable
   virtual int mf(T t) {
      return 4;
   }
};
```
