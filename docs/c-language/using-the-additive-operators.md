---
title: "Używanie dodatkowych operatorów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94e2a63412e4fecd5f358659cc4bf02f90df57ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-the-additive-operators"></a>Używanie dodatkowych operatorów
Poniższe przykłady, które przedstawiają operatorów dodawania i odejmowania, użyj deklaracji:  
  
```  
int i = 4, j;  
float x[10];  
float *px;  
```  
  
 Te instrukcje są równoważne:  
  
```  
px = &x[4 + i];  
px = &x[4] + i;    
```  
  
 Wartość `i` jest mnożona przez długości **float** i dodane do `&x[4]`. Wynikowa wartość wskaźnika jest adresem `x[8]`.  
  
```  
j = &x[i] - &x[i-2];  
```  
  
 W tym przykładzie adres trzeci element `x` (podana przez `x[i-2]`) jest odejmowany od adresu elementu piątego `x` (podana przez `x[i]`). Różnica jest podzielona przez długość **float**; wynik jest wartością całkowitą 2.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory dodawania języka C](../c-language/c-additive-operators.md)