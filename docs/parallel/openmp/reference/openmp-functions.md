---
title: OpenMP — funkcje
ms.date: 10/23/2018
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
ms.openlocfilehash: 36954115d817f3fef042f063a673976e8ce09c43
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489510"
---
# <a name="openmp-functions"></a>OpenMP — funkcje

Zawiera łącza do funkcji używanych w interfejsie API OpenMP.

Implementacja języka Visual C++ OpenMP standardowa obejmuje następujące funkcje.

|Funkcja|Opis|
|--------|-----------|
|[omp_destroy_lock](#omp-destroy-lock)|Deinicjuje blokadę.|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|Deinicjuje blokadą.|
|[omp_get_dynamic](#omp-get-dynamic)|Zwraca wartość wskazującą, jeśli liczba wątków, które są dostępne w kolejnych regionów równoległych można dostosować w czasie wykonywania.|
|[omp_get_max_threads](#omp-get-max-threads)|Zwraca liczbę całkowitą, która jest równa lub większa niż liczba wątków, które będą dostępne w przypadku równoległego regionu bez [num_threads](openmp-clauses.md#num-threads) zostały zdefiniowane w tym momencie w kodzie.|
|[omp_get_nested](#omp-get-nested)|Zwraca wartość wskazującą, czy włączono równoległości zagnieżdżonych.|
|[omp_get_num_procs](#omp-get-num-procs)|Zwraca liczbę procesorów, które są dostępne, gdy wywoływana jest funkcja.|
|[omp_get_num_threads](#omp-get-num-threads)|Zwraca liczbę wątków w równoległego regionu.|
|[omp_get_thread_num](#omp-get-thread-num)|Zwraca liczbę wątków wątek wykonywania w jego zespół wątku.|
|[omp_get_wtick](#omp-get-wtick)|Zwraca liczbę sekund między taktami zegara procesora.|
|[omp_get_wtime](#omp-get-wtime)|Zwraca wartość w sekundach czas, jaki upłynął od pewnego momentu.|
|[omp_in_parallel](#omp-in-parallel)|Zwraca wartość różną od zera, jeśli wywołano z w ramach równoległego regionu.|
|[omp_init_lock](#omp-init-lock)|Inicjuje prostą blokadą.|
|[omp_init_nest_lock](#omp-init-nest-lock)|Inicjuje blokadę.|
|[omp_set_dynamic](#omp-set-dynamic)|Wskazuje, że liczba wątków, które są dostępne w kolejnych regionów równoległych można dostosować w czasie wykonywania.|
|[omp_set_lock](#omp-set-lock)|Wykonywanie wątku bloków, dopóki blokada jest dostępna.|
|[omp_set_nest_lock](#omp-set-nest-lock)|Wykonywanie wątku bloków, dopóki blokada jest dostępna.|
|[omp_set_nested](#omp-set-nested)|Włącza równoległości zagnieżdżonych.|
|[omp_set_num_threads](#omp-set-num-threads)|Ustawia liczbę wątków w kolejnych regionach równoległych, chyba że zostaną zastąpione [num_threads](openmp-clauses.md#num-threads) klauzuli.|
|[omp_test_lock](#omp-test-lock)|Próbuje ustawić blokadę, ale nie blokuje wykonywanie wątków.|
|[omp_test_nest_lock](#omp-test-nest-lock)|Próbuje ustawić blokadę zagnieżdżalnych, ale nie blokuje wykonywanie wątków.|
|[omp_unset_lock](#omp-unset-lock)|Zwalnia blokadę.|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|Zwalnia blokadę zagnieżdżalnych.|

## <a name="omp-destroy-lock"></a>Funkcje omp_destroy_lock

Deinicjuje blokadę.

```
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu [omp_lock_t](openmp-data-types.md#omp-lock-t) , została zainicjowana przy użyciu [funkcje omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.2 funkcje omp_destroy_lock i omp_destroy_nest_lock funkcji](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Przykład

Zobacz [funkcje omp_init_lock](#omp-init-lock) na przykład za pomocą `omp_destroy_lock`.

## <a name="omp-destroy-nest-lock"></a>omp_destroy_nest_lock

Deinicjuje blokadą.

```
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu [omp_nest_lock_t](openmp-data-types.md#omp-nest-lock-t) , została zainicjowana przy użyciu [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.2 funkcje omp_destroy_lock i omp_destroy_nest_lock funkcji](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Przykład

Zobacz [omp_init_nest_lock](#omp-init-nest-lock) na przykład za pomocą `omp_destroy_nest_lock`.

## <a name="omp-get-dynamic"></a>omp_get_dynamic

Zwraca wartość wskazującą, jeśli liczba wątków, które są dostępne w kolejnych regionów równoległych można dostosować w czasie wykonywania.

```
int omp_get_dynamic();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera oznacza, że wątki zostaną dostosowane dynamicznie.

### <a name="remarks"></a>Uwagi

Dynamiczne Dostosowywanie wątków jest określony za pomocą [omp_set_dynamic](#omp-set-dynamic) i [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic).

Aby uzyskać więcej informacji, zobacz [3.1.7 funkcja omp_set_dynamic](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Przykład

Zobacz [omp_set_dynamic](#omp-set-dynamic) na przykład za pomocą `omp_get_dynamic`.

## <a name="omp-get-max-threads"></a>omp_get_max_threads

Zwraca liczbę całkowitą, która jest równa lub większa niż liczba wątków, które będą dostępne w przypadku równoległego regionu bez [num_threads](openmp-clauses.md#num-threads) zostały zdefiniowane w tym momencie w kodzie.

```
int omp_get_max_threads( )
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.1.3 funkcja omp_get_max_threads](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md).

### <a name="example"></a>Przykład

```
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

Zwraca wartość wskazującą, czy włączono równoległości zagnieżdżonych.

```
int omp_get_nested( );
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera oznacza, że zagnieżdżone równoległości jest włączona.

### <a name="remarks"></a>Uwagi

Zagnieżdżone równoległości jest określony za pomocą [omp_set_nested](#omp-set-nested) i [OMP_NESTED](openmp-environment-variables.md#omp-nested).

Aby uzyskać więcej informacji, zobacz [3.1.10 funkcja omp_get_nested](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).

### <a name="example"></a>Przykład

Zobacz [omp_set_nested](#omp-set-nested) na przykład za pomocą `omp_get_nested`.

## <a name="omp-get-num-procs"></a>omp_get_num_procs

Zwraca liczbę procesorów, które są dostępne, gdy wywoływana jest funkcja.

```
int omp_get_num_procs();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.1.5 funkcja omp_get_num_procs](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md).

### <a name="example"></a>Przykład

```
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

Zwraca liczbę wątków w równoległego regionu.

```
int omp_get_num_threads( );
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.1.2 funkcja omp_get_num_threads](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md).

### <a name="example"></a>Przykład

```
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

Zwraca liczbę wątków wątek wykonywania w jego zespół wątku.

```
int omp_get_thread_num( );
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.1.4 funkcja omp_get_thread_num](../../../parallel/openmp/3-1-4-omp-get-thread-num-function.md).

### <a name="example"></a>Przykład

Zobacz [równoległe](openmp-directives.md#parallel) na przykład za pomocą `omp_get_thread_num`.

## <a name="omp-get-wtick"></a>omp_get_wtick

Zwraca liczbę sekund między taktami zegara procesora.

```
double omp_get_wtick( );
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.3.2 funkcja omp_get_wtick](../../../parallel/openmp/3-3-2-omp-get-wtick-function.md).

### <a name="example"></a>Przykład

Zobacz [omp_get_wtime](#omp-get-wtime) na przykład za pomocą `omp_get_wtick`.

## <a name="omp-get-wtime"></a>omp_get_wtime

Zwraca wartość w sekundach czas, jaki upłynął od pewnego momentu.

```
double omp_get_wtime( );
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość w sekundach czas, jaki upłynął od dowolnego niektóre, ale spójnego punktu.

### <a name="remarks"></a>Uwagi

Podczas wykonywania programu, porównywanie nadchodzących możliwe pozostanie niezmienione tego punktu.

Aby uzyskać więcej informacji, zobacz [3.3.1 funkcja omp_get_wtime](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md).

### <a name="example"></a>Przykład

```
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

Zwraca wartość różną od zera, jeśli wywołano z w ramach równoległego regionu.

```
int omp_in_parallel( );
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.1.6 funkcja omp_in_parallel](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md).

### <a name="example"></a>Przykład

```
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

## <a name="omp-init-lock"></a>Funkcje omp_init_lock

Inicjuje prostą blokadą.

```
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu [omp_lock_t](openmp-data-types.md#omp-lock-t).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.1 funkcje omp_init_lock i omp_init_nest_lock funkcji](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

### <a name="example"></a>Przykład

```
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

```
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu [omp_nest_lock_t](openmp-data-types.md#omp-nest-lock-t).

### <a name="remarks"></a>Uwagi

Początkowa liczba zagnieżdżenia wynosi zero.

Aby uzyskać więcej informacji, zobacz [3.2.1 funkcje omp_init_lock i omp_init_nest_lock funkcji](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

### <a name="example"></a>Przykład

```
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

Wskazuje, że liczba wątków, które są dostępne w kolejnych regionów równoległych można dostosować w czasie wykonywania.

```
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość, która wskazuje, jeśli liczba wątków, które są dostępne w kolejnych regionów równoległych można dostosować w czasie wykonywania.  Jeśli wartość jest niezerowa, środowisko uruchomieniowe, które można dostosować liczbę wątków, jeśli zero, środowisko wykonawcze nie będzie dynamicznie dostosowuje liczbę wątków.

### <a name="remarks"></a>Uwagi

Liczba wątków nigdy nie przekroczy wartość ustawioną przy użyciu [omp_set_num_threads](#omp-set-num-threads) lub [OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads).

Użyj [omp_get_dynamic](#omp-get-dynamic) do wyświetlenia bieżącego ustawienia `omp_set_dynamic`.

Ustawienie `omp_set_dynamic` spowoduje przesłonięcie ustawień [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic) zmiennej środowiskowej.

Aby uzyskać więcej informacji, zobacz [3.1.7 funkcja omp_set_dynamic](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Przykład

```
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

Wykonywanie wątku bloków, dopóki blokada jest dostępna.

```
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu [omp_lock_t](openmp-data-types.md#omp-lock-t) , została zainicjowana przy użyciu [funkcje omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.3 funkcje omp_set_lock i omp_set_nest_lock](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Przykłady

Zobacz [funkcje omp_init_lock](#omp-init-lock) na przykład za pomocą `omp_set_lock`.

## <a name="omp-set-nest-lock"></a>omp_set_nest_lock

Wykonywanie wątku bloków, dopóki blokada jest dostępna.

```
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu [omp_nest_lock_t](openmp-data-types.md#omp-nest-lock-t) , została zainicjowana przy użyciu [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.3 funkcje omp_set_lock i omp_set_nest_lock](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Przykłady

Zobacz [omp_init_nest_lock](#omp-init-nest-lock) na przykład za pomocą `omp_set_nest_lock`.

## <a name="omp-set-nested"></a>omp_set_nested

Włącza równoległości zagnieżdżonych.

```
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość różną od zera umożliwia zagnieżdżonych równoległości, gdy zero wyłącza równoległości zagnieżdżonych.

### <a name="remarks"></a>Uwagi

OMP zagnieżdżone równoległość może zostać włączona przy użyciu `omp_set_nested`, lub poprzez skonfigurowanie [OMP_NESTED](openmp-environment-variables.md#omp-nested) zmiennej środowiskowej.

Ustawienie `omp_set_nested` spowoduje przesłonięcie ustawień `OMP_NESTED` zmiennej środowiskowej.

Włączanie zmiennej środowiskowej może przerwać program w przeciwnym razie operacyjnej, ponieważ wykładniczo zwiększa liczbę wątków podczas zagnieżdżania regionów równoległych.  Na przykład funkcja, która recurses sześciokrotnie o liczbie wątków OMP równa 4 wymaga 4096 (4 do potęgi równej 6) wątków. Z wyjątkiem z mogę/aplikacji, aplikacji zwykle spadku wydajności w przypadku większej liczby wątków niż procesorów.

Użyj [omp_get_nested](#omp-get-nested) do wyświetlenia bieżącego ustawienia `omp_set_nested`.

Aby uzyskać więcej informacji, zobacz [3.1.9 funkcja omp_set_nested](../../../parallel/openmp/3-1-9-omp-set-nested-function.md).

### <a name="example"></a>Przykład

```
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

Ustawia liczbę wątków w kolejnych regionach równoległych, chyba że zostaną zastąpione [num_threads](openmp-clauses.md#num-threads) klauzuli.

```
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>Parametry

*num_threads*<br/>
Liczba wątków w równoległego regionu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.1.1 funkcja omp_set_num_threads](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).

### <a name="example"></a>Przykład

Zobacz [omp_get_num_threads](#omp-get-num-threads) na przykład za pomocą `omp_set_num_threads`.

## <a name="omp-test-lock"></a>Funkcje omp_test_lock

Próbuje ustawić blokadę, ale nie blokuje wykonywanie wątków.

```
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu [omp_lock_t](openmp-data-types.md#omp-lock-t) , została zainicjowana przy użyciu [funkcje omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.5 funkcje omp_test_lock i omp_test_nest_lock funkcji](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

### <a name="example"></a>Przykład

```
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

Próbuje ustawić blokadę zagnieżdżalnych, ale nie blokuje wykonywanie wątków.

```
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu [omp_nest_lock_t](openmp-data-types.md#omp-nest-lock-t) , została zainicjowana przy użyciu [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.5 funkcje omp_test_lock i omp_test_nest_lock funkcji](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

### <a name="example"></a>Przykład

```
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

## <a name="omp-unset-lock"></a>Funkcje omp_unset_lock

Zwalnia blokadę.

```
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu [omp_lock_t](openmp-data-types.md#omp-lock-t) , została zainicjowana przy użyciu [funkcje omp_init_lock](#omp-init-lock)własnością wątku i wykonywanie w funkcji.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.4 funkcje omp_unset_lock i omp_unset_nest_lock funkcji](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Przykład

Zobacz [funkcje omp_init_lock](#omp-init-lock) na przykład za pomocą `omp_unset_lock`.

## <a name="omp-unset-nest-lock"></a>omp_unset_nest_lock

Zwalnia blokadę zagnieżdżalnych.

```
void omp_unset_nest_lock( 
   omp_nest_lock_t *lock 
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Zmienna typu [omp_nest_lock_t](openmp-data-types.md#omp-nest-lock-t) , została zainicjowana przy użyciu [omp_init_nest_lock](#omp-init-nest-lock)własnością wątku i wykonywanie w funkcji.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [3.2.4 funkcje omp_unset_lock i omp_unset_nest_lock funkcji](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Przykład

Zobacz [omp_init_nest_lock](#omp-init-nest-lock) na przykład za pomocą `omp_unset_nest_lock`.
