---
title: Błąd kompilatora C2633 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2633
dev_langs:
- C++
helpviewer_keywords:
- C2633
ms.assetid: a7aceb65-4255-42d6-a8fb-e3cb6c4d2270
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2750cad468158ec5f8eddc967392ea68c1029119
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108566"
---
# <a name="compiler-error-c2633"></a>Błąd kompilatora C2633

'Identyfikator': "inline" jest jedyną dozwoloną klasą magazynu dla konstruktorów

Konstruktor jest zadeklarowany jako klasy magazynu innym niż wbudowany.

Poniższy przykład spowoduje wygenerowanie C2633:

```
// C2633.cpp
// compile with: /c
class C {
   extern C();   // C2633, not inline
   inline C();   // OK
};
```