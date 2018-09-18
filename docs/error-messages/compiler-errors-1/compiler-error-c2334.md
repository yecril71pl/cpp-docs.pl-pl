---
title: Błąd kompilatora C2334 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2334
dev_langs:
- C++
helpviewer_keywords:
- C2334
ms.assetid: 36142855-e00b-4bbf-80f5-a301edeff46e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68ce0a6096cfd8a3a4e0fe52d897690f037be40b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073823"
---
# <a name="compiler-error-c2334"></a>Błąd kompilatora C2334

Nieoczekiwany(e) token(y) poprzedzającego ': lub {"; Pomijanie treści widocznych funkcji

Poniższy przykład spowoduje wygenerowanie C2334. Ten błąd występuje po błędzie C2059:

```
// C2334.cpp
// compile with: /c
// C2059 expected
struct s1 {
   s1   {}   // C2334
   s1() {}   // OK
};
```