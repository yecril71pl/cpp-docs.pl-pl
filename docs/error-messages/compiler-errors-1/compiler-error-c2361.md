---
title: Błąd kompilatora C2361 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2361
dev_langs:
- C++
helpviewer_keywords:
- C2361
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d91ee8b004e2f485326378eb2e1611f217f745c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029796"
---
# <a name="compiler-error-c2361"></a>Błąd kompilatora C2361

Inicjowanie 'Identyfikator' jest pomijana przy etykiecie "default"

Inicjowanie `identifier` może być pominięty w `switch` instrukcji. Nie można przeskoczyć poza deklaracją za pomocą inicjatora, chyba że deklaracja jest ujęty w bloku. (Chyba że zostanie ona zadeklarowana w bloku, zmienna znajduje się w zakresie aż do końca `switch` instrukcja.)

Poniższy przykład spowoduje wygenerowanie C2361:

```
// C2361.cpp
void func( void ) {
   int x;
   switch (x) {
   case 0 :
      int i = 1;
      { int j = 1; }
   default :   // C2361 error
      int k = 1;
   }
}
```

Możliwe rozwiązanie:

```
// C2361b.cpp
// compile with: /c
void func( void ) {
   int x = 0;
   switch (x) {
   case 0 :
      { int j = 1; int i = 1;}
   default :
      int k = 1;
   }
}
```