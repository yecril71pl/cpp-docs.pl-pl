---
title: OpenMP — Funkcje
ms.date: 03/20/2019
f1_keywords:
- OpenMP functions
- omp_destroy_lock
- omp_destroy_nest_lock
- omp_get_dynamic
- omp_get_max_threads
- omp_get_nested
- omp_get_num_procs
- omp_get_num_threads
- omp_get_thread_num
- omp_get_wtick
- omp_get_wtime
- omp_in_parallel
- omp_init_lock
- omp_init_nest_lock
- omp_set_dynamic
- omp_set_lock
- omp_set_nest_lock
- omp_set_nested
- omp_set_num_threads
- omp_test_lock
- omp_test_nest_lock
- omp_unset_lock
- omp_unset_nest_lock
helpviewer_keywords:
- OpenMP functions
- omp_destroy_lock OpenMP function
- omp_destroy_nest_lock OpenMP function
- omp_get_dynamic OpenMP function
- omp_get_max_threads OpenMP function
- omp_get_nested OpenMP function
- omp_get_num_procs OpenMP function
- omp_get_num_threads OpenMP function
- omp_get_thread_num OpenMP function
- omp_get_wtick OpenMP function
- omp_get_wtime OpenMP function
- omp_in_parallel OpenMP function
- omp_init_lock OpenMP function
- omp_init_nest_lock OpenMP function
- omp_set_dynamic OpenMP function
- omp_set_lock OpenMP function
- omp_set_nest_lock OpenMP function
- omp_set_nested OpenMP function
- omp_set_num_threads OpenMP function
- omp_test_lock OpenMP function
- omp_test_nest_lock OpenMP function
- omp_unset_lock OpenMP function
- omp_unset_nest_lock OpenMP function
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
ms.openlocfilehash: 4508c683ff5d4bece290b7fef2bbd83ae8023eac
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882917"
---
# <a name="openmp-functions"></a>OpenMP — Funkcje

Zawiera łącza do funkcji używanych w interfejsie API OpenMP.

Wizualna C++ implementacja standardu OpenMP obejmuje następujące funkcje i typy danych.

W przypadku wykonywania środowiska:

|Funkcja|Opis|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|Ustawia liczbę wątków w nadchodzących regionach równoległych, chyba że zostanie zastąpiona klauzulą [num_threads](openmp-clauses.md#num-threads) .|
|[omp_get_num_threads](#omp-get-num-threads)|Zwraca liczbę wątków w regionie równoległym.|
|[omp_get_max_threads](#omp-get-max-threads)|Zwraca liczbę całkowitą, która jest równa lub większa od liczby wątków, które byłyby dostępne, jeśli region równoległy bez [num_threads](openmp-clauses.md#num-threads) został zdefiniowany w tym momencie w kodzie.|
|[omp_get_thread_num](#omp-get-thread-num)|Zwraca numer wątku wykonywany w ramach jego zespołu wątków.|
|[omp_get_num_procs](#omp-get-num-procs)|Zwraca liczbę procesorów, które są dostępne w przypadku wywołania funkcji.|
|[omp_in_parallel](#omp-in-parallel)|Zwraca wartość różną od zera, jeśli jest wywoływana z poziomu równoległego regionu.|
|[omp_set_dynamic](#omp-set-dynamic)|Wskazuje, że liczba wątków dostępnych w nadchodzących regionach równoległych może zostać ustawiona przez czas wykonywania.|
|[omp_get_dynamic](#omp-get-dynamic)|Zwraca wartość wskazującą, czy liczba wątków dostępnych w nadchodzących regionach równoległych może zostać skorygowana przez czas wykonywania.|
|[omp_set_nested](#omp-set-nested)|Włącza zagnieżdżoną równoległość.|
|[omp_get_nested](#omp-get-nested)|Zwraca wartość wskazującą, czy włączono zagnieżdżoną równoległość.|

W przypadku blokady:

|Funkcja|Opis|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|Inicjuje prostą blokadę.|
|[omp_init_nest_lock](#omp-init-nest-lock)|Inicjuje blokadę.|
|[omp_destroy_lock](#omp-destroy-lock)|Odinicjuje blokadę.|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|Odinicjuje blokadę zagnieżdżenia.|
|[omp_set_lock](#omp-set-lock)|Blokuje wykonywanie wątków do momentu udostępnienia blokady.|
|[omp_set_nest_lock](#omp-set-nest-lock)|Blokuje wykonywanie wątków do momentu udostępnienia blokady.|
|[omp_unset_lock](#omp-unset-lock)|Zwalnia blokadę.|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|Zwalnia blokadę zagnieżdżenia.|
|[omp_test_lock](#omp-test-lock)|Próbuje ustawić blokadę, ale nie blokuje wykonywania wątku.|
|[omp_test_nest_lock](#omp-test-nest-lock)|Próbuje ustawić blokadę zagnieżdżenia, ale nie blokuje wykonywania wątku.|

|Typ danych|Opis|
|---------|-----------|
|`omp_lock_t`|Typ, który przechowuje stan blokady, niezależnie od tego, czy jest dostępna blokada, czy wątek jest zablokowany.|
|`omp_nest_lock_t`|Typ, który zawiera jedną z następujących informacji o blokadzie: czy blokada jest dostępna i tożsamość wątku będącego właścicielem blokady i liczby zagnieżdżenia.|

Dla procedur chronometrażu:

|Funkcja|Opis|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|Zwraca wartość (w sekundach) czasu, który upłynął od pewnego momentu.|
|[omp_get_wtick](#omp-get-wtick)|Zwraca liczbę sekund między taktami zegara procesora.|

## <a name="omp-destroy-lock"></a>omp_destroy_lock

Odinicjuje blokadę.

```cpp
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu `omp_lock_t`, która została zainicjowana z [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.2 omp_destroy_lock i omp_destroy_nest_lock Functions](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Przykład

Zobacz [omp_init_lock](#omp-init-lock) , aby zapoznać się z przykładem `omp_destroy_lock`.

## <a name="omp-destroy-nest-lock"></a>omp_destroy_nest_lock

Odinicjuje blokadę zagnieżdżenia.

```cpp
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu `omp_nest_lock_t`, która została zainicjowana z [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.2 omp_destroy_lock i omp_destroy_nest_lock Functions](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Przykład

Zobacz [omp_init_nest_lock](#omp-init-nest-lock) , aby zapoznać się z przykładem `omp_destroy_nest_lock`.

## <a name="omp-get-dynamic"></a>omp_get_dynamic

Zwraca wartość wskazującą, czy liczba wątków dostępnych w nadchodzących regionach równoległych może zostać skorygowana przez czas wykonywania.

```cpp
int omp_get_dynamic();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera oznacza, że wątki będą dynamicznie dostosowywane.

### <a name="remarks"></a>Uwagi

Dynamiczne dopasowanie wątków jest określane przy użyciu [omp_set_dynamic](#omp-set-dynamic) i [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic).

Aby uzyskać więcej informacji, zobacz [3.1.7 omp_set_dynamic Function](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Przykład

Zobacz [omp_set_dynamic](#omp-set-dynamic) , aby zapoznać się z przykładem `omp_get_dynamic`.

## <a name="omp-get-max-threads"></a>omp_get_max_threads

Zwraca liczbę całkowitą, która jest równa lub większa od liczby wątków, które byłyby dostępne, jeśli region równoległy bez [num_threads](openmp-clauses.md#num-threads) został zdefiniowany w tym momencie w kodzie.

```cpp
int omp_get_max_threads( )
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.1.3 omp_get_max_threads funkcji](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md).

### <a name="example"></a>Przykład

```cpp
// omp_get_max_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(8);
    printf_s("%d\n", omp_get_max_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));
}
```

```Output
8
8
8
8
8
```

## <a name="omp-get-nested"></a>omp_get_nested

Zwraca wartość wskazującą, czy włączono zagnieżdżoną równoległość.

```cpp
int omp_get_nested( );
```

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera oznacza, że zagnieżdżona równoległość jest włączona.

### <a name="remarks"></a>Uwagi

Zagnieżdżony równoległy jest określany przy użyciu [omp_set_nested](#omp-set-nested) i [OMP_NESTED](openmp-environment-variables.md#omp-nested).

Aby uzyskać więcej informacji, zobacz [3.1.10 omp_get_nested Function](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).

### <a name="example"></a>Przykład

Zobacz [omp_set_nested](#omp-set-nested) , aby zapoznać się z przykładem `omp_get_nested`.

## <a name="omp-get-num-procs"></a>omp_get_num_procs

Zwraca liczbę procesorów, które są dostępne w przypadku wywołania funkcji.

```cpp
int omp_get_num_procs();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Funkcja 3.1.5 omp_get_num_procs](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md).

### <a name="example"></a>Przykład

```cpp
// omp_get_num_procs.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    printf_s("%d\n", omp_get_num_procs( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_procs( ));
        }
}
```

```Output
// Expect the following output when the example is run on a two-processor machine:
2
2
```

## <a name="omp-get-num-threads"></a>omp_get_num_threads

Zwraca liczbę wątków w regionie równoległym.

```cpp
int omp_get_num_threads( );
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.1.2 omp_get_num_threads Function](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md).

### <a name="example"></a>Przykład

```cpp
// omp_get_num_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_num_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));
}
```

```Output
1
4
1
3
1
```

## <a name="omp-get-thread-num"></a>omp_get_thread_num

Zwraca numer wątku wykonywany w ramach jego zespołu wątków.

```cpp
int omp_get_thread_num( );
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.1.4 omp_get_thread_num funkcji](../../../parallel/openmp/3-1-4-omp-get-thread-num-function.md).

### <a name="example"></a>Przykład

Zobacz [Parallel](openmp-directives.md#parallel) , aby zapoznać się z przykładem użycia `omp_get_thread_num`.

## <a name="omp-get-wtick"></a>omp_get_wtick

Zwraca liczbę sekund między taktami zegara procesora.

```cpp
double omp_get_wtick( );
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.3.2 omp_get_wtick Function](../../../parallel/openmp/3-3-2-omp-get-wtick-function.md).

### <a name="example"></a>Przykład

Zobacz [omp_get_wtime](#omp-get-wtime) , aby zapoznać się z przykładem `omp_get_wtick`.

## <a name="omp-get-wtime"></a>omp_get_wtime

Zwraca wartość (w sekundach) czasu, który upłynął od pewnego momentu.

```cpp
double omp_get_wtime( );
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość (w sekundach) czasu, który upłynął od dowolnego dowolnego elementu, ale spójnego punktu.

### <a name="remarks"></a>Uwagi

Ten punkt pozostanie spójny podczas wykonywania programu, co pozwala na dalsze porównania.

Aby uzyskać więcej informacji, zobacz [3.3.1 omp_get_wtime funkcji](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md).

### <a name="example"></a>Przykład

```cpp
// omp_get_wtime.cpp
// compile with: /openmp
#include "omp.h"
#include <stdio.h>
#include <windows.h>

int main() {
    double start = omp_get_wtime( );
    Sleep(1000);
    double end = omp_get_wtime( );
    double wtick = omp_get_wtick( );

    printf_s("start = %.16g\nend = %.16g\ndiff = %.16g\n",
             start, end, end - start);

    printf_s("wtick = %.16g\n1/wtick = %.16g\n",
             wtick, 1.0 / wtick);
}
```

```Output
start = 594255.3671159324
end = 594256.3664474116
diff = 0.9993314791936427
wtick = 2.793651148400146e-007
1/wtick = 3579545
```

## <a name="omp-in-parallel"></a>omp_in_parallel

Zwraca wartość różną od zera, jeśli jest wywoływana z poziomu równoległego regionu.

```cpp
int omp_in_parallel( );
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.1.6 omp_in_parallel Function](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md).

### <a name="example"></a>Przykład

```cpp
// omp_in_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_in_parallel( ));

    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_in_parallel( ));
        }
}
```

```Output
0
1
```

## <a name="omp-init-lock"></a>omp_init_lock

Inicjuje prostą blokadę.

```cpp
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu `omp_lock_t`.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.1 omp_init_lock i omp_init_nest_lock Functions](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

### <a name="example"></a>Przykład

```cpp
// omp_init_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t my_lock;

int main() {
   omp_init_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num( );
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_lock(&my_lock);
         printf_s("Thread %d - starting locked region\n", tid);
         printf_s("Thread %d - ending locked region\n", tid);
         omp_unset_lock(&my_lock);
      }
   }

   omp_destroy_lock(&my_lock);
}
```

```Output
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
```

## <a name="omp-init-nest-lock"></a>omp_init_nest_lock

Inicjuje blokadę.

```cpp
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu `omp_nest_lock_t`.

### <a name="remarks"></a>Uwagi

Początkowa liczba zagnieżdżenia to zero.

Aby uzyskać więcej informacji, zobacz [3.2.1 omp_init_lock i omp_init_nest_lock Functions](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

### <a name="example"></a>Przykład

```cpp
// omp_init_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t my_lock;

void Test() {
   int tid = omp_get_thread_num( );
   omp_set_nest_lock(&my_lock);
   printf_s("Thread %d - starting nested locked region\n", tid);
   printf_s("Thread %d - ending nested locked region\n", tid);
   omp_unset_nest_lock(&my_lock);
}

int main() {
   omp_init_nest_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_nest_lock(&my_lock);
            if (i % 3)
               Test();
            omp_unset_nest_lock(&my_lock);
        }
    }

    omp_destroy_nest_lock(&my_lock);
}
```

```Output
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
```

## <a name="omp-set-dynamic"></a>omp_set_dynamic

Wskazuje, że liczba wątków dostępnych w nadchodzących regionach równoległych może zostać ustawiona przez czas wykonywania.

```cpp
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>Parametry

*użyte*<br/>
Wartość wskazująca, czy liczba wątków dostępnych w nadchodzących regionach równoległych może być dostosowywana przez środowisko uruchomieniowe. Jeśli wartość jest różna od zera, środowisko uruchomieniowe może dostosować liczbę wątków, a jeśli zero, środowisko uruchomieniowe nie dostosowuje dynamicznie liczby wątków.

### <a name="remarks"></a>Uwagi

Liczba wątków nigdy nie będzie przekraczać wartości ustawionej przez [omp_set_num_threads](#omp-set-num-threads) lub [OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads).

Użyj [omp_get_dynamic](#omp-get-dynamic) , aby wyświetlić bieżące ustawienie `omp_set_dynamic`.

Ustawienie `omp_set_dynamic` spowoduje zastąpienie ustawienia zmiennej środowiskowej [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic) .

Aby uzyskać więcej informacji, zobacz [3.1.7 omp_set_dynamic Function](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Przykład

```cpp
// omp_set_dynamic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_dynamic(9);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_dynamic( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_dynamic( ));
        }
}
```

```Output
1
1
```

## <a name="omp-set-lock"></a>omp_set_lock

Blokuje wykonywanie wątków do momentu udostępnienia blokady.

```cpp
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu `omp_lock_t`, która została zainicjowana z [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.3 omp_set_lock i omp_set_nest_lock funkcje](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Przykłady

Zobacz [omp_init_lock](#omp-init-lock) , aby zapoznać się z przykładem `omp_set_lock`.

## <a name="omp-set-nest-lock"></a>omp_set_nest_lock

Blokuje wykonywanie wątków do momentu udostępnienia blokady.

```cpp
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu `omp_nest_lock_t`, która została zainicjowana z [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.3 omp_set_lock i omp_set_nest_lock funkcje](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Przykłady

Zobacz [omp_init_nest_lock](#omp-init-nest-lock) , aby zapoznać się z przykładem `omp_set_nest_lock`.

## <a name="omp-set-nested"></a>omp_set_nested

Włącza zagnieżdżoną równoległość.

```cpp
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>Parametry

*użyte*<br/>
Wartość różna od zera włącza zagnieżdżoną równoległość, natomiast zero wyłącza zagnieżdżoną równoległość.

### <a name="remarks"></a>Uwagi

Zagnieżdżoną równoległość OMP można włączyć przy użyciu `omp_set_nested`lub przez ustawienie zmiennej środowiskowej [OMP_NESTED](openmp-environment-variables.md#omp-nested) .

Ustawienie `omp_set_nested` spowoduje zastąpienie ustawienia zmiennej środowiskowej `OMP_NESTED`.

Włączenie zmiennej środowiskowej może spowodować przerwanie działania programu działającego w inny sposób, ponieważ liczba wątków rośnie wykładniczo podczas zagnieżdżania regionów równoległych. Na przykład funkcja, która powtarza się sześć razy z liczbą OMP wątków ustawionym na 4, wymaga 4 096 (4 do potęgi 6) wątków. W przypadku aplikacji z ograniczeniami we/wy wydajność aplikacji zazwyczaj zmniejsza się, jeśli jest więcej wątków niż procesory.

Użyj [omp_get_nested](#omp-get-nested) , aby wyświetlić bieżące ustawienie `omp_set_nested`.

Aby uzyskać więcej informacji, zobacz [3.1.9 omp_set_nested Function](../../../parallel/openmp/3-1-9-omp-set-nested-function.md).

### <a name="example"></a>Przykład

```cpp
// omp_set_nested.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_nested(1);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_nested( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_nested( ));
        }
}
```

```Output
1
1
```

## <a name="omp-set-num-threads"></a>omp_set_num_threads

Ustawia liczbę wątków w nadchodzących regionach równoległych, chyba że zostanie zastąpiona klauzulą [num_threads](openmp-clauses.md#num-threads) .

```cpp
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>Parametry

*num_threads*<br/>
Liczba wątków w regionie równoległym.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.1.1 omp_set_num_threads funkcji](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).

### <a name="example"></a>Przykład

Zobacz [omp_get_num_threads](#omp-get-num-threads) , aby zapoznać się z przykładem `omp_set_num_threads`.

## <a name="omp-test-lock"></a>omp_test_lock

Próbuje ustawić blokadę, ale nie blokuje wykonywania wątku.

```cpp
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu `omp_lock_t`, która została zainicjowana z [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz sekcję [3.2.5 omp_test_lock i omp_test_nest_lock](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

### <a name="example"></a>Przykład

```cpp
// omp_test_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t simple_lock;

int main() {
    omp_init_lock(&simple_lock);

    #pragma omp parallel num_threads(4)
    {
        int tid = omp_get_thread_num();

        while (!omp_test_lock(&simple_lock))
            printf_s("Thread %d - failed to acquire simple_lock\n",
                     tid);

        printf_s("Thread %d - acquired simple_lock\n", tid);

        printf_s("Thread %d - released simple_lock\n", tid);
        omp_unset_lock(&simple_lock);
    }

    omp_destroy_lock(&simple_lock);
}
```

```Output
Thread 1 - acquired simple_lock
Thread 1 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - acquired simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - acquired simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - released simple_lock
Thread 3 - failed to acquire simple_lock
Thread 3 - acquired simple_lock
Thread 3 - released simple_lock
```

## <a name="omp-test-nest-lock"></a>omp_test_nest_lock

Próbuje ustawić blokadę zagnieżdżenia, ale nie blokuje wykonywania wątku.

```cpp
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu `omp_nest_lock_t`, która została zainicjowana z [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz sekcję [3.2.5 omp_test_lock i omp_test_nest_lock](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

### <a name="example"></a>Przykład

```cpp
// omp_test_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t nestable_lock;

int main() {
   omp_init_nest_lock(&nestable_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num();
      while (!omp_test_nest_lock(&nestable_lock))
         printf_s("Thread %d - failed to acquire nestable_lock\n",
                tid);

      printf_s("Thread %d - acquired nestable_lock\n", tid);

      if (omp_test_nest_lock(&nestable_lock)) {
         printf_s("Thread %d - acquired nestable_lock again\n",
                tid);
         printf_s("Thread %d - released nestable_lock\n",
                tid);
         omp_unset_nest_lock(&nestable_lock);
      }

      printf_s("Thread %d - released nestable_lock\n", tid);
      omp_unset_nest_lock(&nestable_lock);
   }

   omp_destroy_nest_lock(&nestable_lock);
}
```

```Output
Thread 1 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock again
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - acquired nestable_lock
Thread 2 - acquired nestable_lock again
Thread 2 - released nestable_lock
Thread 2 - released nestable_lock
```

## <a name="omp-unset-lock"></a>omp_unset_lock

Zwalnia blokadę.

```cpp
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu `omp_lock_t`, która została zainicjowana przy użyciu [omp_init_lock](#omp-init-lock), należących do wątku i wykonywanych w funkcji.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.4 omp_unset_lock i omp_unset_nest_lock Functions](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Przykład

Zobacz [omp_init_lock](#omp-init-lock) , aby zapoznać się z przykładem `omp_unset_lock`.

## <a name="omp-unset-nest-lock"></a>omp_unset_nest_lock

Zwalnia blokadę zagnieżdżenia.

```cpp
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu `omp_nest_lock_t`, która została zainicjowana przy użyciu [omp_init_nest_lock](#omp-init-nest-lock), należących do wątku i wykonywanych w funkcji.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.4 omp_unset_lock i omp_unset_nest_lock Functions](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Przykład

Zobacz [omp_init_nest_lock](#omp-init-nest-lock) , aby zapoznać się z przykładem `omp_unset_nest_lock`.
