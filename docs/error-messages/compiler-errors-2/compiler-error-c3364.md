---
title: Błąd kompilatora C3364 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3364
dev_langs:
- C++
helpviewer_keywords:
- C3364
ms.assetid: 98654741-60fe-4472-a6af-e580f8c0a6e1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65ac2c54ccd0fe4a086cfcc79cf4dba269876ad3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096252"
---
# <a name="compiler-error-c3364"></a>Błąd kompilatora C3364

"delegowanie": Konstruktor delegata: argument musi być wskaźnikiem do funkcji składowej klasy zarządzanej lub funkcja globalna

Drugi parametr konstruktora delegata przyjmuje adresu funkcji składowej lub adres statycznej funkcji członkowskiej dowolnej klasy. Oba są traktowane jako prosty adresów.

Poniższy przykład spowoduje wygenerowanie C3364:

```
// C3364_2.cpp
// compile with: /clr

delegate int D( int, int );

ref class C {
public:
   int mf( int, int ) {
      return 1;
   }
};

int main() {
   C^ pC = gcnew C;
   System::Delegate^ pD = gcnew D( pC,pC->mf( 1, 2 ) ); // C3364

   // try the following line instead
   // System::Delegate^ pD = gcnew D(pC, &C::mf);
}
```
