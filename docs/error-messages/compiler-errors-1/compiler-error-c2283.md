---
title: Błąd kompilatora C2283
ms.date: 11/04/2016
f1_keywords:
- C2283
helpviewer_keywords:
- C2283
ms.assetid: 8a5b3175-b480-4598-a1f7-0b50504c5caa
ms.openlocfilehash: 1113236680241a80c462e382c8c9c7de342b5463
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629999"
---
# <a name="compiler-error-c2283"></a>Błąd kompilatora C2283

'Identyfikator': czysty specyfikator lub abstrakcyjny specyfikator override nie dozwolony dla struktury nienazwane

Funkcji składowej bez nazwy klasy lub struktury jest zadeklarowany za pomocą czysty specyfikator jest niedozwolony.

Poniższy przykład spowoduje wygenerowanie C2283:

```
// C2283.cpp
// compile with: /c
struct {
   virtual void func() = 0;   // C2283
};
struct T {
   virtual void func() = 0;   // OK
};
```