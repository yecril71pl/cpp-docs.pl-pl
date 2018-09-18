---
title: Błąd kompilatora C2658 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2658
dev_langs:
- C++
helpviewer_keywords:
- C2658
ms.assetid: 638368e8-7893-4a14-abec-13c768a9543a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adbaa5c538bf5e85f30064d698d7755851c9549b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096200"
---
# <a name="compiler-error-c2658"></a>Błąd kompilatora C2658

"członek": ponowna definicja w anonimowej strukturze/związku

Dwie struktury anonimowe lub związkami zawiera deklaracje członków przy użyciu tego samego identyfikatora, ale z różnymi typami. W obszarze [/Za](../../build/reference/za-ze-disable-language-extensions.md), będzie również otrzymać ten błąd dla elementów członkowskich z tym samym identyfikatorem i typu.

Poniższy przykład spowoduje wygenerowanie C2658:

```
// C2658.cpp
// compile with: /c
struct X {
   union { // can be struct too
      int i;
   };
   union {
      int i;   // Under /Za, C2658
      // int i not needed here because it is defined in the first union
   };
};

struct Z {
   union {
      char *i;
   };

   union {
      void *i;   // C2658 redefinition of 'i'
      // try the following line instead
      // void *ii;
   };
};
```