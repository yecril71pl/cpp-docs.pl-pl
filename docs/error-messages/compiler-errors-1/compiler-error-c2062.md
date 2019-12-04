---
title: Błąd kompilatora C2062
ms.date: 11/04/2016
f1_keywords:
- C2062
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
ms.openlocfilehash: a709a540b24756a7e08f98552c5888a55c3ea601
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735973"
---
# <a name="compiler-error-c2062"></a>Błąd kompilatora C2062

nieoczekiwany typ "Type"

Kompilator nie oczekiwał nazwy typu.

Poniższy przykład generuje C2062:

```cpp
// C2062.cpp
// compile with: /c
struct A {  : int l; };   // C2062
struct B { private: int l; };   // OK
```

C2062 może również wystąpić ze względu na sposób, w jaki kompilator obsługuje niezdefiniowane typy na liście parametrów konstruktora. Jeśli kompilator napotyka niezdefiniowany typ (błędny), zakłada, że Konstruktor jest wyrażeniem i problemy C2062. Aby rozwiązać ten problem, należy użyć zdefiniowanych typów na liście parametrów konstruktora.
