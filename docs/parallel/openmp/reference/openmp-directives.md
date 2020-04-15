---
title: OpenMP — Dyrektywy
ms.date: 03/20/2019
f1_keywords:
- OpenMP directives
- atomic
- barrier
- critical
- flush
- for
- master
- parallel
- section
- single
- threadprivate
helpviewer_keywords:
- OpenMP directives
- atomic OpenMP directive
- barrier OpenMP directive
- critical OpenMP directive
- flush OpenMP directive
- for OpenMP directive
- master OpenMP directive
- ordered OpenMP directive
- parallel OpenMP directive
- sections OpenMP directive
- single OpenMP directive
- threadprivate OpenMP directive
ms.assetid: 0562c263-344c-466d-843e-de830d918940
ms.openlocfilehash: 569419b3422b155afc6e9692efaecd4e5a06f188
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366443"
---
# <a name="openmp-directives"></a>OpenMP — Dyrektywy

Zawiera łącza do dyrektyw używanych w interfejsie API OpenMP.

Visual C++ obsługuje następujące dyrektywy OpenMP.

W przypadku równoległego dzielenia się pracą:

|Dyrektywy|Opis|
|---------|-----------|
|[parallel](#parallel)|Definiuje region równoległy, który jest kodem, który będzie wykonywany przez wiele wątków równolegle.|
|[for](#for-openmp)|Powoduje, że praca `for` wykonana w pętli wewnątrz regionu równoległego, które mają być podzielone między wątki.|
|[Sekcje](#sections-openmp)|Identyfikuje sekcje kodu, które mają być podzielone między wszystkie wątki.|
|[Pojedynczy](#single)|Pozwala określić, że sekcja kodu powinny być wykonywane w jednym wątku, niekoniecznie wątek główny.|

Dla wzorca i synchronizacji:

|Dyrektywy|Opis|
|---------|-----------|
|[master](#master)|Określa, że tylko wątek główny powinien wykonać sekcję programu.|
|[Krytyczne](#critical)|Określa, że kod jest wykonywany tylko w jednym wątku naraz.|
|[Barierę](#barrier)|Synchronizuje wszystkie wątki w zespole; wszystkie wątki zatrzymują się przy barierze, aż wszystkie wątki wykonają barierę.|
|[atomic](#atomic)|Określa, że lokalizacja pamięci, która zostanie zaktualizowana niepodzielnie.|
|[opróżnianie](#flush-openmp)|Określa, że wszystkie wątki mają ten sam widok pamięci dla wszystkich obiektów udostępnionych.|
|[Zamówione](#ordered-openmp-directives)|Określa, że kod w `for` pętli równoległej powinny być wykonywane jak sekwencyjnej pętli.|

Dla środowiska danych:

|Dyrektywy|Opis|
|---------|-----------|
|[threadprivate](#threadprivate)|Określa, że zmienna jest prywatna dla wątku.|

## <a name="atomic"></a><a name="atomic"></a>Atomowej

Określa, że lokalizacja pamięci, która zostanie zaktualizowana niepodzielnie.

```cpp
#pragma omp atomic
   expression
```

### <a name="parameters"></a>Parametry

*Wyrażenie*<br/>
Instrukcja, która ma *lvalue*, którego lokalizację pamięci, którą chcesz chronić przed więcej niż jednym zapisem.

### <a name="remarks"></a>Uwagi

Dyrektywa `atomic` nie obsługuje żadnych klauzul.

Aby uzyskać więcej informacji, zobacz [2.6.4 konstrukcji atomowej](../../../parallel/openmp/2-6-4-atomic-construct.md).

### <a name="example"></a>Przykład

```cpp
// omp_atomic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define MAX 10

int main() {
   int count = 0;
   #pragma omp parallel num_threads(MAX)
   {
      #pragma omp atomic
      count++;
   }
   printf_s("Number of threads: %d\n", count);
}
```

```Output
Number of threads: 10
```

## <a name="barrier"></a><a name="barrier"></a>Barierę

Synchronizuje wszystkie wątki w zespole; wszystkie wątki zatrzymują się przy barierze, aż wszystkie wątki wykonają barierę.

```cpp
#pragma omp barrier
```

### <a name="remarks"></a>Uwagi

Dyrektywa `barrier` nie obsługuje żadnych klauzul.

Więcej informacji można znaleźć w [2.6.3 dyrektywy w sprawie barier](../../../parallel/openmp/2-6-3-barrier-directive.md).

### <a name="example"></a>Przykład

Aby uzyskać przykład sposobu `barrier`używania , zobacz [master](#master).

## <a name="critical"></a><a name="critical"></a>Krytyczne

Określa, że kod jest wykonywany tylko w jednym wątku naraz.

```cpp
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*Nazwa*<br/>
(Opcjonalnie) Nazwa identyfikująca kod krytyczny. Nazwa musi być ujęta w nawiasy.

### <a name="remarks"></a>Uwagi

Dyrektywa `critical` nie obsługuje żadnych klauzul.

Aby uzyskać więcej informacji, zobacz [2.6.2 konstrukcja krytyczna](../../../parallel/openmp/2-6-2-critical-construct.md).

### <a name="example"></a>Przykład

```cpp
// omp_critical.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>

#define SIZE 10

int main()
{
    int i;
    int max;
    int a[SIZE];

    for (i = 0; i < SIZE; i++)
    {
        a[i] = rand();
        printf_s("%d\n", a[i]);
    }

    max = a[0];
    #pragma omp parallel for num_threads(4)
        for (i = 1; i < SIZE; i++)
        {
            if (a[i] > max)
            {
                #pragma omp critical
                {
                    // compare a[i] and max again because max
                    // could have been changed by another thread after
                    // the comparison outside the critical section
                    if (a[i] > max)
                        max = a[i];
                }
            }
        }

    printf_s("max = %d\n", max);
}
```

```Output
41
18467
6334
26500
19169
15724
11478
29358
26962
24464
max = 29358
```

## <a name="flush"></a><a name="flush-openmp"></a>Flush

Określa, że wszystkie wątki mają ten sam widok pamięci dla wszystkich obiektów udostępnionych.

```cpp
#pragma omp flush [(var)]
```

### <a name="parameters"></a>Parametry

*var*<br/>
(Opcjonalnie) Oddzielona przecinkami lista zmiennych, które reprezentują obiekty, które chcesz zsynchronizować. Jeśli *var* nie jest określony, cała pamięć jest opróżniana.

### <a name="remarks"></a>Uwagi

Dyrektywa `flush` nie obsługuje żadnych klauzul.

Aby uzyskać więcej informacji, zobacz [2.6.5 flush dyrektywy](../../../parallel/openmp/2-6-5-flush-directive.md).

### <a name="example"></a>Przykład

```cpp
// omp_flush.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void read(int *data) {
   printf_s("read data\n");
   *data = 1;
}

void process(int *data) {
   printf_s("process data\n");
   (*data)++;
}

int main() {
   int data;
   int flag;

   flag = 0;

   #pragma omp parallel sections num_threads(2)
   {
      #pragma omp section
      {
         printf_s("Thread %d: ", omp_get_thread_num( ));
         read(&data);
         #pragma omp flush(data)
         flag = 1;
         #pragma omp flush(flag)
         // Do more work.
      }

      #pragma omp section
      {
         while (!flag) {
            #pragma omp flush(flag)
         }
         #pragma omp flush(data)

         printf_s("Thread %d: ", omp_get_thread_num( ));
         process(&data);
         printf_s("data = %d\n", data);
      }
   }
}
```

```Output
Thread 0: read data
Thread 1: process data
data = 2
```

## <a name="for"></a><a name="for-openmp"></a>For

Powoduje, że praca `for` wykonana w pętli wewnątrz regionu równoległego, które mają być podzielone między wątki.

```cpp
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>Parametry

*Klauzule*<br/>
(Opcjonalnie) Zero lub więcej klauzul, zobacz **uwagi** sekcji.

*for_statement*<br/>
Pętla. `for` Niezdefiniowane zachowanie spowoduje, jeśli `for` kod użytkownika w pętli zmienia zmienną indeksu.

### <a name="remarks"></a>Uwagi

Dyrektywa `for` obsługuje następujące klauzule:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [Zamówione](openmp-clauses.md#ordered-openmp-clauses)
- [Harmonogram](openmp-clauses.md#schedule)
- [nowait](openmp-clauses.md#nowait)

Jeśli `parallel` jest również `clauses` określony, może być `parallel` dowolna klauzula zaakceptowana przez lub `for` dyrektyw, z wyjątkiem `nowait`.

Aby uzyskać więcej informacji, zobacz [2.4.1 dla konstrukcji](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Przykład

```cpp
// omp_for.cpp
// compile with: /openmp
#include <stdio.h>
#include <math.h>
#include <omp.h>

#define NUM_THREADS 4
#define NUM_START 1
#define NUM_END 10

int main() {
   int i, nRet = 0, nSum = 0, nStart = NUM_START, nEnd = NUM_END;
   int nThreads = 0, nTmp = nStart + nEnd;
   unsigned uTmp = (unsigned((abs(nStart - nEnd) + 1)) *
                               unsigned(abs(nTmp))) / 2;
   int nSumCalc = uTmp;

   if (nTmp < 0)
      nSumCalc = -nSumCalc;

   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel default(none) private(i) shared(nSum, nThreads, nStart, nEnd)
   {
      #pragma omp master
      nThreads = omp_get_num_threads();

      #pragma omp for
      for (i=nStart; i<=nEnd; ++i) {
            #pragma omp atomic
            nSum += i;
      }
   }

   if  (nThreads == NUM_THREADS) {
      printf_s("%d OpenMP threads were used.\n", NUM_THREADS);
      nRet = 0;
   }
   else {
      printf_s("Expected %d OpenMP threads, but %d were used.\n",
               NUM_THREADS, nThreads);
      nRet = 1;
   }

   if (nSum != nSumCalc) {
      printf_s("The sum of %d through %d should be %d, "
               "but %d was reported!\n",
               NUM_START, NUM_END, nSumCalc, nSum);
      nRet = 1;
   }
   else
      printf_s("The sum of %d through %d is %d\n",
               NUM_START, NUM_END, nSum);
}
```

```Output
4 OpenMP threads were used.
The sum of 1 through 10 is 55
```

## <a name="master"></a><a name="master"></a>Master

Określa, że tylko wątek główny powinien wykonać sekcję programu.

```cpp
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>Uwagi

Dyrektywa `master` nie obsługuje żadnych klauzul.

[Pojedyncza](#single) dyrektywa pozwala określić, że sekcja kodu powinny być wykonywane w jednym wątku, niekoniecznie wątek główny.

Aby uzyskać więcej informacji, zobacz [2.6.1 master construct](../../../parallel/openmp/2-6-1-master-construct.md).

### <a name="example"></a>Przykład

```cpp
// omp_master.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>

int main( )
{
    int a[5], i;

    #pragma omp parallel
    {
        // Perform some computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] = i * i;

        // Print intermediate results.
        #pragma omp master
            for (i = 0; i < 5; i++)
                printf_s("a[%d] = %d\n", i, a[i]);

        // Wait.
        #pragma omp barrier

        // Continue with the computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] += i;
    }
}
```

```Output
a[0] = 0
a[1] = 1
a[2] = 4
a[3] = 9
a[4] = 16
```

## <a name="ordered"></a><a name="ordered-openmp-directives"></a>Zamówione

Określa, że kod w `for` pętli równoległej powinny być wykonywane jak sekwencyjnej pętli.

```cpp
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>Uwagi

Dyrektywa `ordered` musi mieszczeć się w `parallel for` dynamicznym `ordered` zakresie [for](#for-openmp) lub konstrukcji z klauzulą.

Dyrektywa `ordered` nie obsługuje żadnych klauzul.

Aby uzyskać więcej informacji, zobacz [2.6.6 zamówiona konstrukcja](../../../parallel/openmp/2-6-6-ordered-construct.md).

### <a name="example"></a>Przykład

```cpp
// omp_ordered.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

static float a[1000], b[1000], c[1000];

void test(int first, int last)
{
    #pragma omp for schedule(static) ordered
    for (int i = first; i <= last; ++i) {
        // Do something here.
        if (i % 2)
        {
            #pragma omp ordered
            printf_s("test() iteration %d\n", i);
        }
    }
}

void test2(int iter)
{
    #pragma omp ordered
    printf_s("test2() iteration %d\n", iter);
}

int main( )
{
    int i;
    #pragma omp parallel
    {
        test(1, 8);
        #pragma omp for ordered
        for (i = 0 ; i < 5 ; i++)
            test2(i);
    }
}
```

```Output
test() iteration 1
test() iteration 3
test() iteration 5
test() iteration 7
test2() iteration 0
test2() iteration 1
test2() iteration 2
test2() iteration 3
test2() iteration 4
```

## <a name="parallel"></a><a name="parallel"></a>Równoległe

Definiuje region równoległy, który jest kodem, który będzie wykonywany przez wiele wątków równolegle.

```cpp
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*Klauzule*<br/>
(Opcjonalnie) Zero lub więcej klauzul, zobacz **uwagi** sekcji.

### <a name="remarks"></a>Uwagi

Dyrektywa `parallel` obsługuje następujące klauzule:

- [if](openmp-clauses.md#if-openmp)
- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [default](openmp-clauses.md#default-openmp)
- [Udostępnionych](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [reduction](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel`mogą być również używane z dyrektywami [for](#for-openmp) i [sections.](#sections-openmp)

Aby uzyskać więcej informacji, zobacz [2.3 konstrukcja równoległa](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak ustawić liczbę wątków i zdefiniować region równoległy. Liczba wątków jest domyślnie równa liczbie procesorów logicznych na komputerze. Na przykład jeśli masz komputer z jednym procesorem fizycznym, który ma włączone hiperwątkowości włączone, będzie miał dwa procesory logiczne i dwa wątki. Kolejność wydruków może się różnić na różnych maszynach.

```cpp
// omp_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(4)
   {
      int i = omp_get_thread_num();
      printf_s("Hello from thread %d\n", i);
   }
}
```

```Output
Hello from thread 0
Hello from thread 1
Hello from thread 2
Hello from thread 3
```

## <a name="sections"></a><a name="sections-openmp"></a>Sekcje

Identyfikuje sekcje kodu, które mają być podzielone między wszystkie wątki.

```cpp
#pragma omp [parallel] sections [clauses]
{
   #pragma omp section
   {
      code_block
   }
}
```

### <a name="parameters"></a>Parametry

*Klauzule*<br/>
(Opcjonalnie) Zero lub więcej klauzul, zobacz **uwagi** sekcji.

### <a name="remarks"></a>Uwagi

Dyrektywa `sections` może zawierać zero `section` lub więcej dyrektyw.

Dyrektywa `sections` obsługuje następujące klauzule:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [nowait](openmp-clauses.md#nowait)

Jeśli `parallel` jest również `clauses` określony, może być `parallel` dowolna klauzula zaakceptowana przez lub `sections` dyrektyw, z wyjątkiem `nowait`.

Aby uzyskać więcej informacji, zobacz [2.4.2 sekcje konstruować](../../../parallel/openmp/2-4-2-sections-construct.md).

### <a name="example"></a>Przykład

```cpp
// omp_sections.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
    #pragma omp parallel sections num_threads(4)
    {
        printf_s("Hello from thread %d\n", omp_get_thread_num());
        #pragma omp section
        printf_s("Hello from thread %d\n", omp_get_thread_num());
    }
}
```

```Output
Hello from thread 0
Hello from thread 0
```

## <a name="single"></a><a name="single"></a>Pojedynczy

Pozwala określić, że sekcja kodu powinny być wykonywane w jednym wątku, niekoniecznie wątek główny.

```cpp
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*Klauzule*<br/>
(Opcjonalnie) Zero lub więcej klauzul, zobacz **uwagi** sekcji.

### <a name="remarks"></a>Uwagi

Dyrektywa `single` obsługuje następujące klauzule:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [nowait](openmp-clauses.md#nowait)

Master [master](#master) dyrektywy pozwala określić, że sekcja kodu powinny być wykonywane tylko w wątku głównym.

Aby uzyskać więcej informacji, zobacz [2.4.3 pojedyncza konstrukcja](../../../parallel/openmp/2-4-3-single-construct.md).

### <a name="example"></a>Przykład

```cpp
// omp_single.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(2)
   {
      #pragma omp single
      // Only a single thread can read the input.
      printf_s("read input\n");

      // Multiple threads in the team compute the results.
      printf_s("compute results\n");

      #pragma omp single
      // Only a single thread can write the output.
      printf_s("write output\n");
    }
}
```

```Output
read input
compute results
compute results
write output
```

## <a name="threadprivate"></a><a name="threadprivate"></a>Threadprivate

Określa, że zmienna jest prywatna dla wątku.

```cpp
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Oddzielona przecinkami lista zmiennych, które mają być prywatne dla wątku. *var* musi być zmienną o zakresie globalnym lub przestrzenią nazw lub lokalną zmienną statyczną.

### <a name="remarks"></a>Uwagi

Dyrektywa `threadprivate` nie obsługuje żadnych klauzul.

Dyrektywa `threadprivate` jest oparta na [atrybutie wątku](../../../cpp/thread.md) przy użyciu [__declspec](../../../cpp/declspec.md) słowa kluczowego; ograniczenia `__declspec(thread)` dotyczą `threadprivate`. Na przykład `threadprivate` zmienna będzie istnieć w dowolnym wątku uruchomionym w procesie, a nie tylko te wątki, które są częścią zespołu wątku zrodzone przez region równoległy. Należy pamiętać o tym szczegóły implementacji; można zauważyć, że konstruktory dla typu zdefiniowanego przez `threadprivate` użytkownika są wywoływane częściej niż oczekiwane.

Można użyć `threadprivate` w biblioteki DLL, która jest statycznie ładowana podczas uruchamiania procesu, `threadprivate` jednak nie można używać w żadnej biblioteki DLL, która zostanie załadowana za pośrednictwem [LoadLibrary,](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) takich jak biblioteki DLL, które są ładowane z [/DELAYLOAD (import obciążenia opóźnienia),](../../../build/reference/delayload-delay-load-import.md)który również używa `LoadLibrary`.

Zmienna `threadprivate` typu *zniszczalnego* nie jest gwarantowana, aby jej destruktora. Przykład:

```cpp
struct MyType
{
    ~MyType();
};

MyType threaded_var;
#pragma omp threadprivate(threaded_var)
int main()
{
    #pragma omp parallel
    {}
}
```

Użytkownicy nie mają kontroli, kiedy wątki stanowiące region równoległy zakończy. Jeśli te wątki istnieją, gdy proces kończy działanie, wątki nie zostaną powiadomione o zakończeniu procesu, `threaded_var` a destruktor nie będzie wywoływany w dowolnym wątku z wyjątkiem tego, który kończy pracę (w tym miejscu wątek podstawowy). Więc kod nie powinien liczyć `threadprivate` na właściwe zniszczenie zmiennych.

Aby uzyskać więcej informacji, zobacz [2.7.1 threadprivate dyrektywy](../../../parallel/openmp/2-7-1-threadprivate-directive.md).

### <a name="example"></a>Przykład

Aby uzyskać przykład `threadprivate`użycia, zobacz [prywatne](openmp-clauses.md#private-openmp).
