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
ms.openlocfilehash: 838427320fcb68cedb97b36156fc18002ed962d8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143275"
---
# <a name="openmp-environment-variables"></a>Zmienne środowiskowe OpenMP

Oferuje linki do zmiennych środowiskowych używanych w interfejsie API OpenMP.

Wizualna C++ implementacja standardu OpenMP obejmuje następujące zmienne środowiskowe. Te zmienne środowiskowe są odczytywane przy uruchamianiu programu, a modyfikacje w ich wartości są ignorowane w czasie wykonywania (na przykład przy użyciu [_putenv, _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Zmienna środowiskowa|Opis|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|Modyfikuje zachowanie klauzuli [Schedule](openmp-clauses.md#schedule) , gdy `schedule(runtime)` jest określony w dyrektywie `for` lub `parallel for`.|
|[OMP_NUM_THREADS](#omp-num-threads)|Ustawia maksymalną liczbę wątków w regionie równoległym, chyba że zostaną zastąpione przez [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) lub [num_threads](openmp-clauses.md#num-threads).|
|[OMP_DYNAMIC](#omp-dynamic)|Określa, czy czas uruchomienia OpenMP może dostosować liczbę wątków w regionie równoległym.|
|[OMP_NESTED](#omp-nested)|Określa, czy zagnieżdżona równoległość jest włączona, chyba że zagnieżdżone równoległe jest włączone lub wyłączone przy użyciu `omp_set_nested`.|

## <a name="omp-dynamic"></a>OMP_DYNAMIC

Określa, czy czas uruchomienia OpenMP może dostosować liczbę wątków w regionie równoległym.

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>Uwagi

Zmienna środowiskowa `OMP_DYNAMIC` może być zastąpiona przez funkcję [omp_set_dynamic](openmp-functions.md#omp-set-dynamic) .

Wartość domyślna w implementacji wizualizacji C++ w standardzie OpenMP jest `OMP_DYNAMIC=FALSE`.

Aby uzyskać więcej informacji, zobacz [4,3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).

### <a name="example"></a>Przykład

Następujące polecenie ustawia zmienną środowiskową `OMP_DYNAMIC` na TRUE:

```cmd
set OMP_DYNAMIC=TRUE
```

Następujące polecenie wyświetla bieżące ustawienie zmiennej środowiskowej `OMP_DYNAMIC`:

```cmd
set OMP_DYNAMIC
```

## <a name="omp-nested"></a>OMP_NESTED

Określa, czy zagnieżdżona równoległość jest włączona, chyba że zagnieżdżone równoległe jest włączone lub wyłączone przy użyciu `omp_set_nested`.

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>Uwagi

Zmienna środowiskowa `OMP_NESTED` może być zastąpiona przez funkcję [omp_set_nested](openmp-functions.md#omp-set-nested) .

Wartość domyślna w implementacji wizualizacji C++ w standardzie OpenMP jest `OMP_DYNAMIC=FALSE`.

Aby uzyskać więcej informacji, zobacz [4,4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).

### <a name="example"></a>Przykład

Następujące polecenie ustawia zmienną środowiskową `OMP_NESTED` na TRUE:

```cmd
set OMP_NESTED=TRUE
```

Następujące polecenie wyświetla bieżące ustawienie zmiennej środowiskowej `OMP_NESTED`:

```cmd
set OMP_NESTED
```

## <a name="omp-num-threads"></a>OMP_NUM_THREADS

Ustawia maksymalną liczbę wątków w regionie równoległym, chyba że zostaną zastąpione przez [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) lub [num_threads](openmp-clauses.md#num-threads).

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Parametry

*numerowan*<br/>
Maksymalna liczba wątków w regionie równoległym, do 64 w implementacji wizualizacji C++ .

### <a name="remarks"></a>Uwagi

Zmienna środowiskowa `OMP_NUM_THREADS` może zostać przesłonięta przez funkcję [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) lub [num_threads](openmp-clauses.md#num-threads).

Wartość domyślna `num` w implementacji wizualizacji C++ w standardzie OpenMP to liczba procesorów wirtualnych, w tym procesorów wielowątkowości.

Aby uzyskać więcej informacji, zobacz [4,2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).

### <a name="example"></a>Przykład

Następujące polecenie ustawia zmienną środowiskową `OMP_NUM_THREADS` na `16`:

```cmd
set OMP_NUM_THREADS=16
```

Następujące polecenie wyświetla bieżące ustawienie zmiennej środowiskowej `OMP_NUM_THREADS`:

```cmd
set OMP_NUM_THREADS
```

## <a name="omp-schedule"></a>OMP_SCHEDULE

Modyfikuje zachowanie klauzuli [Schedule](openmp-clauses.md#schedule) , gdy `schedule(runtime)` jest określony w dyrektywie `for` lub `parallel for`.

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>Parametry

*zmienia*<br/>
Obowiązkowe Określa rozmiar iteracji. *rozmiar* musi być dodatnią liczbą całkowitą. Wartość domyślna to `1`, z wyjątkiem sytuacji, gdy *Typ* jest statyczny. Nieprawidłowy, gdy *Typ* jest `runtime`.

*type*<br/>
Rodzaj planowania, `dynamic`, `guided`, `runtime`lub `static`.

### <a name="remarks"></a>Uwagi

Wartość domyślna w implementacji wizualizacji C++ w standardzie OpenMP jest `OMP_SCHEDULE=static,0`.

Aby uzyskać więcej informacji, zobacz [4,1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).

### <a name="example"></a>Przykład

Następujące polecenie ustawia zmienną środowiskową `OMP_SCHEDULE`:

```cmd
set OMP_SCHEDULE="guided,2"
```

Następujące polecenie wyświetla bieżące ustawienie zmiennej środowiskowej `OMP_SCHEDULE`:

```cmd
set OMP_SCHEDULE
```
