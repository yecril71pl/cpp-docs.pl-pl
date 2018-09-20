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
ms.openlocfilehash: 98b61535fd07066c4a1ee24658fdfe81047efc90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446572"
---
# <a name="openmp-environment-variables"></a>Zmienne środowiskowe OpenMP

Zawiera łącza do zmiennych środowiskowych, używany w interfejsie API OpenMP.

Implementacja języka Visual C++ OpenMP standardowa obejmuje następujące zmienne środowiskowe. Te zmienne środowiskowe są odczytywane w momencie uruchamiania programu, a modyfikacji wartości są ignorowane w czasie wykonywania (na przykład za pomocą [_putenv, _wputenv —](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Zmienna środowiskowa|Opis|
|--------------------------|-----------------|
|[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)|Określa, czy OpenMP, w czasie wykonywania można dostosować liczbę wątków w równoległego regionu.|
|[OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md)|Określa, czy zagnieżdżonych równoległości jest włączona, chyba że zagnieżdżone równoległości jest włączone lub wyłączone przy użyciu `omp_set_nested`.|
|[OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)|Ustawia maksymalną liczbę wątków w równoległego regionu, chyba że zostaną zastąpione [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) lub [num_threads](../../../parallel/openmp/reference/num-threads.md).|
|[OMP_SCHEDULE](../../../parallel/openmp/reference/omp-schedule.md)|Modyfikuje zachowanie [harmonogram](../../../parallel/openmp/reference/schedule.md) klauzuli podczas `schedule(runtime)` została określona w `for` lub `parallel for` dyrektywy.|

## <a name="see-also"></a>Zobacz też

[Odwołanie do biblioteki](../../../parallel/openmp/reference/openmp-library-reference.md)