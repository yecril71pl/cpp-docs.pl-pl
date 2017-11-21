---
title: "A.29 podziału Użyj pracy tworzy wewnątrz konstrukcja krytyczna | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: d5c8a83f-2f51-4f23-8ddf-d267e347507f
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2aac51541574ee1cf0363a77f40891ac37a18c49
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="a29---use-of-work-sharing-constructs-inside-a-critical-construct"></a>A.29   Użycie konstrukcji podziału pracy w konstrukcji krytycznej
W poniższym przykładzie pokazano, przy użyciu konstrukcji podziału pracy, wewnątrz `critical` utworzenia. W tym przykładzie jest zgodny, ponieważ podziału pracy tworzenia i `critical` konstrukcja nie powiązać z tym samym regionie równoległych.  
  
```  
void f()  
{  
  int i = 1;  
  #pragma omp parallel sections  
  {  
    #pragma omp section  
    {  
      #pragma omp critical (name)  
      {  
        #pragma omp parallel  
        {  
          #pragma omp single  
          {  
            i++;  
          }  
        }  
      }  
    }  
  }  
}  
```