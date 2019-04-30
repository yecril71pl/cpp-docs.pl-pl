---
title: Compiler Error C3609
ms.date: 11/04/2016
f1_keywords:
- C3609
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
ms.openlocfilehash: 27eba3df800c42cc53a7031e958a675c84255440
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344514"
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
