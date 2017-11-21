---
title: 3.1.7 funkcja omp_set_dynamic | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1fba961b-b82c-4a1e-ab0f-e4be826e50ab
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1569235e807fb8e6981c45d7547cae7bd6f70c56
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="317-ompsetdynamic-function"></a>3.1.7 Funkcja omp_set_dynamic
**Omp_set_dynamic** funkcja włącza lub wyłącza dynamiczne Dostosowywanie liczba wątków dostępnych do wykonywania równoległego regionów. Format jest następujący:  
  
```  
#include <omp.h>  
void omp_set_dynamic(int dynamic_threads);  
```  
  
 Jeśli *dynamic_threads* ocenia na wartość niezerową liczbę wątków, które są używane do wykonywania kolejnych regionach równoległe mogą być automatycznie dostosowane przez środowisko wykonawcze najlepiej wykorzystać zasoby systemowe. W rezultacie to liczba wątków określone przez użytkownika jest maksymalnej liczby wątków. Liczba wątków w zespole wykonywania równoległego regionu pozostaje stały czas trwania tego równoległego regionu i został zgłoszony przez **omp_get_num_threads** funkcji.  
  
 Jeśli *dynamic_threads* ocenia 0, dynamiczne Dostosowywanie jest wyłączona.  
  
 Ta funkcja ma wpływ opisane powyżej, gdy wywoływana z części programu gdzie **omp_in_parallel** funkcja zwraca wartość zero. Jeśli jest ona wywoływana z części program gdzie **omp_in_parallel** funkcja zwraca wartość niezerową, działanie tej funkcji jest niezdefiniowany.  
  
 Wywołanie **omp_set_dynamic** ma pierwszeństwo przed **OMP_DYNAMIC** zmiennej środowiskowej.  
  
 Wartość domyślna dynamiczne Dostosowywanie wątków jest zdefiniowane w implementacji. W związku z tym kody użytkownika, które są zależne od określonej liczby wątków wykonywania poprawne jawnie Wyłącz dynamiczne wątków. Implementacje nie są wymagane, aby zapewnić możliwość dynamicznie Dostosuj liczbę wątków, ale są one wymagane do interfejsu w celu obsługi przenośność na wszystkich platformach.  
  
## <a name="cross-references"></a>Odsyłacze:  
  
-   **omp_get_num_threads** funkcji, zobacz [sekcji 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stronie 37.  
  
-   **OMP_DYNAMIC** środowiska zmiennych, zobacz [4.3 sekcji](../../parallel/openmp/4-3-omp-dynamic.md) na stronie 49.  
  
-   **omp_in_parallel** funkcji, zobacz [sekcji 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) na stronie 38.