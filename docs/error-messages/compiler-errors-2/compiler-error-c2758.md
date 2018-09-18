---
title: Błąd kompilatora C2758 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2758
dev_langs:
- C++
helpviewer_keywords:
- C2758
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ffa6d33dba70a463d789f3b0f016dc1d157eb65
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072930"
---
# <a name="compiler-error-c2758"></a>Błąd kompilatora C2758

"członek": składowa typu referencyjnego musi zostać zainicjowany

Błąd kompilatora C2758 występuje po konstruktora, nie inicjuje składowej typu odwołania na liście inicjatora. Kompilator pozostawia niezdefiniowane elementu członkowskiego. Odwołanie do elementu członkowskiego musi zmienne inicjowane, gdy zadeklarowane lub należy podać wartość w listy inicjowania konstruktora.

Poniższy przykład spowoduje wygenerowanie C2758:

```
// C2758.cpp
// Compile by using: cl /W3 /c C2758.cpp
struct A {
   const int i;

   A(int n) { };   // C2758
   // try the following line instead
   // A(int n) : i{n} {};
};
```