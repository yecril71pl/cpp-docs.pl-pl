---
title: "Błąd matematyczny M6111 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: M6111
dev_langs: C++
helpviewer_keywords: M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 80bca2ae3462bf67bc017de0f77ce56b4a45994b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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