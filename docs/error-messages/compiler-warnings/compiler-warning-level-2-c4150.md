---
title: Kompilator ostrzeżenie (poziom 2) C4150
ms.date: 11/04/2016
f1_keywords:
- C4150
helpviewer_keywords:
- C4150
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
ms.openlocfilehash: 4c5c10ee0ea3242e52e6db5391694c9ddf941a78
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527676"
---
# <a name="compiler-warning-level-2-c4150"></a>Kompilator ostrzeżenie (poziom 2) C4150

Usunięcie wskaźnika do niekompletnego typu 'type'; Brak wywołania destruktora

**Usuń** operator jest wywoływana, aby usunąć typ, który został zadeklarowany, ale nie zdefiniowano, aby kompilator nie może odnaleźć destruktora.

Poniższy przykład spowoduje wygenerowanie C4150:

```
// C4150.cpp
// compile with: /W2
class  IncClass;

void NoDestruct( IncClass* pIncClass )
{
   delete pIncClass;
} // C4150, define class to resolve

int main()
{
}
```