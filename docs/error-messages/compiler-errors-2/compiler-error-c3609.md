---
title: Compiler Error C3609
ms.date: 11/04/2016
f1_keywords:
- C3609
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
ms.openlocfilehash: 27eba3df800c42cc53a7031e958a675c84255440
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780980"
---
# <a name="compiler-error-c3609"></a>Compiler Error C3609

"członek": funkcja zapieczętowana ani końcowego musi być funkcją wirtualną

[Zapieczętowanego](../../extensions/sealed-cpp-component-extensions.md) i [końcowego](../../cpp/final-specifier.md) słowa kluczowe są dozwolone tylko dla klasy, struktury lub element członkowski funkcji oznaczonej `virtual`.

Poniższy przykład spowoduje wygenerowanie C3609:

```
// C3609.cpp
// compile with: /clr /c
ref class C {
   int f() sealed;   // C3609
   virtual int f2() sealed;   // OK
};
```
