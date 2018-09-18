---
title: Kompilator ostrzeżenie (poziom 2) C4150 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4150
dev_langs:
- C++
helpviewer_keywords:
- C4150
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d317384d3708679d485ae0a77c6ee9b6622b9c83
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050427"
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