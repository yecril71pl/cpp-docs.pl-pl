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
ms.openlocfilehash: d6a15e841cfc8daf1abdafc9997698807e7356af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="math-error-m6201"></a>Błąd matematyczny M6201
"Funkcja": _domain — błąd  
  
 Argument funkcji danego był spoza domeny prawne wartości wejściowe dla tej funkcji.  
  
## <a name="example"></a>Przykład  
  
```  
result = sqrt(-1.0)   // C statement  
result = SQRT(-1.0)   !  FORTRAN statement  
```  
  
 Ten błąd wywołania `_matherr` funkcji z nazwą funkcji, argumentów i typ błędu. Można ponownie napisać `_matherr` funkcji, aby dostosować obsługę niektórych błędów czasu wykonywania zmiennoprzecinkowej matematyczny.