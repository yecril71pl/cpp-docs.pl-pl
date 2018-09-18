---
title: Błąd kompilatora C2611 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2611
dev_langs:
- C++
helpviewer_keywords:
- C2611
ms.assetid: 3f2d5253-f24f-4724-83d0-6b2aa6a4e551
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 728d22a7af72232618716e665b241188773cd66c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031291"
---
# <a name="compiler-error-c2611"></a>Błąd kompilatora C2611

"token": niedozwolony następujące "~" (oczekiwany identyfikator)

Token nie jest identyfikatorem.

Poniższy przykład spowoduje wygenerowanie C2611:

```
// C2611.cpp
// compile with: /c
class C {
   C::~operator int();   // C2611
   ~C();   // OK
};
```