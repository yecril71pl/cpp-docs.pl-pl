---
title: Błąd kompilatora C3279 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3279
dev_langs:
- C++
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89c537da9bcf91e7774353cc1516a4c44e28649c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056771"
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