---
title: Kompilator ostrzeżenie (poziom 4) C4457 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4457
dev_langs:
- C++
helpviewer_keywords:
- C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62232a814bed47f8b6a5041d20e6f37776abffe8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093535"
---
# <a name="compiler-warning-level-4-c4457"></a>Kompilator ostrzeżenie (poziom 4) C4457

> Deklaracja "*identyfikator*" powoduje ukrycie parametru funkcji

Deklaracja *identyfikator* w zakresie lokalnym ukrywa deklarację parametru funkcji takiej samej nazwie. To ostrzeżenie informuje o tym, który odwołuje się do *identyfikator* w zakresie lokalnym rozwiązać wersji lokalnie zadeklarowane, nie parametrze, co może spowodować lub może nie być zgodne z zamiarami użytkownika. Aby rozwiązać ten problem, zalecane jest nadać nazwy zmiennych lokalnych, które nie wchodzą w konflikt z nazwy parametru.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4457, ponieważ parametr `x` i zmienną lokalną `x` w `member_fn` takich samych nazwach. Aby rozwiązać ten problem, należy używać różnych nazw parametrów i zmiennych lokalnych.

```cpp
// C4457_hide.cpp
// compile with: cl /W4 /c C4457_hide.cpp

struct S {
    void member_fn(unsigned x) {
        double a = 0;
        for (int x = 0; x < 10; ++x) {  // C4457
            a += x; // uses local x
        }
        a += x; // uses parameter x
    }
} s;
```
