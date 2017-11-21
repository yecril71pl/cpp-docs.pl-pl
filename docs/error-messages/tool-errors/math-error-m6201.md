---
title: "Błąd matematyczny M6201 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: M6201
dev_langs: C++
helpviewer_keywords: M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e8288770d74497e576a299d683b846214a187a1c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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