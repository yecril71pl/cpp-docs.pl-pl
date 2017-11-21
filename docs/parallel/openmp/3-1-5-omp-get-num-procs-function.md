---
title: 3.1.5 funkcja omp_get_num_procs | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: bbfbf17b-0c68-4ba6-a25d-07c36ecb551f
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 48e91bb2e728111cf76649ce89efcf991c794782
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="315-ompgetnumprocs-function"></a>3.1.5 Funkcja omp_get_num_procs
`omp_get_num_procs` Funkcja zwraca liczbę procesorów, które są dostępne dla programu w momencie wywołania funkcji. Format jest następujący:  
  
```  
#include <omp.h>  
int omp_get_num_procs(void);  
```