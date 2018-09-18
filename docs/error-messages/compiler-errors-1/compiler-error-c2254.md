---
title: Błąd kompilatora C2254 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2254
dev_langs:
- C++
helpviewer_keywords:
- C2254
ms.assetid: 49bb3d7e-3bdf-4af6-937c-fa627be412a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6030f85ef1b8742b07f1be92101d740732207fa5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067093"
---
# <a name="compiler-error-c2254"></a>Błąd kompilatora C2254

'Funkcja': czysty specyfikator lub abstrakcyjny specyfikator override nie dozwolony dla funkcji zaprzyjaźnionej

A `friend` funkcji jest określony jako czysty `virtual`.

Poniższy przykład spowoduje wygenerowanie C2254:

```
// C2254.cpp
// compile with: /c
class A {
public:
   friend void func1() = 0;   // C2254, func1 is friend
   void virtual func2() = 0;   // OK, pure virtual
   friend void func3();   // OK, friend not virtual nor pure
};

void func1() {};
void func3() {};
```