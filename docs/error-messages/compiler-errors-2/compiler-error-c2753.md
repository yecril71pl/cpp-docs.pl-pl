---
title: Błąd kompilatora C2753
ms.date: 11/04/2016
f1_keywords:
- C2753
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
ms.openlocfilehash: e13c45cec99e60d8aec7dcc3db8e5a4813ea7de9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62228786"
---
# <a name="compiler-error-c2753"></a>Błąd kompilatora C2753

"*szablonu*": specjalizacji nie odpowiada liście argumentów dla podstawowego szablonu

Jeśli lista argumentów szablonu odpowiada liście parametrów, kompilator traktuje jako tego samego szablonu. Definiowanie dwa razy tego samego szablonu nie jest dozwolone.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2753 i pokazuje sposób, aby rozwiązać ten problem:

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