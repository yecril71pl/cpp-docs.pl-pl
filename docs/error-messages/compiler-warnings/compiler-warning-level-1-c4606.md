---
title: Kompilator ostrzeżenie (poziom 1) C4606 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4606
dev_langs:
- C++
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcdaba046f495dc3a29a7c9228edc561674f568f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035997"
---
# <a name="compiler-warning-level-1-c4606"></a>Kompilator ostrzeżenie (poziom 1) C4606

\#warning elementu pragma: "warning_number" ignorowane. Ostrzeżenia analizy kodu nie są skojarzone z poziomami ostrzeżeń

Ostrzeżenia analizy kodu, tylko `error`, `once`, i `default` są obsługiwane w przypadku [ostrzeżenie](../../preprocessor/warning.md) pragmy.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4606.

```
// C4606.cpp
// compile with: /c /W1
#pragma warning(1: 6001)   // C4606
#pragma warning(once: 6001)   // OK
```