---
title: Kompilator ostrzeżenie (poziom 1) C4461 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4461
dev_langs:
- C++
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86c12208c6992b97f30bc36ea821ba26148ff751
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081404"
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