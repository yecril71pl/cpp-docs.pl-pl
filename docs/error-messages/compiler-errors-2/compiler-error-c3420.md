---
title: Błąd kompilatora C3420
ms.date: 11/04/2016
f1_keywords:
- C3420
helpviewer_keywords:
- C3420
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
ms.openlocfilehash: 5e165a0c181bc27adebe75111050f49130305693
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756256"
---
# <a name="compiler-error-c3420"></a>Błąd kompilatora C3420

"Finalizer": finalizator nie może być wirtualny

Finalizator może być wywołany tylko jako niepraktycznie od jego typu otaczającego. W związku z tym jest to błąd w celu zadeklarowania wirtualnego finalizatora.

Aby uzyskać więcej informacji, zobacz [destruktory i finalizatory w instrukcje: Definiowanie i korzystanie z klas i struktur (C++/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3420.

```cpp
// C3420.cpp
// compile with: /clr /c
ref class R {
   virtual !R() {}   // C3420
};
```
