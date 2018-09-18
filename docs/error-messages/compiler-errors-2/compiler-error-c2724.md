---
title: Błąd kompilatora C2724 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2724
dev_langs:
- C++
helpviewer_keywords:
- C2724
ms.assetid: 4e4664bc-8c96-4156-b79f-03436f532ea8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d637892a71f9a2c9bafdced6cb3a6e51e23ae463
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029341"
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