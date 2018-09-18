---
title: Błąd kompilatora C2279 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2279
dev_langs:
- C++
helpviewer_keywords:
- C2279
ms.assetid: 1b5c88ef-2336-49b8-9ddb-d61f97c73e14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1b194476e6400618045324a14c9e4781f9ec8f0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067951"
---
# <a name="compiler-error-c2279"></a>Błąd kompilatora C2279

Specyfikacja wyjątku nie może występować w deklaracji typedef

W obszarze **/Za**, [specyfikacje wyjątków](../../cpp/exception-specifications-throw-cpp.md) nie są dozwolone w deklaracji typedef.

Poniższy przykład spowoduje wygenerowanie C2279:

```
// C2279.cpp
// compile with: /Za /c
typedef int (*xy)() throw(...);   // C2279
typedef int (*xyz)();   // OK
```