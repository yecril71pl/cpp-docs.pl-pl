---
title: Błąd kompilatora C2753
ms.date: 11/04/2016
f1_keywords:
- C2753
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
ms.openlocfilehash: ea2901c998ac1a44ad142779e7ce48bfffff66c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202159"
---
# <a name="compiler-error-c2753"></a>Błąd kompilatora C2753

"*Template*": Częściowa specjalizacja nie jest zgodna z listą argumentów dla szablonu podstawowego

Jeśli lista argumentów szablonu jest zgodna z listą parametrów, kompilator traktuje ją jako ten sam szablon. Definiowanie tego samego szablonu dwa razy jest niedozwolone.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2753 i przedstawia sposób jego rozwiązania:

```cpp
// C2753.cpp
// compile with: cl /c C2753.cpp
template<class T>
struct A {};

template<class T>
struct A<T> {};   // C2753
// try the following line instead
// struct A<int> {};

template<class T, class U, class V, class W, class X>
struct B {};
```
