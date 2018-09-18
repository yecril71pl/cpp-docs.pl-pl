---
title: Błąd kompilatora C2111 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2111
dev_langs:
- C++
helpviewer_keywords:
- C2111
ms.assetid: 38fd42ec-1480-4a44-aaca-ae4593ed5f50
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1fcfac1e268ae3e8c6a16af31a1e7f06c073a5d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023426"
---
# <a name="compiler-error-c2111"></a>Błąd kompilatora C2111

"+": Dodawanie wskaźników wymaga całkowitego operandu

Próbowano dodać wartość nonintegral do wskaźnika za pomocą plus ( `+` ) — operator.

Poniższy przykład spowoduje wygenerowanie C2111:

```
// C2111.cpp
int main() {
   int *a = 0, *pa = 0, b = 0;
   double d = 0.00;

   a = pa + d;   // C2111
   a = pa + b;   // OK
}
```