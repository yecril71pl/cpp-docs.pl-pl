---
title: 3.3.2 funkcja omp_get_wtick | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1ad08500-bcb0-40d9-a81f-f131819006c9
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dc7a67eebfe4cef5f9e5b3806dcd77cb77c32637
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="332-ompgetwtick-function"></a>3.3.2 Funkcja omp_get_wtick
`omp_get_wtick` Funkcja zwraca wartość podwójnej precyzji zmienna punktu równa liczbie sekund między kolejnymi zegarowych. Format jest następujący:  
  
```  
#include <omp.h>  
double omp_get_wtick(void);  
```