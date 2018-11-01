---
title: Błąd kompilatora C2724
ms.date: 11/04/2016
f1_keywords:
- C2724
helpviewer_keywords:
- C2724
ms.assetid: 4e4664bc-8c96-4156-b79f-03436f532ea8
ms.openlocfilehash: 3014a12767cb9a73dc65852c544b7ac9574b9a52
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585253"
---
# <a name="compiler-error-c2724"></a>Błąd kompilatora C2724

'Identyfikator': "static" nie powinna być używana w funkcji składowej zdefiniowanej w zakresie pliku

Statyczne funkcje Członkowskie powinien być zadeklarowany za pomocą zewnętrznego powiązania.

Poniższy przykład spowoduje wygenerowanie C2724:

```
// C2724.cpp
class C {
   static void func();
};

static void C::func(){};   // C2724
// try the following line instead
// void C::func(){};
```