---
title: Błąd kompilatora C2351 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2351
dev_langs:
- C++
helpviewer_keywords:
- C2351
ms.assetid: 5439ccf6-66f6-4859-964c-c73f5eddfc1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c92f955beaafa92a8259df4878301158d03c18ff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034775"
---
# <a name="compiler-error-c2351"></a>Błąd kompilatora C2351

przestarzała Inicjalizacja składni konstruktora C++

Na liście inicjowania nowego stylu dla konstruktora jawnie nazwę każdego bezpośrednią klasą bazową, nawet jeśli jest on tylko podstawowej klasy.

Poniższy przykład spowoduje wygenerowanie C2351:

```
// C2351.cpp
// compile with: /c
class B {
public:
   B() : () {}   // C2351
   B() {}   // OK
};
```