---
title: Ostrzeżenie kompilatora (poziom 1) C4813
ms.date: 11/04/2016
f1_keywords:
- C4813
helpviewer_keywords:
- C4813
ms.assetid: c30bf877-ab04-4fe4-897e-8162092426f0
ms.openlocfilehash: c63539b14041a8615b0a5ad99932c0d44a4942b8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174898"
---
# <a name="compiler-warning-level-1-c4813"></a>Ostrzeżenie kompilatora (poziom 1) C4813

"Function": funkcja zaprzyjaźniona klasy lokalnej musiała zostać poprzednio zadeklarowana

Funkcja zaprzyjaźniona w klasie wewnętrznej nie została zadeklarowana w klasie zewnętrznej.

Poniższy przykład generuje C4813:

```cpp
// C4813.cpp
// compile with: /W1 /LD
void MyClass()
{
   // void func();
   class InnerClass
   {
      friend void func();   // C4813 uncomment declaration above
   };
}
```
