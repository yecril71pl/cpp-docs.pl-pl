---
title: Błąd kompilatora C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: 72646d7611163748fe7e27ea6c78cd38426eb6ad
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447812"
---
# <a name="compiler-error-c3279"></a>Błąd kompilatora C3279

częściowe i jawne specjalizacje jak również jawne utworzenia wystąpień szablonów klasy zadeklarowanych w przestrzeni nazw cli są niedozwolone.

`cli` Przestrzeni nazw jest zdefiniowana przez firmę Microsoft i zawiera pseudo-szablony. Microsoft C++ kompilatora nie zezwala na zdefiniowanych przez użytkownika, częściowe i jawne specjalizacje i jawne utworzenia wystąpień szablonów klasy w tej przestrzeni nazw.

Poniższy przykład spowoduje wygenerowanie C3279:

```
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```