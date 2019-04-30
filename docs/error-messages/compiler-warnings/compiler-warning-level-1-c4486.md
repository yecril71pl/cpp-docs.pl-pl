---
title: Kompilator ostrzeżenie (poziom 1) C4486
ms.date: 11/04/2016
f1_keywords:
- C4486
helpviewer_keywords:
- C4486
ms.assetid: 2c0c59e3-d025-4d97-8da2-fa27df1402fc
ms.openlocfilehash: 402d5eefde6c2dfd5693e53c27edb00d1ac2e56c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404068"
---
# <a name="compiler-warning-level-1-c4486"></a>Kompilator ostrzeżenie (poziom 1) C4486

'Funkcja': prywatna metoda wirtualna klasy referencyjnej lub klasy wartości powinna być oznaczona jako "sealed"

Ponieważ prywatna wirtualna funkcja składowa klasy zarządzanej lub struktury, nie można uzyskać dostępu do lub zastąpić, powinien być oznaczony [zapieczętowanego](../../extensions/sealed-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4486.

```
// C4486.cpp
// compile with: /clr /c /W1
ref class B {
private:
   virtual void f() {}   // C4486
   virtual void f1() sealed {}   // OK
};
```

## <a name="example"></a>Przykład

Poniższy przykład demonstruje jedno użycie możliwe prywatnej funkcji sealed, wirtualne.

```
// C4486_b.cpp
// compile with: /clr /c
ref class B {};

ref class D : B {};

interface class I {
   B^ mf();
};

ref class E : I {
private:
   virtual B^ g() sealed = I::mf {
      return gcnew B;
   }

public:
   virtual D^ mf() {
      return gcnew D;
   }
};
```