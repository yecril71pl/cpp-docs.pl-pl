---
title: Kompilator ostrzeżenie (poziom 1) C4384
ms.date: 11/04/2016
f1_keywords:
- C4384
helpviewer_keywords:
- C4384
ms.assetid: fafa8eb2-cbfc-4edb-8b0f-511ff5d37ac0
ms.openlocfilehash: 0f2666011e88dfd59eaaca154f4407bece7c963c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454697"
---
# <a name="compiler-warning-level-1-c4384"></a>Kompilator ostrzeżenie (poziom 1) C4384

\#pragma "make_public" można używać tylko w zakresie globalnym

[Make_public](../../preprocessor/make-public.md) pragma została zastosowana niepoprawnie.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4384.

```
// C4384.cpp
// compile with: /c /W1
namespace n {
   #pragma make_public(N::C)   // C4384
   namespace N {
      class C {};
   }
}
```