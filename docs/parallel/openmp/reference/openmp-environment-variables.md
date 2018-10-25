---
title: Zmienne środowiskowe OpenMP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/23/2018
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OpenMP environment variables
- OMP_DYNAMIC
- OMP_NESTED
- OMP_NUM_THREADS
- OMP_SCHEDULE
dev_langs:
- C++
helpviewer_keywords:
- OpenMP environment variables
- OMP_DYNAMIC OpenMP environment variable
- OMP_NESTED OpenMP environment variable
- OMP_NUM_THREADS OpenMP environment variable
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a229aa453b6e40f0da25252f2f8aa1be3d97a729
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074257"
---
# <a name="openmp-environment-variables"></a>Zmienne środowiskowe OpenMP

Zawiera łącza do zmiennych środowiskowych, używany w interfejsie API OpenMP.

Implementacja języka Visual C++ OpenMP standardowa obejmuje następujące zmienne środowiskowe. Te zmienne środowiskowe są odczytywane w momencie uruchamiania programu, a modyfikacji wartości są ignorowane w czasie wykonywania (na przykład za pomocą [_putenv, _wputenv —](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Zmienna środowiskowa|Opis|
|--------------------|-----------|
|[OMP_DYNAMIC](#omp-dynamic)|Określa, czy OpenMP, w czasie wykonywania można dostosować liczbę wątków w równoległego regionu.|
|[OMP_NESTED](#omp-nested)|Określa, czy zagnieżdżonych równoległości jest włączona, chyba że zagnieżdżone równoległości jest włączone lub wyłączone przy użyciu `omp_set_nested`.|
|[OMP_NUM_THREADS](#omp-num-threads)|Ustawia maksymalną liczbę wątków w równoległego regionu, chyba że zostaną zastąpione [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) lub [num_threads](openmp-clauses.md#num-threads).|
|[OMP_SCHEDULE](#omp-schedule)|Modyfikuje zachowanie [harmonogram](openmp-clauses.md#schedule) klauzuli podczas `schedule(runtime)` została określona w `for` lub `parallel for` dyrektywy.|

## <a name="omp-dynamic"></a>OMP_DYNAMIC

Określa, czy OpenMP, w czasie wykonywania można dostosować liczbę wątków w równoległego regionu.

```
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>Uwagi

`OMP_DYNAMIC` Zmiennej środowiskowej, może zostać przesłonięta przez [omp_set_dynamic](openmp-functions.md#omp-set-dynamic) funkcji.

Wartość domyślna w implementacji Visual C++ OpenMP standard to `OMP_DYNAMIC=FALSE`.

Aby uzyskać więcej informacji, zobacz [4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).

### <a name="example"></a>Przykład

Następujące polecenie ustawia `OMP_DYNAMIC` zmiennej środowiskowej na wartość TRUE:

```
set OMP_DYNAMIC=TRUE
```

Następujące polecenie wyświetla bieżące ustawienie `OMP_DYNAMIC` zmienną środowiskową:

```
set OMP_DYNAMIC
```

## <a name="omp-nested"></a>OMP_NESTED

Określa, czy zagnieżdżonych równoległości jest włączona, chyba że zagnieżdżone równoległości jest włączone lub wyłączone przy użyciu `omp_set_nested`.

```
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>Uwagi

`OMP_NESTED` Zmiennej środowiskowej, może zostać przesłonięta przez [omp_set_nested](openmp-functions.md#omp-set-nested) funkcji.

Wartość domyślna w implementacji Visual C++ OpenMP standard to `OMP_DYNAMIC=FALSE`.

Aby uzyskać więcej informacji, zobacz [4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).

### <a name="example"></a>Przykład

Następujące polecenie ustawia `OMP_NESTED` zmiennej środowiskowej na wartość TRUE:

```
set OMP_NESTED=TRUE
```

Następujące polecenie wyświetla bieżące ustawienie `OMP_NESTED` zmienną środowiskową:

```
set OMP_NESTED
```

## <a name="omp-num-threads"></a>OMP_NUM_THREADS

Ustawia maksymalną liczbę wątków w równoległego regionu, chyba że zostaną zastąpione [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) lub [num_threads](openmp-clauses.md#num-threads).

```
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Parametry

*num*<br/>
Maksymalna liczba wątków w równoległego regionu, maksymalnie 64 w implementacji Visual C++.

### <a name="remarks"></a>Uwagi

`OMP_NUM_THREADS` Zmiennej środowiskowej, może zostać przesłonięta przez [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) funkcji lub [num_threads](openmp-clauses.md#num-threads).

Wartość domyślna `num` w programie Visual C++ implementacja standardu OpenMP jest liczba procesorów wirtualnych, w tym procesory CPU wielowątkowość.

Aby uzyskać więcej informacji, zobacz [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).

### <a name="example"></a>Przykład

Następujące polecenie ustawia `OMP_NUM_THREADS` zmiennej środowiskowej 16:

```
set OMP_NUM_THREADS=16
```

Następujące polecenie wyświetla bieżące ustawienie `OMP_NUM_THREADS` zmienną środowiskową:

```
set OMP_NUM_THREADS
```

## <a name="omp-schedule"></a>OMP_SCHEDULE

Modyfikuje zachowanie [harmonogram](openmp-clauses.md#schedule) klauzuli podczas `schedule(runtime)` została określona w `for` lub `parallel for` dyrektywy.

```
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
(Opcjonalnie) Określa rozmiar iteracji. `size` Musi być dodatnią liczbą całkowitą. Wartość domyślna to 1, chyba że `type` jest statyczna. Jeśli `type` jest `runtime`.

*Typ*<br/>
Rodzaj planowania:

- `dynamic`
- `guided`
- `runtime`
- `static`

### <a name="remarks"></a>Uwagi

Wartość domyślna w implementacji Visual C++ OpenMP standard to `OMP_SCHEDULE=static,0`.

Aby uzyskać więcej informacji, zobacz [4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).

### <a name="example"></a>Przykład

Następujące polecenie ustawia `OMP_SCHEDULE` zmienną środowiskową:

```
set OMP_SCHEDULE="guided,2"
```

Następujące polecenie wyświetla bieżące ustawienie `OMP_SCHEDULE` zmienną środowiskową:

```
set OMP_SCHEDULE
```
