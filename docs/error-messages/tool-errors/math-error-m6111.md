---
title: Błąd matematyczny M6111 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6111
dev_langs:
- C++
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b03937ed442b169b960d573b44c0eb6ebca9660
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="math-error-m6111"></a>Błąd matematyczny M6111
przepełnienie stosu  
  
 Operacja zmiennoprzecinkowa spowodowała przepełnienie stosu w Koprocesor 8087/287/387 lub emulator.  
  
 Ten błąd jest często spowodowane przez wywołanie do `long double` funkcja, która nie zwraca wartości. Na przykład następujące generuje ten błąd podczas skompilowany i uruchom:  
  
```  
long double ld() {};  
main ()  
{  
  ld();  
}  
```  
  
 Program kończy się z kodem zakończenia 139.