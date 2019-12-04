---
title: Błąd kompilatora C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: 3025dbf7c6bf4701218c2d9a956cae26d7180848
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757608"
---
# <a name="compiler-error-c3279"></a>Błąd kompilatora C3279

częściowe i jawne specjalizacje oraz jawne wystąpienia szablonów klas zadeklarowanych w przestrzeni nazw CLI są niedozwolone

Przestrzeń nazw `cli` jest definiowana przez firmę Microsoft i zawiera pseudo Templates. Kompilator firmy C++ Microsoft nie zezwala na zdefiniowane przez użytkownika, częściowe i jawne specjalizacje oraz jawne wystąpienia szablonów klas w tej przestrzeni nazw.

Poniższy przykład generuje C3279:

```cpp
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```
