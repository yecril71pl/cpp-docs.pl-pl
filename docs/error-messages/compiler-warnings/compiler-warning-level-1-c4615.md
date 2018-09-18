---
title: Kompilatora (poziom 1) ostrzeżenie C4615 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4615
dev_langs:
- C++
helpviewer_keywords:
- C4615
ms.assetid: 7b107c01-0da2-4e01-8b40-93813e30b94c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd260e37fb3f98f3e23d1c99c9ff53cae4f0198f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073710"
---
# <a name="compiler-warning-level-1-c4615"></a>Kompilatora (poziom 1) ostrzeżenie C4615

\#warning elementu pragma: Nieznany typ ostrzeżenia użytkownika

Nieprawidłowy specyfikator ostrzeżenie był używany z **pragma** [ostrzeżenie](../../preprocessor/warning.md). Aby naprawić błąd, należy użyć Nieprawidłowy specyfikator ostrzeżenie.

Poniższy przykład spowoduje wygenerowanie C4615:

```
// C4615.cpp
// compile with: /W1 /LD
#pragma warning(enable : 4401)   // C4615, 'enable' not valid specifier

// use the code below to resolve the error
// #pragma warning(default : 4401)
```