---
title: 3.1.9 funkcja omp_set_nested | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e4afc3aa-bb96-4314-9849-fd5df5f437d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df08d6eb1a93ff5852c239757d5f917e9777919b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687286"
---
# <a name="319-ompsetnested-function"></a>3.1.9 Funkcja omp_set_nested
**Omp_set_nested** funkcja włącza lub wyłącza równoległości zagnieżdżonych. Format jest następujący:  
  
```  
#include <omp.h>  
void omp_set_nested(int nested);  
```  
  
 Jeśli *zagnieżdżonych* daje w wyniku 0 zagnieżdżone równoległości jest wyłączone, co jest ustawieniem domyślnym i zagnieżdżone regiony równoległe są serializowane i wykonywane przez bieżący wątek. Jeśli *zagnieżdżonych* ocenia na wartość niezerową zagnieżdżonych równoległości jest włączona i równoległych regionów, które są zagnieżdżone może wdrożyć dodatkowe wątki do tworzenia zespołów zagnieżdżonych.  
  
 Ta funkcja ma wpływ opisane powyżej, gdy wywoływana z części programu gdzie **omp_in_parallel** funkcja zwraca wartość zero. Jeśli jest ona wywoływana z części program gdzie **omp_in_parallel** funkcja zwraca wartość niezerową, działanie tej funkcji jest niezdefiniowany.  
  
 To wywołanie ma pierwszeństwo przed **OMP_NESTED** zmiennej środowiskowej.  
  
 Po włączeniu zagnieżdżonych równoległości liczbę wątków używanych do wykonania zagnieżdżonych regionów równoległe jest zdefiniowane w implementacji. W związku z tym zgodne OpenMP implementacje mogą serializować zagnieżdżonych równoległych regionów, nawet wtedy, gdy włączono równoległości zagnieżdżonych.  
  
## <a name="cross-references"></a>Odsyłacze:  
  
-   **OMP_NESTED** środowiska zmiennych, zobacz [4.4 sekcji](../../parallel/openmp/4-4-omp-nested.md) na stronie 49.  
  
-   **omp_in_parallel** funkcji, zobacz [sekcji 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) na stronie 38.