---
title: Klauzule OpenMP | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4de0ac69733bee42d4102edf345f69be2e5fea3f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="openmp-clauses"></a>Klauzule OpenMP
Zawiera łącza do klauzule używany w interfejsie API OpenMP.  
  
 Visual C++ obsługuje następujące klauzule OpenMP:  
  
|Klauzula|Opis|  
|------------|-----------------|  
|[copyin](../../../parallel/openmp/reference/copyin.md)|Umożliwia dostęp do wartości wątku głównego wątków do [threadprivate](../../../parallel/openmp/reference/threadprivate.md) zmiennej.|  
|[copyprivate](../../../parallel/openmp/reference/copyprivate.md)|Określa, że co najmniej jedną zmienną powinna być współużytkowane przez wszystkie wątki.|  
|[domyślne](../../../parallel/openmp/reference/default-openmp.md)|Określa zachowanie niewystępującego w zakresie zmiennych równoległego regionu.|  
|[firstprivate](../../../parallel/openmp/reference/firstprivate.md)|Określa, że każdy wątek powinien mieć własne wystąpienie zmiennej i czy zmienna powinien być inicjowany przez wartość zmiennej, ponieważ istnieje przed równoległych konstrukcji.|  
|[Jeśli](../../../parallel/openmp/reference/if-openmp.md)|Określa, czy pętlę powinny być wykonywane równolegle lub kolei.|  
|[lastprivate](../../../parallel/openmp/reference/lastprivate.md)|Określa, że wersja otaczającym kontekście zmiennej jest taki sam, niezależnie od wątku wykonuje końcowego iteracji (konstrukcji pętli for) lub ostatniej sekcji (#pragma sekcje) wersji prywatnej.|  
|[NOWAIT](../../../parallel/openmp/reference/nowait.md)|Zastępuje bariery niejawne w dyrektywie.|  
|[num_threads](../../../parallel/openmp/reference/num-threads.md)|Ustawia liczbę wątków w zespole wątku.|  
|[uporządkowane](../../../parallel/openmp/reference/ordered-openmp-clauses.md)|Wymagane na równoległego [dla](../../../parallel/openmp/reference/for-openmp.md) instrukcji Jeśli [uporządkowane](../../../parallel/openmp/reference/ordered-openmp-directives.md) dyrektywy ma być używana w pętli.|  
|[prywatne](../../../parallel/openmp/reference/private-openmp.md)|Określa, że każdy wątek powinien mieć własne wystąpienie zmiennej.|  
|[redukcja](../../../parallel/openmp/reference/reduction.md)|Określa jeden lub więcej zmiennych, które są prywatne, aby każdy wątek podlegają operacji zmniejszenia na końcu równoległego regionu.|  
|[Harmonogram](../../../parallel/openmp/reference/schedule.md)|Dotyczy [dla](../../../parallel/openmp/reference/for-openmp.md) dyrektywy.|  
|[udostępnione](../../../parallel/openmp/reference/shared-openmp.md)|Określa, że co najmniej jedną zmienną powinna być współużytkowane przez wszystkie wątki.|  
  
## <a name="see-also"></a>Zobacz też  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Dyrektywy](../../../parallel/openmp/reference/openmp-directives.md)