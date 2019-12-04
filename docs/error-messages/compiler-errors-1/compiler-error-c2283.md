---
title: Błąd kompilatora C2283
ms.date: 11/04/2016
f1_keywords:
- C2283
helpviewer_keywords:
- C2283
ms.assetid: 8a5b3175-b480-4598-a1f7-0b50504c5caa
ms.openlocfilehash: 7f3568aa5dfee116a225256a4452465c05f72f6f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759155"
---
# <a name="compiler-error-c2283"></a>Błąd kompilatora C2283

"Identyfikator": czysty specyfikator lub abstrakcyjny specyfikator override nie jest dozwolony dla nienazwanej struktury

Funkcja członkowska nienazwanej klasy lub struktury jest zadeklarowana za pomocą czystego specyfikatora, co jest niedozwolone.

Poniższy przykład generuje C2283:

```cpp
// C2283.cpp
// compile with: /c
struct {
   virtual void func() = 0;   // C2283
};
struct T {
   virtual void func() = 0;   // OK
};
```
