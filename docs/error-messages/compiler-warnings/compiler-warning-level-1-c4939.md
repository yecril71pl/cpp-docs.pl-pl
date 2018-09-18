---
title: Kompilator ostrzeżenie (poziom 1) C4939 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4939
dev_langs:
- C++
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e13cab2d5277cca0a1962b8ec254aaef10cfc98
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118768"
---
# <a name="compiler-warning-level-1-c4939"></a>Kompilator ostrzeżenie (poziom 1) C4939

\#pragma vtordisp jest przestarzała i zostanie usunięta w przyszłej wersji programu Visual C++

[Vtordisp](../../preprocessor/vtordisp.md) pragma zostanie usunięta w przyszłej wersji programu Visual C++.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4939.

```
// C4939.cpp
// compile with: /c /W1
#pragma vtordisp(off)   // C4939
```