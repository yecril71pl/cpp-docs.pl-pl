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
ms.openlocfilehash: 3f9117c531bdf0c5a0c94e0b18a055591f431036
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503752"
---
# <a name="openmp-environment-variables"></a>Zmienne środowiskowe OpenMP

Oferuje linki do zmiennych środowiskowych używanych w interfejsie API OpenMP.

Visual C++ implementacja standardu OpenMP obejmuje następujące zmienne środowiskowe. Te zmienne środowiskowe są odczytywane przy uruchamianiu programu, a modyfikacje w ich wartości są ignorowane w czasie wykonywania (na przykład przy użyciu [_putenv, _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Zmienna środowiskowa|Opis|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|Modyfikuje zachowanie klauzuli [Schedule](openmp-clauses.md#schedule) , gdy `schedule(runtime)` jest określony w `for` `parallel for` dyrektywie lub.|
|[OMP_NUM_THREADS](#omp-num-threads)|Ustawia maksymalną liczbę wątków w regionie równoległym, chyba że zostaną zastąpione przez [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) lub [num_threads](openmp-clauses.md#num-threads).|
|[OMP_DYNAMIC](#omp-dynamic)|Określa, czy czas uruchomienia OpenMP może dostosować liczbę wątków w regionie równoległym.|
|[OMP_NESTED](#omp-nested)|Określa, czy zagnieżdżona równoległość jest włączona, chyba że zagnieżdżone równoległe jest włączone lub wyłączone przy użyciu `omp_set_nested` .|

## <a name="omp_dynamic"></a><a name="omp-dynamic"></a> OMP_DYNAMIC

Określa, czy czas uruchomienia OpenMP może dostosować liczbę wątków w regionie równoległym.

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>Uwagi

`OMP_DYNAMIC`Zmienna środowiskowa może być zastąpiona przez funkcję [omp_set_dynamic](openmp-functions.md#omp-set-dynamic) .

Wartość domyślna w Visual C++ implementacji standardu OpenMP to `OMP_DYNAMIC=FALSE` .

Aby uzyskać więcej informacji, zobacz [4,3 OMP_DYNAMIC](../4-environment-variables.md#43-omp_dynamic).

### <a name="example"></a>Przykład

Następujące polecenie ustawia `OMP_DYNAMIC` zmienną środowiskową na true:

```cmd
set OMP_DYNAMIC=TRUE
```

Następujące polecenie wyświetla bieżące ustawienie `OMP_DYNAMIC` zmiennej środowiskowej:

```cmd
set OMP_DYNAMIC
```

## <a name="omp_nested"></a><a name="omp-nested"></a> OMP_NESTED

Określa, czy zagnieżdżona równoległość jest włączona, chyba że zagnieżdżone równoległe jest włączone lub wyłączone przy użyciu `omp_set_nested` .

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>Uwagi

`OMP_NESTED`Zmienna środowiskowa może być zastąpiona przez funkcję [omp_set_nested](openmp-functions.md#omp-set-nested) .

Wartość domyślna w Visual C++ implementacji standardu OpenMP to `OMP_DYNAMIC=FALSE` .

Aby uzyskać więcej informacji, zobacz [4,4 OMP_NESTED](../4-environment-variables.md#44-omp_nested).

### <a name="example"></a>Przykład

Następujące polecenie ustawia `OMP_NESTED` zmienną środowiskową na true:

```cmd
set OMP_NESTED=TRUE
```

Następujące polecenie wyświetla bieżące ustawienie `OMP_NESTED` zmiennej środowiskowej:

```cmd
set OMP_NESTED
```

## <a name="omp_num_threads"></a><a name="omp-num-threads"></a> OMP_NUM_THREADS

Ustawia maksymalną liczbę wątków w regionie równoległym, chyba że zostaną zastąpione przez [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) lub [num_threads](openmp-clauses.md#num-threads).

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Parametry

*numerowan*<br/>
Maksymalna liczba wątków w regionie równoległym, do 64 w implementacji Visual C++.

### <a name="remarks"></a>Uwagi

`OMP_NUM_THREADS`Zmienna środowiskowa może być zastąpiona przez funkcję [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) lub przez [num_threads](openmp-clauses.md#num-threads).

Wartość domyślna `num` w Visual C++ implementacji standardu OpenMP to liczba procesorów wirtualnych, w tym procesorów wielowątkowości.

Aby uzyskać więcej informacji, zobacz [4,2 OMP_NUM_THREADS](../4-environment-variables.md#42-omp_num_threads).

### <a name="example"></a>Przykład

Następujące polecenie ustawia `OMP_NUM_THREADS` zmienną środowiskową na `16` :

```cmd
set OMP_NUM_THREADS=16
```

Następujące polecenie wyświetla bieżące ustawienie `OMP_NUM_THREADS` zmiennej środowiskowej:

```cmd
set OMP_NUM_THREADS
```

## <a name="omp_schedule"></a><a name="omp-schedule"></a> OMP_SCHEDULE

Modyfikuje zachowanie klauzuli [Schedule](openmp-clauses.md#schedule) , gdy `schedule(runtime)` jest określony w `for` `parallel for` dyrektywie lub.

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>Parametry

*zmienia*<br/>
Obowiązkowe Określa rozmiar iteracji. *rozmiar* musi być dodatnią liczbą całkowitą. Wartość domyślna to `1` , z wyjątkiem sytuacji, gdy *Typ* jest statyczny. Nieprawidłowa, gdy *typem* jest `runtime` .

*Wprowadź*<br/>
Rodzaj planowania,,, `dynamic` `guided` `runtime` lub `static` .

### <a name="remarks"></a>Uwagi

Wartość domyślna w Visual C++ implementacji standardu OpenMP to `OMP_SCHEDULE=static,0` .

Aby uzyskać więcej informacji, zobacz [4,1 OMP_SCHEDULE](../4-environment-variables.md#41-omp_schedule).

### <a name="example"></a>Przykład

Następujące polecenie ustawia `OMP_SCHEDULE` zmienną środowiskową:

```cmd
set OMP_SCHEDULE="guided,2"
```

Następujące polecenie wyświetla bieżące ustawienie `OMP_SCHEDULE` zmiennej środowiskowej:

```cmd
set OMP_SCHEDULE
```
