---
title: Błąd kompilatora C3420
ms.date: 11/04/2016
f1_keywords:
- C3420
helpviewer_keywords:
- C3420
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
ms.openlocfilehash: 3db109598ce0741ca34a230d8925994543bcb5ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645942"
---
# <a name="compiler-error-c3420"></a>Błąd kompilatora C3420

"finalizator": finalizator nie może być wirtualny

Finalizator może zostać wywołana tylko-niemal z jego typie otaczającym. Dlatego jest błędem jest deklaracja finalizatora wirtualnego.

Aby uzyskać więcej informacji, zobacz [destruktory i finalizatory w instrukcje: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3420.

```
// C3420.cpp
// compile with: /clr /c
ref class R {
   virtual !R() {}   // C3420
};
```