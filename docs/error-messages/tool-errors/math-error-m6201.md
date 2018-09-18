---
title: Błąd matematyczny M6201 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6201
dev_langs:
- C++
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87d2c09d6448bcf7fb0557fa3a174c60205a34ea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099398"
---
# <a name="math-error-m6201"></a>Błąd matematyczny M6201

'Funkcja': błąd _domeny

Argument do danej funkcji była spoza domeny prawne wartości wejściowe dla tej funkcji.

## <a name="example"></a>Przykład

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

Ten błąd wywołania `_matherr` funkcję z nazwy funkcji, argumentów i typ błędu. Można napisać ponownie `_matherr` funkcję, aby dostosować obsługi niektórych błędów zmiennoprzecinkowym zapisu matematycznego w czasie wykonywania.