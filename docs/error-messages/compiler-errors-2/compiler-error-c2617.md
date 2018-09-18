---
title: Błąd kompilatora C2617 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2617
dev_langs:
- C++
helpviewer_keywords:
- C2617
ms.assetid: d6a435d2-7d95-4dbf-ad4a-abe4744f63e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 14435dd5620a144f1b1dd53836c583acefe309c9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109876"
---
# <a name="compiler-error-c2617"></a>Błąd kompilatora C2617

'Funkcja': niespójna instrukcja return

Określona funkcja nie ma zadeklarowany typ zwracany i poprzedniej zwracana wartość nie zostały dostarczone przez instrukcję.

Poniższy przykład spowoduje wygenerowanie C2617:

```
// C2617.cpp
int i;
func() {   // no return type prototype
   if( i ) return;   // no return value
   else return( 1 );   // C2617 detected on this line
}
```

Możliwe rozwiązanie:

```
// C2617b.cpp
// compile with: /c
int i;
int MyF() {
   if (i)
      return 0;
   else
      return (1);
}
```