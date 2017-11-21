---
title: A.5 krytyczne Dyrektywa Using | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1ef678b58df9d2c323cdebb61feed52ebbaf607f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="a5---using-the-critical-directive"></a>A.5   Użycie dyrektywy krytycznej
Poniższy przykład zawiera kilka `critical` dyrektywy ([sekcji 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) na stronie 18). Kolejkowanie modelu usuniętej i Praca nad zadania pokazano w przykładzie. Aby zabezpieczyć się przed wiele wątków usuwania tego samego zadania, dequeuing operacji musi być w `critical` sekcji. Ponieważ dwie kolejki w tym przykładzie są niezależne, są chronione przez `critical` dyrektywy o różnych nazwach *xaxis* i *yaxis*.  
  
```  
#pragma omp parallel shared(x, y) private(x_next, y_next)  
{  
    #pragma omp critical ( xaxis )  
        x_next = dequeue(x);  
    work(x_next);  
    #pragma omp critical ( yaxis )  
        y_next = dequeue(y);  
    work(y_next);  
}  
```