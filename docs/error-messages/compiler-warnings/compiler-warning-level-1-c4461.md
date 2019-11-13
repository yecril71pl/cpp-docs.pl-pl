---
title: Ostrzeżenie kompilatora (poziom 1) C4461
ms.date: 11/04/2016
f1_keywords:
- C4461
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
ms.openlocfilehash: 195e5532b6555210077e43ad3086ee3106f3e757
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966014"
---
# <a name="compiler-warning-level-1-c4461"></a>Ostrzeżenie kompilatora (poziom 1) C4461

"Type": Ta klasa ma finalizator "Finalizer", ale nie ma destruktora "dtor"

Obecność finalizatora w typie oznacza zasoby do usunięcia. Chyba że finalizator jest jawnie wywoływany z destruktora typu, środowisko uruchomieniowe języka wspólnego określa, kiedy ma być uruchamiany finalizator, gdy obiekt wykracza poza zakres.

Jeśli zdefiniujesz destruktor w typie i jawnie wywoła finalizator z destruktora, można w sposób jednoznaczny uruchomić finalizator.

Aby uzyskać więcej informacji, zobacz [destruktory i finalizatory](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4461.

```cpp
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