---
title: "Przy użyciu blokady A.16 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 873bf32b-6cfe-4ce1-b994-bef80b50f399
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 612abe97de27b179f710b2b09811535829885c5f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="a16---using-locks"></a>A.16   Użycie blokad
W poniższym przykładzie (dla [sekcji 3.2](../../parallel/openmp/3-2-lock-functions.md) na stronie 41) należy pamiętać, że argument do funkcji blokady musi mieć właściwość type `omp_lock_t`, i że nie istnieje potrzeba aby opróżnić go.  Funkcje blokady spowodować wątków ze stanu bezczynności podczas oczekiwania na zapis w pierwszej sekcji krytyczne, ale wykonywać inne zadania podczas oczekiwania na zapis do drugiego.  `omp_set_lock` Funkcja bloków, ale `omp_test_lock` — funkcja nie jest, umożliwiając pracę w skip() do wykonania.  
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Kod  
  
```  
// omp_using_locks.c  
// compile with: /openmp /c  
#include <stdio.h>  
#include <omp.h>  
  
void work(int);  
void skip(int);  
  
int main() {  
   omp_lock_t lck;  
   int id;  
  
   omp_init_lock(&lck);  
   #pragma omp parallel shared(lck) private(id)  
   {  
      id = omp_get_thread_num();  
  
      omp_set_lock(&lck);  
      printf_s("My thread id is %d.\n", id);  
  
      // only one thread at a time can execute this printf  
      omp_unset_lock(&lck);  
  
      while (! omp_test_lock(&lck)) {  
         skip(id);   // we do not yet have the lock,  
                     // so we must do something else   
      }  
      work(id);     // we now have the lock  
                    // and can do the work   
      omp_unset_lock(&lck);  
   }  
   omp_destroy_lock(&lck);  
}  
```