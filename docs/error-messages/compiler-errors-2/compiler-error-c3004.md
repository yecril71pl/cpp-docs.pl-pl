---
title: Błąd kompilatora C3004 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3004
dev_langs:
- C++
helpviewer_keywords:
- C3004
ms.assetid: 819c2b57-8366-4ca7-9135-1f0c5e5b6bb6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9ccca52b5977c5d709b79dbc6351b5a94605849
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068806"
---
# <a name="compiler-error-c3004"></a>Błąd kompilatora C3004

"w klauzuli": Klauzula nie jest prawidłowa w dyrektywie OpenMP "dyrektywa"

OpenMP — klauzula został użyty w dyrektywie, dla której nie jest włączone.

Poniższy przykład spowoduje wygenerowanie C3004:

```
// C3004.c
// compile with: /openmp
int main()
{
   int x, y, z;

   // Shared clause not allowed for 'single' directive.
   #pragma omp single shared(x, y)   // C3004

   x = y;
}
```