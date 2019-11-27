---
title: Ostrzeżenie kompilatora (poziom 4) C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: 982457ded987f6aee4f2891bbb7d9103b830cc99
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541791"
---
# <a name="compiler-warning-level-4-c4238"></a>Ostrzeżenie kompilatora (poziom 4) C4238

użyto niestandardowego rozszerzenia: Klasa rvalue użyta jako lvalue

Aby zapewnić zgodność z poprzednimi wersjami programu Visual C++, rozszerzenia Microsoft ( **/ze**) umożliwiają użycie typu klasy jako rvalue w kontekście, który niejawnie lub jawnie pobiera swój adres. W niektórych przypadkach, takich jak Poniższy przykład, może to być niebezpieczne.

## <a name="example"></a>Przykład

```cpp
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

To użycie powoduje błąd w obszarze zgodność ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).