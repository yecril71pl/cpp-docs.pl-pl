---
title: Błąd kompilatora C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: 5f39510ee9ec0e717d675aa8b396405bc33b4ea1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445009"
---
# <a name="compiler-error-c3279"></a>Błąd kompilatora C3279

częściowe i jawne specjalizacje jak również jawne utworzenia wystąpień szablonów klasy zadeklarowanych w przestrzeni nazw cli są niedozwolone.

`cli` Przestrzeni nazw jest zdefiniowana przez firmę Microsoft i zawiera pseudo-szablony. Kompilator języka Visual C++ nie zezwala na zdefiniowanych przez użytkownika, częściowe i jawne specjalizacje i jawne utworzenia wystąpień szablonów klasy w tej przestrzeni nazw.

Poniższy przykład spowoduje wygenerowanie C3279:

```
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```