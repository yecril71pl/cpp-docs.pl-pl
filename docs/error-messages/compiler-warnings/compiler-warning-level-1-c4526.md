---
title: Kompilator ostrzeżenie (poziom 1) C4526
ms.date: 11/04/2016
f1_keywords:
- C4526
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
ms.openlocfilehash: 892e6c37e54a868be48ced35354a1096aa7bf9d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160747"
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