---
title: Kompilator ostrzeżenie (poziom 1) C4461
ms.date: 11/04/2016
f1_keywords:
- C4461
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
ms.openlocfilehash: 5cc9b08f0f25e9c92b4185f060ab123684c5d9e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591025"
---
# <a name="compiler-warning-level-1-c4461"></a>Kompilator ostrzeżenie (poziom 1) C4461

"type": Ta klasa ma finalizator "finalizator", ale nie ma destruktora "dtor"

Obecność finalizator w typie oznacza zasobów do usunięcia. Chyba że finalizator jest jawnie wywoływana z destruktora typu, środowisko uruchomieniowe języka wspólnego Określa, kiedy finalizatora, została uruchomiona po obiekt wykracza poza zakres.

Jeśli zdefiniowanie destruktora w typie, a następnie jawnie wywołać finalizatora z destruktora, sposób deterministyczny można uruchomić usługi finalizatora.

Aby uzyskać więcej informacji, zobacz [destruktory i finalizatory](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4461.

```
// C4461.cpp
// compile with: /W1 /clr /c
ref class A {
protected:
   !A() {}   // C4461
};

// OK
ref struct B {
   ~B() {
      B::!B();
   }

   !B() {}
};
```