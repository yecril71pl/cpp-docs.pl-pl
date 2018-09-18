---
title: Błąd kompilatora C3352 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3352
dev_langs:
- C++
helpviewer_keywords:
- C3352
ms.assetid: f233bed7-474e-425f-aad2-7801578169d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c045df51271c761ab61a3d5ec7d97634858909a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093852"
---
# <a name="compiler-error-c3352"></a>Błąd kompilatora C3352

'Funkcja': określona funkcja jest niezgodna z typem obiektu delegowanego "type"

Parametr, który wyświetla listę dla `function` i delegata nie są zgodne.

Aby uzyskać więcej informacji, zobacz [delegate (C++ Component Extensions)](../../windows/delegate-cpp-component-extensions.md).

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
