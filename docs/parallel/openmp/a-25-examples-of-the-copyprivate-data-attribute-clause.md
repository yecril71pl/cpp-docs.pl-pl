---
title: "Przykłady A.25 copyprivate klauzuli atrybutu danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 7b1cb6a5-5691-4b95-b3ac-d7543ede6405
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d141ec66aa7ed0bac53c8242a87d08e092272eaa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="a25---examples-of-the-copyprivate-data-attribute-clause"></a>A.25   Przykłady klauzuli atrybutu danych prywatnej kopii
**Przykład 1:** `copyprivate` klauzuli ([sekcji 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) na stronie 32) może służyć do emisji wartości uzyskaną przez pojedynczy wątek bezpośrednio do wszystkich wystąpień zmiennych prywatnych w innych wątków.  
  
```  
float x, y;  
#pragma omp threadprivate(x, y)  
  
void init( )   
{  
    float a;  
    float b;  
  
    #pragma omp single copyprivate(a,b,x,y)  
    {  
        get_values(a,b,x,y);  
    }  
  
    use_values(a, b, x, y);  
}  
```  
  
 W przypadku rutynowych *init* jest wywoływana z obszarem serial jego zachowanie nie ma wpływu na obecność dyrektywy. Po wywołaniu *get_values* procedury zostało wykonane przez jeden wątek, żadnego wątku pozostawia konstrukcja do prywatnego obiekty wskazywany przez *a*, *b*, *x*, i *y* w wszystkie wątki zdefiniowano stają się przy użyciu wartości do odczytu.  
  
 **Przykład 2:** inaczej niż w poprzednim przykładzie załóżmy, że odczytu musi zostać wykonana przez wątek określonego powiedz głównego wątku. W takim przypadku `copyprivate` nie można użyć klauzuli bezpośrednio do emisji, ale może służyć do zapewnienia dostępu do tymczasowego obiektu współużytkowanego.  
  
```  
float read_next( )   
{  
    float * tmp;  
    float return_val;  
  
    #pragma omp single copyprivate(tmp)  
    {  
        tmp = (float *) malloc(sizeof(float));  
    }  
  
    #pragma omp master  
    {  
        get_float( tmp );  
    }  
  
    #pragma omp barrier  
    return_val = *tmp;  
    #pragma omp barrier  
  
    #pragma omp single  
    {  
       free(tmp);  
    }  
  
    return return_val;  
}  
```  
  
 **Przykład 3:** Załóżmy, że liczba obiektów blokady wymagane w ramach równoległego regionu łatwo nie można ustalić przed wprowadzić go. `copyprivate` Klauzuli może służyć do zapewnienia dostępu do obiektów blokady współużytkowanej, które są przydzielane w ramach równoległego regionu.  
  
```  
#include <omp.h>  
  
omp_lock_t *new_lock()  
{  
    omp_lock_t *lock_ptr;  
  
    #pragma omp single copyprivate(lock_ptr)  
    {  
        lock_ptr = (omp_lock_t *) malloc(sizeof(omp_lock_t));  
        omp_init_lock( lock_ptr );  
    }  
  
    return lock_ptr;  
}  
```