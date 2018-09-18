---
title: Błąd ewaluatora wyrażeń CXX0045 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0045
dev_langs:
- C++
helpviewer_keywords:
- CXX0045
- CAN0045
ms.assetid: 32181bc8-e79c-4ad7-a82f-47c62ec06d7d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d9913bc77dfc3fbc95bd03fd32c954c4d304d27
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023205"
---
# <a name="expression-evaluator-error-cxx0045"></a>Błąd CXX0045 programu Expression Evaluator

not — funkcja

Lista argumentów została dostarczona dla symbolu w programie, który nie jest nazwą funkcji.

## <a name="example"></a>Przykład

```
queue( alpha, beta )
```

gdy `queue` nie jest funkcją.

Ten błąd jest taka sama jak CAN0045.