---
title: Błąd kompilatora C3352
ms.date: 11/04/2016
f1_keywords:
- C3352
helpviewer_keywords:
- C3352
ms.assetid: f233bed7-474e-425f-aad2-7801578169d4
ms.openlocfilehash: 6641f05c8daa5ad505c0bcb8d29a369ad5fd9a9a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58779602"
---
# <a name="compiler-error-c3352"></a>Błąd kompilatora C3352

'Funkcja': określona funkcja jest niezgodna z typem obiektu delegowanego "type"

Parametr, który wyświetla listę dla `function` i delegata nie są zgodne.

Aby uzyskać więcej informacji, zobacz [delegate (C++ Component Extensions)](../../extensions/delegate-cpp-component-extensions.md).

Poniższy przykład spowoduje wygenerowanie C3352:

```
// C3352.cpp
// compile with: /clr
delegate int D( int, int );
ref class C {
public:
   int mf( int ) {
      return 1;
   }

   // Uncomment the following line to resolve.
   // int mf(int, int) { return 1; }
};

int main() {
   C^ pC = gcnew C;
   System::Delegate^ pD = gcnew D( pC, &C::mf );   // C3352
}
```
