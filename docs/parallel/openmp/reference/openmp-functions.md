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
ms.openlocfilehash: 0475a83ba259ed00bbcb9ddaba99a1556b35f613
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317142"
---
# <a name="openmp-functions"></a>OpenMP — Funkcje

Zawiera łącza do funkcji używanych w interfejsie API OpenMP.

Visual C++ implementacji standardu OpenMP zawiera następujące funkcje i typy danych.

W przypadku wykonywania środowiska:

|Funkcja|Opis|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|Ustawia liczbę wątków w nadchodzących regionach równoległych, chyba że zastąpione przez [num_threads](openmp-clauses.md#num-threads) klauzuli.|
|[omp_get_num_threads](#omp-get-num-threads)|Zwraca liczbę wątków w regionie równoległym.|
|[omp_get_max_threads](#omp-get-max-threads)|Zwraca liczbę całkowitą, która jest równa lub większa niż liczba wątków, które byłyby dostępne, jeśli region równoległy bez [num_threads](openmp-clauses.md#num-threads) zostały zdefiniowane w tym punkcie w kodzie.|
|[omp_get_thread_num](#omp-get-thread-num)|Zwraca numer wątku wykonującego w jego zespole wątku.|
|[omp_get_num_procs](#omp-get-num-procs)|Zwraca liczbę procesorów, które są dostępne, gdy funkcja jest wywoływana.|
|[omp_in_parallel](#omp-in-parallel)|Zwraca wartość niezerową, jeśli jest wywoływana z poziomu regionu równoległego.|
|[omp_set_dynamic](#omp-set-dynamic)|Wskazuje, że liczba wątków dostępnych w nadchodzących regionach równoległych może być dostosowana przez czas wykonywania.|
|[omp_get_dynamic](#omp-get-dynamic)|Zwraca wartość, która wskazuje, czy liczba wątków dostępnych w nadchodzących regionach równoległych może być dostosowana przez czas wykonywania.|
|[omp_set_nested](#omp-set-nested)|Włącza równoległość zagnieżdżoną.|
|[omp_get_nested](#omp-get-nested)|Zwraca wartość, która wskazuje, czy zagnieżdżony równoległość jest włączona.|

Dla zamka:

|Funkcja|Opis|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|Inicjuje prosty zamek.|
|[omp_init_nest_lock](#omp-init-nest-lock)|Inicjuje blokadę.|
|[omp_destroy_lock](#omp-destroy-lock)|Uninitializes blokady.|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|Uninitializes blokady zagnieżdżenia.|
|[omp_set_lock](#omp-set-lock)|Blokuje wykonywanie wątku, dopóki blokada nie jest dostępna.|
|[omp_set_nest_lock](#omp-set-nest-lock)|Blokuje wykonywanie wątku, dopóki blokada nie jest dostępna.|
|[omp_unset_lock](#omp-unset-lock)|Zwalnia blokadę.|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|Zwalnia blokadę zagnieżdżoną.|
|[omp_test_lock](#omp-test-lock)|Próbuje ustawić blokadę, ale nie blokuje wykonywania wątku.|
|[omp_test_nest_lock](#omp-test-nest-lock)|Próbuje ustawić blokadę zagnieżdżoną, ale nie blokuje wykonywania wątku.|

|Typ danych|Opis|
|---------|-----------|
|`omp_lock_t`|Typ, który przechowuje stan blokady, czy blokada jest dostępna lub jeśli wątek jest właścicielem blokady.|
|`omp_nest_lock_t`|Typ, który zawiera jedną z następujących informacji o blokadzie: czy blokada jest dostępna i tożsamość wątku, który jest właścicielem blokady i liczby zagnieżdżenia.|

Dla procedur czasowych:

|Funkcja|Opis|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|Zwraca wartość w sekundach czasu, który upłynął od pewnego punktu.|
|[omp_get_wtick](#omp-get-wtick)|Zwraca liczbę sekund między znacznikami zegara procesora.|

## <a name="omp_destroy_lock"></a><a name="omp-destroy-lock"></a>omp_destroy_lock

Uninitializes blokady.

```cpp
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu, `omp_lock_t` która została zainicjowana za pomocą [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.2 omp_destroy_lock i funkcje omp_destroy_nest_lock](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Przykład

Zobacz [omp_init_lock](#omp-init-lock) na przykład za `omp_destroy_lock`pomocą .

## <a name="omp_destroy_nest_lock"></a><a name="omp-destroy-nest-lock"></a>omp_destroy_nest_lock

Uninitializes blokady zagnieżdżenia.

```cpp
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu, `omp_nest_lock_t` która została zainicjowana za pomocą [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.2 omp_destroy_lock i funkcje omp_destroy_nest_lock](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Przykład

Zobacz [omp_init_nest_lock,](#omp-init-nest-lock) aby uzyskać przykład `omp_destroy_nest_lock`użycia pliku .

## <a name="omp_get_dynamic"></a><a name="omp-get-dynamic"></a>omp_get_dynamic

Zwraca wartość, która wskazuje, czy liczba wątków dostępnych w nadchodzących regionach równoległych może być dostosowana przez czas wykonywania.

```cpp
int omp_get_dynamic();
```

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa oznacza, że wątki będą dostosowywane dynamicznie.

### <a name="remarks"></a>Uwagi

Dynamiczna regulacja wątków jest określona za pomocą [omp_set_dynamic](#omp-set-dynamic) i [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic).

Aby uzyskać więcej informacji, zobacz [3.1.7 omp_set_dynamic funkcji](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Przykład

Zobacz [omp_set_dynamic,](#omp-set-dynamic) aby uzyskać `omp_get_dynamic`przykład użycia pliku .

## <a name="omp_get_max_threads"></a><a name="omp-get-max-threads"></a>omp_get_max_threads

Zwraca liczbę całkowitą, która jest równa lub większa niż liczba wątków, które byłyby dostępne, jeśli region równoległy bez [num_threads](openmp-clauses.md#num-threads) zostały zdefiniowane w tym punkcie w kodzie.

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

## <a name="omp_get_nested"></a><a name="omp-get-nested"></a>omp_get_nested

Zwraca wartość, która wskazuje, czy zagnieżdżony równoległość jest włączona.

```cpp
int omp_get_nested( );
```

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa oznacza, że równoległość zagnieżdżona jest włączona.

### <a name="remarks"></a>Uwagi

Równoległość zagnieżdżona jest określona za pomocą [omp_set_nested](#omp-set-nested) i [OMP_NESTED](openmp-environment-variables.md#omp-nested).

Aby uzyskać więcej informacji, zobacz [3.1.10 omp_get_nested funkcji](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).

### <a name="example"></a>Przykład

Zobacz [omp_set_nested](#omp-set-nested) na przykład użycia `omp_get_nested`pliku .

## <a name="omp_get_num_procs"></a><a name="omp-get-num-procs"></a>omp_get_num_procs

Zwraca liczbę procesorów, które są dostępne, gdy funkcja jest wywoływana.

```cpp
int omp_get_num_procs();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.1.5 omp_get_num_procs funkcji](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md).

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

## <a name="omp_get_num_threads"></a><a name="omp-get-num-threads"></a>omp_get_num_threads

Zwraca liczbę wątków w regionie równoległym.

```cpp
int omp_get_num_threads( );
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.1.2 omp_get_num_threads funkcji](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md).

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

## <a name="omp_get_thread_num"></a><a name="omp-get-thread-num"></a>omp_get_thread_num

Zwraca numer wątku wykonującego w jego zespole wątku.

```cpp
int omp_get_thread_num( );
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.1.4 omp_get_thread_num funkcji](../../../parallel/openmp/3-1-4-omp-get-thread-num-function.md).

### <a name="example"></a>Przykład

Zobacz [równolegle](openmp-directives.md#parallel) na przykład `omp_get_thread_num`za pomocą .

## <a name="omp_get_wtick"></a><a name="omp-get-wtick"></a>omp_get_wtick

Zwraca liczbę sekund między znacznikami zegara procesora.

```cpp
double omp_get_wtick( );
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.3.2 omp_get_wtick funkcji](../../../parallel/openmp/3-3-2-omp-get-wtick-function.md).

### <a name="example"></a>Przykład

Zobacz [omp_get_wtime,](#omp-get-wtime) aby uzyskać przykład `omp_get_wtick`użycia pliku .

## <a name="omp_get_wtime"></a><a name="omp-get-wtime"></a>omp_get_wtime

Zwraca wartość w sekundach czasu, który upłynął od pewnego punktu.

```cpp
double omp_get_wtime( );
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość w sekundach czasu, który upłynął z niektórych dowolnego, ale spójnego punktu.

### <a name="remarks"></a>Uwagi

Ten punkt pozostanie spójny podczas wykonywania programu, dzięki czemu możliwe są nadchodzące porównania.

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

## <a name="omp_in_parallel"></a><a name="omp-in-parallel"></a>omp_in_parallel

Zwraca wartość niezerową, jeśli jest wywoływana z poziomu regionu równoległego.

```cpp
int omp_in_parallel( );
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.1.6 omp_in_parallel funkcji](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md).

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

## <a name="omp_init_lock"></a><a name="omp-init-lock"></a>omp_init_lock

Inicjuje prosty zamek.

```cpp
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu `omp_lock_t`.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.1 omp_init_lock i omp_init_nest_lock funkcje](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

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

## <a name="omp_init_nest_lock"></a><a name="omp-init-nest-lock"></a>omp_init_nest_lock

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

Początkowa liczba zagnieżdżeń wynosi zero.

Aby uzyskać więcej informacji, zobacz [3.2.1 omp_init_lock i omp_init_nest_lock funkcje](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

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

## <a name="omp_set_dynamic"></a><a name="omp-set-dynamic"></a>Omp_set_dynamic

Wskazuje, że liczba wątków dostępnych w nadchodzących regionach równoległych może być dostosowana przez czas wykonywania.

```cpp
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość, która wskazuje, czy liczba wątków dostępnych w nadchodzących regionach równoległych mogą być dostosowane przez środowisko uruchomieniowe. Jeśli nonzero, środowisko wykonawcze można dostosować liczbę wątków, jeśli zero, środowisko wykonawcze nie będzie dynamicznie dostosować liczbę wątków.

### <a name="remarks"></a>Uwagi

Liczba wątków nigdy nie przekroczy wartości ustawionej przez [omp_set_num_threads](#omp-set-num-threads) lub [OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads).

Użyj [omp_get_dynamic,](#omp-get-dynamic) aby wyświetlić `omp_set_dynamic`bieżące ustawienie .

Ustawienie dla `omp_set_dynamic` spowoduje zastąpienie ustawienia zmiennej środowiskowej [OMP_DYNAMIC.](openmp-environment-variables.md#omp-dynamic)

Aby uzyskać więcej informacji, zobacz [3.1.7 omp_set_dynamic funkcji](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

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

## <a name="omp_set_lock"></a><a name="omp-set-lock"></a>omp_set_lock

Blokuje wykonywanie wątku, dopóki blokada nie jest dostępna.

```cpp
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu, `omp_lock_t` która została zainicjowana za pomocą [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.3 omp_set_lock i funkcje omp_set_nest_lock](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Przykłady

Zobacz [omp_init_lock](#omp-init-lock) na przykład za `omp_set_lock`pomocą .

## <a name="omp_set_nest_lock"></a><a name="omp-set-nest-lock"></a>omp_set_nest_lock

Blokuje wykonywanie wątku, dopóki blokada nie jest dostępna.

```cpp
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu, `omp_nest_lock_t` która została zainicjowana za pomocą [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.3 omp_set_lock i funkcje omp_set_nest_lock](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Przykłady

Zobacz [omp_init_nest_lock,](#omp-init-nest-lock) aby uzyskać przykład `omp_set_nest_lock`użycia pliku .

## <a name="omp_set_nested"></a><a name="omp-set-nested"></a>Omp_set_nested

Włącza równoległość zagnieżdżoną.

```cpp
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość niezerowa umożliwia równoległość zagnieżdżoną, podczas gdy zero wyłącza równoległość zagnieżdżoną.

### <a name="remarks"></a>Uwagi

Równoległość zagnieżdżona OMP można włączyć za pomocą `omp_set_nested`lub ustawiając [OMP_NESTED](openmp-environment-variables.md#omp-nested) zmienną środowiskową.

Ustawienie dla `omp_set_nested` spowoduje zastąpienie ustawienia zmiennej środowiskowej. `OMP_NESTED`

Włączenie zmiennej środowiskowej może przerwać program operacyjny w przeciwnym razie, ponieważ liczba wątków zwiększa się wykładniczo podczas zagnieżdżania regionów równoległych. Na przykład funkcja, która powtarza się sześć razy z liczbą wątków OMP ustawionych na 4 wymaga 4096 (4 do potęgi 6) wątków. Z wyjątkiem aplikacji związanych z we/wy wydajność aplikacji zazwyczaj obniża, jeśli istnieje więcej wątków niż procesory.

Użyj [omp_get_nested,](#omp-get-nested) aby wyświetlić bieżące `omp_set_nested`ustawienie .

Aby uzyskać więcej informacji, zobacz [3.1.9 omp_set_nested funkcji](../../../parallel/openmp/3-1-9-omp-set-nested-function.md).

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

## <a name="omp_set_num_threads"></a><a name="omp-set-num-threads"></a>Omp_set_num_threads

Ustawia liczbę wątków w nadchodzących regionach równoległych, chyba że zastąpione przez [num_threads](openmp-clauses.md#num-threads) klauzuli.

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

Zobacz [omp_get_num_threads,](#omp-get-num-threads) aby uzyskać przykład `omp_set_num_threads`użycia pliku .

## <a name="omp_test_lock"></a><a name="omp-test-lock"></a>omp_test_lock

Próbuje ustawić blokadę, ale nie blokuje wykonywania wątku.

```cpp
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu, `omp_lock_t` która została zainicjowana za pomocą [omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.5 omp_test_lock i omp_test_nest_lock funkcje](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

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

## <a name="omp_test_nest_lock"></a><a name="omp-test-nest-lock"></a>omp_test_nest_lock

Próbuje ustawić blokadę zagnieżdżoną, ale nie blokuje wykonywania wątku.

```cpp
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu, `omp_nest_lock_t` która została zainicjowana za pomocą [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.5 omp_test_lock i omp_test_nest_lock funkcje](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

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

## <a name="omp_unset_lock"></a><a name="omp-unset-lock"></a>omp_unset_lock

Zwalnia blokadę.

```cpp
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu, `omp_lock_t` która została zainicjowana za pomocą [omp_init_lock](#omp-init-lock), należącej do wątku i wykonującej w funkcji.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.4 omp_unset_lock i funkcje omp_unset_nest_lock](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Przykład

Zobacz [omp_init_lock](#omp-init-lock) na przykład za `omp_unset_lock`pomocą .

## <a name="omp_unset_nest_lock"></a><a name="omp-unset-nest-lock"></a>omp_unset_nest_lock

Zwalnia blokadę zagnieżdżoną.

```cpp
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu, `omp_nest_lock_t` która została zainicjowana za pomocą [omp_init_nest_lock](#omp-init-nest-lock), należącej do wątku i wykonującej w funkcji.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.4 omp_unset_lock i funkcje omp_unset_nest_lock](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Przykład

Zobacz [omp_init_nest_lock,](#omp-init-nest-lock) aby uzyskać przykład `omp_unset_nest_lock`użycia pliku .
