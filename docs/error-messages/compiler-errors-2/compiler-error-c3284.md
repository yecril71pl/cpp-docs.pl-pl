---
title: Błąd kompilatora C3284
ms.date: 11/04/2016
f1_keywords:
- C3824
helpviewer_keywords:
- C3284
ms.assetid: e582f316-e9db-4d27-9c70-fdfa737a9d5f
ms.openlocfilehash: 6e79de18e277de9ee79945d319640fa906dea622
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511634"
---
# <a name="compiler-error-c3284"></a>Błąd kompilatora C3284

ograniczenia dla parametru ogólnego "parametru" funkcji "function" musi być zgodne z ograniczeniami dla parametru ogólnego "parametru" funkcji "function"

Ogólna funkcja wirtualna musi używać tych samych ograniczeń co funkcja wirtualna o tej samej nazwie i zestawu argumentów w klasie bazowej.

Poniższy przykład spowoduje wygenerowanie C3284:

```
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