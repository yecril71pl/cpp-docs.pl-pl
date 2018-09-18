---
title: Błąd kompilatora C2636 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2636
dev_langs:
- C++
helpviewer_keywords:
- C2636
ms.assetid: 379873ec-8d05-49f8-adf1-b067bc07bdb8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5eb89c6e2a555aa6f832018a69a9648e8e2953ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086398"
---
# <a name="compiler-error-c2636"></a>Błąd kompilatora C2636

'Identyfikator': wskaźnik do odwołania składowej jest niedozwolony

Wskaźnik do odwołania składowej został zadeklarowany.

Poniższy przykład spowoduje wygenerowanie C2636:

```
// C2636.cpp
struct S {};
int main() {
   int &S::*prs;   // C2636
   int S::*prs1;   // OK
   int *S::*prs2;   // OK
}
```