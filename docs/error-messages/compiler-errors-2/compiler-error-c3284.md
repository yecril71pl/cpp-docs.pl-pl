---
title: Compiler Error C3284
ms.date: 11/04/2016
f1_keywords:
- C3284
helpviewer_keywords:
- C3284
ms.assetid: e582f316-e9db-4d27-9c70-fdfa737a9d5f
ms.openlocfilehash: acefcac849b9ce36bcf24d45f3ce85ba220b3698
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381374"
---
# <a name="compiler-error-c3284"></a>Compiler Error C3284

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