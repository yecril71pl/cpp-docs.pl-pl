---
title: Błąd kompilatora C2537 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2537
dev_langs:
- C++
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65db4fa66d147cc46c1a6013d07048892dfa0800
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136026"
---
# <a name="compiler-error-c2537"></a>Błąd kompilatora C2537

"specyfikatora": Niedozwolona specyfikacja powiązania

Możliwe przyczyny:

1. Specyfikator powiązania nie jest obsługiwane. Obsługiwane jest tylko specyfikator powiązania "C".

1. Powiązania "C" określono więcej niż jedną funkcję w zestaw przeciążonych funkcji. Jest to niedozwolone.

Poniższy przykład spowoduje wygenerowanie C2537:

```
// C2537.cpp
// compile with: /c
extern "c" void func();   // C2537
extern "C" void func2();   // OK
```