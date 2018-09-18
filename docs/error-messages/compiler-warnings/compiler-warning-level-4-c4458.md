---
title: Kompilator ostrzeżenie (poziom 4) C4458 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4458
dev_langs:
- C++
helpviewer_keywords:
- C4458
ms.assetid: 7bdaa1b1-0caf-4d68-98c4-6bdd441c23fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 873aa94db899ae6620e2bbb1f24277c6e7c841c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094549"
---
# <a name="compiler-warning-level-4-c4458"></a>Kompilator ostrzeżenie (poziom 4) C4458

> Deklaracja "*identyfikator*" powoduje ukrycie składowej klasy

Deklaracja *identyfikator* w zakresie lokalnym ukrywa deklarację o takiej samej nazwie *identyfikator* w zakresie klasy. To ostrzeżenie informuje o tym, który odwołuje się do *identyfikator* w tym zakresie rozpoznać lokalnie zadeklarowanych wersji, a nie wersji elementu członkowskiego klasy, która może być lub może nie być zgodne z zamiarami użytkownika. Aby rozwiązać ten problem, zalecane jest nadać nazwy zmiennych lokalnych, które nie wchodzą w konflikt z nazwą składowej klasy.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4458, ponieważ parametr `x` i zmienną lokalną `y` w `member_fn` mają takie same nazwy elementów członkowskich danych klasy. Aby rozwiązać ten problem, należy używać różnych nazw parametrów i zmiennych lokalnych.

```cpp
// C4458_hide.cpp
// compile with: cl /W4 /c C4458_hide.cpp

struct S {
    int x;
    float y;
    void member_fn(long x) {   // C4458
        double y;  // C4458
        y = x;
        // To fix this issue, change the parameter name x
        // and local name y to something that does not
        // conflict with the data member names.
    }
} s;
```
