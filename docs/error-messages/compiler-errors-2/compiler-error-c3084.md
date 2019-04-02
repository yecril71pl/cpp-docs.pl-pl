---
title: Błąd kompilatora C3084
ms.date: 11/04/2016
f1_keywords:
- C3084
helpviewer_keywords:
- C3084
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
ms.openlocfilehash: 01e229fe0ae5bf9e04c577bb653ff1ed7fdb33bf
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773908"
---
# <a name="compiler-error-c3084"></a>Błąd kompilatora C3084

'Funkcja': finalizator/destruktor nie może być "— słowo kluczowe"

Nieprawidłowo zadeklarowano finalizator lub destruktor.

Na przykład, destruktor nie powinien być oznaczony jako zapieczętowany.  Destruktor jest niedostępna dla typów pochodnych.  Aby uzyskać więcej informacji, zobacz [jawne zastępowanie](../../extensions/explicit-overrides-cpp-component-extensions.md) i [destruktory i finalizatory w sposób: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3084.

```
// C3084.cpp
// compile with: /clr /c
ref struct R {
protected:
   !R() sealed;   // C3084
   !R() abstract;   // C3084
   !R();
};
```