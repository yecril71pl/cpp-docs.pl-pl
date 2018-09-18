---
title: Błąd kompilatora C2365 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2365
dev_langs:
- C++
helpviewer_keywords:
- C2365
ms.assetid: 35839b0b-4055-4b79-8957-b3a0871bdd02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8809c4137cd9b3c1d45960387b8a28bdb007ac8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029157"
---
# <a name="compiler-error-c2365"></a>Błąd kompilatora C2365

"składowej klasy": zmiana definicji; Definicja Poprzednia była "składowej klasy"

Próbowano zmienić definicję składowej klasy.

Poniższy przykład spowoduje wygenerowanie C2365.

```
// C2365.cpp
// compile with: /c
class C1 {
   int CFunc();
   char *CFunc;   // C2365, already exists as a member function

   int CMem;
   char *CMem();   // C2365, already exists as a data member
};
```