---
title: Ostrzeżenie kompilatora C4485
ms.date: 11/04/2016
f1_keywords:
- C4485
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
ms.openlocfilehash: 896fca6c6b257c90ccdf813a9c6cb6bc27ad9e96
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623614"
---
# <a name="compiler-warning-c4485"></a>Ostrzeżenie kompilatora C4485

"override_function": pasuje do metody bazowej klasy referencyjnej "base_class_function", ale nie jest oznaczona modyfikatorem "New" ani "override"; Założono modyfikator "New" (i "Virtual")

Metoda dostępu zastępuje, przy użyciu słowa kluczowego `virtual` lub bez niego, funkcja akcesora klasy bazowej, ale specyfikator `override` lub `new` nie był częścią zastępujący sygnatury funkcji. Dodaj specyfikator `new` lub `override`, aby rozwiązać to ostrzeżenie.

Aby uzyskać więcej informacji, zobacz [przesłonięcie](../../extensions/override-cpp-component-extensions.md) i [nowe (nowe miejsce w tabeli tablic wirtualnych)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md) .

C4485 jest zawsze wystawiony jako błąd. Użyj [ostrzeżenia](../../preprocessor/warning.md) pragma, aby pominąć C4485.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4485

```cpp
// C4485.cpp
// compile with: /clr
delegate void Del();

ref struct A {
   virtual event Del ^E;
};

ref struct B : A {
   virtual event Del ^E;   // C4485
};

ref struct C : B {
   virtual event Del ^E {
      void raise() override {}
      void add(Del ^) override {}
      void remove(Del^) override {}
   }
};
```