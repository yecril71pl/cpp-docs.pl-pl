---
title: Zmienne środowiskowe OpenMP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02248b7725f2a4312f26984c798e7248463d2615
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692311"
---
# <a name="openmp-environment-variables"></a>Zmienne środowiskowe OpenMP
Zawiera łącza do zmiennych środowiskowych w interfejsie API OpenMP.  
  
 Visual C++ stosowania standardowych OpenMP obejmuje następujące zmienne środowiskowe. Te zmienne środowiskowe są odczytywane w momencie uruchamiania programu, a modyfikacji wartości są ignorowane w czasie wykonywania (na przykład za pomocą [_putenv —, _wputenv —](../../../c-runtime-library/reference/putenv-wputenv.md)).  
  
|Zmienna środowiskowa|Opis|  
|--------------------------|-----------------|  
|[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)|Określa, czy OpenMP czas wykonywania można zmienić liczbę wątków w równoległego regionu.|  
|[OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md)|Określa, czy zagnieżdżonych równoległości jest włączone, chyba że zagnieżdżonych równoległości jest włączone lub wyłączone z `omp_set_nested`.|  
|[OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)|Ustawia maksymalną liczbę wątków w równoległego regionu, chyba że zostaną zastąpione [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) lub [num_threads](../../../parallel/openmp/reference/num-threads.md).|  
|[OMP_SCHEDULE](../../../parallel/openmp/reference/omp-schedule.md)|Modyfikuje zachowanie [harmonogram](../../../parallel/openmp/reference/schedule.md) klauzuli podczas `schedule(runtime)` została określona w `for` lub `parallel for` dyrektywy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki](../../../parallel/openmp/reference/openmp-library-reference.md)