---
title: Kompilator ostrzeżenie (poziom 1) C4526 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4526
dev_langs:
- C++
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ed6f2da3252c27b7a84b4d5b73f7e8ba52823dd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118508"
---
# <a name="compiler-warning-level-1-c4526"></a>Kompilator ostrzeżenie (poziom 1) C4526

'Funkcja': funkcja statycznej składowej nie można przesłonić funkcji wirtualnej ' wirtualnego function'override zignorowane, funkcja wirtualna zostanie ukryta

Funkcja statycznej składowej spełnia kryteria, które można przesłonić funkcji wirtualnej, co sprawia, że funkcja elementu członkowskiego wirtualnego i statyczne.

Poniższy kod generuje C4526:

```
// C4526.cpp
// compile with: /W1 /c
// C4526 expected
struct myStruct1 {
   virtual void __stdcall func( int ) = 0;
};

struct myStruct2: public myStruct1 {
   static void __stdcall func( int );
};
```

Poniżej przedstawiono możliwe poprawki:

- Jeśli funkcja była zamierzona można przesłonić funkcji wirtualnej klasy bazowej, Usuń specyfikator statycznej.

- Jeśli funkcja ma to być statycznej funkcji członkowskiej, należy ją zmienić, dzięki czemu nie koliduje to z funkcją wirtualną klasę bazową.