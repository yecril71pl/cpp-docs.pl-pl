---
title: Błąd kompilatora C2760 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2760
dev_langs:
- C++
helpviewer_keywords:
- C2760
ms.assetid: 585757fd-d519-43f3-94e5-50316ac8b90b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ae920b9bf0d6d8a743bd9defac883304e80c117
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026091"
---
# <a name="compiler-error-c2760"></a>Błąd kompilatora C2760

Błąd składniowy: oczekiwano "Nazwa1" nie "Nazwa2"

Operator rzutowania jest używana z nieprawidłowy operator.

Poniższy przykład spowoduje wygenerowanie C2760:

```
// C2760.cpp
class B {};
class D : public B {};

void f(B* pb) {
    D* pd1 = static_cast<D*>(pb);
    D* pd2 = static_cast<D*>=(pb);  // C2760
    D* pd3 = static_cast<D*=(pb);   // C2760
}
```