---
title: Zmienne środowiskowe OpenMP
ms.date: 03/20/2019
f1_keywords:
- OpenMP environment variables
- OMP_DYNAMIC
- OMP_NESTED
- OMP_NUM_THREADS
- OMP_SCHEDULE
helpviewer_keywords:
- OpenMP environment variables
- OMP_DYNAMIC OpenMP environment variable
- OMP_NESTED OpenMP environment variable
- OMP_NUM_THREADS OpenMP environment variable
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
ms.openlocfilehash: bee9b0fbdf147ee962ff92d0b3b9ff57d4209f84
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363884"
---
# <a name="openmp-environment-variables"></a>Zmienne środowiskowe OpenMP

Zawiera łącza do zmiennych środowiskowych używanych w interfejsie API OpenMP.

Visual C++ implementacji standardu OpenMP zawiera następujące zmienne środowiskowe. Te zmienne środowiskowe są odczytywane podczas uruchamiania programu, a modyfikacje ich wartości są ignorowane w czasie wykonywania (na przykład przy użyciu [_putenv, _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Zmienna środowiskowa|Opis|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|Modyfikuje zachowanie [klauzuli harmonogram,](openmp-clauses.md#schedule) `schedule(runtime)` gdy `for` `parallel for` jest określony w lub dyrektywy.|
|[OMP_NUM_THREADS](#omp-num-threads)|Ustawia maksymalną liczbę wątków w regionie równoległym, chyba że zostaną zastąpione przez [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) lub [num_threads](openmp-clauses.md#num-threads).|
|[OMP_DYNAMIC](#omp-dynamic)|Określa, czy czas wykonywania OpenMP może dostosować liczbę wątków w regionie równoległym.|
|[OMP_NESTED](#omp-nested)|Określa, czy równoległość zagnieżdżona jest włączona, chyba `omp_set_nested`że zagnieżdżony równoległość jest włączona lub wyłączona za pomocą .|

## <a name="omp_dynamic"></a><a name="omp-dynamic"></a>Omp_dynamic

Określa, czy czas wykonywania OpenMP może dostosować liczbę wątków w regionie równoległym.

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>Uwagi

Zmienną środowiskową `OMP_DYNAMIC` można zastąpić funkcją [omp_set_dynamic.](openmp-functions.md#omp-set-dynamic)

Wartością domyślną w implementacji visual c++ `OMP_DYNAMIC=FALSE`standardu OpenMP jest .

Aby uzyskać więcej informacji, zobacz [4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).

### <a name="example"></a>Przykład

Następujące polecenie ustawia `OMP_DYNAMIC` zmienną środowiskową na TRUE:

```cmd
set OMP_DYNAMIC=TRUE
```

Następujące polecenie wyświetla bieżące `OMP_DYNAMIC` ustawienie zmiennej środowiskowej:

```cmd
set OMP_DYNAMIC
```

## <a name="omp_nested"></a><a name="omp-nested"></a>Omp_nested

Określa, czy równoległość zagnieżdżona jest włączona, chyba `omp_set_nested`że zagnieżdżony równoległość jest włączona lub wyłączona za pomocą .

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>Uwagi

Zmienną środowiskową `OMP_NESTED` można zastąpić funkcją [omp_set_nested.](openmp-functions.md#omp-set-nested)

Wartością domyślną w implementacji visual c++ `OMP_DYNAMIC=FALSE`standardu OpenMP jest .

Aby uzyskać więcej informacji, zobacz [4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).

### <a name="example"></a>Przykład

Następujące polecenie ustawia `OMP_NESTED` zmienną środowiskową na TRUE:

```cmd
set OMP_NESTED=TRUE
```

Następujące polecenie wyświetla bieżące `OMP_NESTED` ustawienie zmiennej środowiskowej:

```cmd
set OMP_NESTED
```

## <a name="omp_num_threads"></a><a name="omp-num-threads"></a>Omp_num_threads

Ustawia maksymalną liczbę wątków w regionie równoległym, chyba że zostaną zastąpione przez [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) lub [num_threads](openmp-clauses.md#num-threads).

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Parametry

*num*<br/>
Maksymalna liczba wątków, które mają w regionie równoległym, do 64 w visual C++ implementacji.

### <a name="remarks"></a>Uwagi

Zmienną środowiskową `OMP_NUM_THREADS` można zastąpić funkcją [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) lub [num_threads](openmp-clauses.md#num-threads).

Domyślną `num` wartością w implementacji Visual C++ standardu OpenMP jest liczba procesorów wirtualnych, w tym procesorów hyperthreading.

Aby uzyskać więcej informacji, zobacz [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).

### <a name="example"></a>Przykład

Następujące polecenie ustawia `OMP_NUM_THREADS` zmienną `16`środowiskową na:

```cmd
set OMP_NUM_THREADS=16
```

Następujące polecenie wyświetla bieżące `OMP_NUM_THREADS` ustawienie zmiennej środowiskowej:

```cmd
set OMP_NUM_THREADS
```

## <a name="omp_schedule"></a><a name="omp-schedule"></a>OMP_SCHEDULE

Modyfikuje zachowanie [klauzuli harmonogram,](openmp-clauses.md#schedule) `schedule(runtime)` gdy `for` `parallel for` jest określony w lub dyrektywy.

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
(Opcjonalnie) Określa rozmiar iteracji. *rozmiar* musi być dodatnią liczebnością całkowitą. Wartość domyślna to `1`, z wyjątkiem sytuacji, gdy *typ* jest statyczny. Nieprawidłowe, *type* gdy `runtime`typ jest .

*Typu*<br/>
`dynamic`Rodzaj planowania, albo , `guided`, `runtime`, `static`lub .

### <a name="remarks"></a>Uwagi

Wartością domyślną w implementacji visual c++ `OMP_SCHEDULE=static,0`standardu OpenMP jest .

Aby uzyskać więcej informacji, zobacz [4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).

### <a name="example"></a>Przykład

Następujące polecenie ustawia `OMP_SCHEDULE` zmienną środowiskową:

```cmd
set OMP_SCHEDULE="guided,2"
```

Następujące polecenie wyświetla bieżące `OMP_SCHEDULE` ustawienie zmiennej środowiskowej:

```cmd
set OMP_SCHEDULE
```
