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
- ordered
- parallel
- section
- SECTIONS
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
ms.openlocfilehash: 4db341cf58884263e414e24aacf888c8c88e57cc
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142016"
---
# <a name="openmp-directives"></a>OpenMP — Dyrektywy

Zawiera łącza do dyrektyw używanych w interfejsie API OpenMP.

Wizualizacja C++ obsługuje następujące dyrektywy OpenMP.

W przypadku równoległego udostępniania pracy:

|— Dyrektywa|Opis|
|---------|-----------|
|[parallel](#parallel)|Definiuje region równoległy, który jest kodem, który będzie wykonywany równolegle przez wiele wątków.|
|[for](#for-openmp)|Powoduje, że prace wykonywane w pętli `for` wewnątrz równoległego regionu mają być podzielone między wątki.|
|[poszczególne](#sections-openmp)|Identyfikuje sekcje kodu, które mają być podzielone między wszystkie wątki.|
|[single](#single)|Pozwala określić, że sekcja kodu powinna być wykonywana na pojedynczym wątku, niekoniecznie w wątku głównym.|

W przypadku serwera głównego i synchronizacji:

|— Dyrektywa|Opis|
|---------|-----------|
|[master](#master)|Określa, że tylko wątek główny ma wykonać sekcję programu.|
|[critical](#critical)|Określa, że kod jest wykonywany tylko w jednym wątku naraz.|
|[barrier](#barrier)|Synchronizuje wszystkie wątki w zespole; wszystkie wątki wstrzymują się w granicach, dopóki wszystkie wątki nie wykonują bariery.|
|[atomic](#atomic)|Określa, że lokalizacja pamięci, która ma zostać zaktualizowana niepodzielnie.|
|[płukan](#flush-openmp)|Określa, że wszystkie wątki mają ten sam widok pamięci dla wszystkich obiektów udostępnionych.|
|[każe](#ordered-openmp-directives)|Określa, że kod w ramach równoległej pętli `for` powinien być wykonany jak pętla sekwencyjna.|

W przypadku środowiska danych:

|— Dyrektywa|Opis|
|---------|-----------|
|[threadprivate](#threadprivate)|Określa, że zmienna jest prywatna do wątku.|

## <a name="atomic"></a>części

Określa, że lokalizacja pamięci, która ma zostać zaktualizowana niepodzielnie.

```cpp
#pragma omp atomic
   expression
```

### <a name="parameters"></a>Parametry

*wyrażenia*<br/>
Instrukcja, która ma *lvalue*, której lokalizacja pamięci ma być chroniona przed więcej niż jednym zapisem.

### <a name="remarks"></a>Uwagi

Dyrektywa `atomic` nie obsługuje klauzul.

Aby uzyskać więcej informacji, zobacz [2.6.4a niepodzielna konstrukcja](../../../parallel/openmp/2-6-4-atomic-construct.md).

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

## <a name="barrier"></a>barier

Synchronizuje wszystkie wątki w zespole; wszystkie wątki wstrzymują się w granicach, dopóki wszystkie wątki nie wykonują bariery.

```cpp
#pragma omp barrier
```

### <a name="remarks"></a>Uwagi

Dyrektywa `barrier` nie obsługuje klauzul.

Aby uzyskać więcej informacji, zobacz [dyrektywa bariery 2.6.3](../../../parallel/openmp/2-6-3-barrier-directive.md).

### <a name="example"></a>Przykład

Przykład używania `barrier`można znaleźć w temacie [Master](#master).

## <a name="critical"></a>najistotniejsz

Określa, że kod jest wykonywany tylko w jednym wątku naraz.

```cpp
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*Nazwij*<br/>
Obowiązkowe Nazwa identyfikująca kod krytyczny. Nazwa musi być ujęta w nawiasy.

### <a name="remarks"></a>Uwagi

Dyrektywa `critical` nie obsługuje klauzul.

Aby uzyskać więcej informacji, zobacz [2.6.2 o krytycznym znaczeniu](../../../parallel/openmp/2-6-2-critical-construct.md).

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

## <a name="flush-openmp"></a>płukan

Określa, że wszystkie wątki mają ten sam widok pamięci dla wszystkich obiektów udostępnionych.

```cpp
#pragma omp flush [(var)]
```

### <a name="parameters"></a>Parametry

*var*<br/>
Obowiązkowe Rozdzielana przecinkami lista zmiennych reprezentujących obiekty, które mają zostać zsynchronizowane. Jeśli *var* nie jest określona, cała pamięć zostanie opróżniona.

### <a name="remarks"></a>Uwagi

Dyrektywa `flush` nie obsługuje klauzul.

Aby uzyskać więcej informacji, zobacz [2.6.5 Flush — dyrektywa](../../../parallel/openmp/2-6-5-flush-directive.md).

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

## <a name="for-openmp"></a>dla

Powoduje, że prace wykonywane w pętli `for` wewnątrz równoległego regionu mają być podzielone między wątki.

```cpp
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>Parametry

*warunki*<br/>
Obowiązkowe Zero lub więcej klauzul, zobacz sekcję **uwagi** .

*for_statement*<br/>
Pętla `for`. Niezdefiniowane zachowanie spowoduje, że kod użytkownika w pętli `for` zmieni zmienną indeksu.

### <a name="remarks"></a>Uwagi

Dyrektywa `for` obsługuje następujące klauzule:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [każe](openmp-clauses.md#ordered-openmp-clauses)
- [schedule](openmp-clauses.md#schedule)
- [nowait](openmp-clauses.md#nowait)

Jeśli określono również `parallel`, `clauses` może być dowolną klauzulą akceptowaną przez dyrektywy `parallel` lub `for`, z wyjątkiem `nowait`.

Aby uzyskać więcej informacji, zobacz [2.4.1 for konstrukcja](../../../parallel/openmp/2-4-1-for-construct.md).

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

## <a name="master"></a>formantu

Określa, że tylko wątek główny ma wykonać sekcję programu.

```cpp
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>Uwagi

Dyrektywa `master` nie obsługuje klauzul.

[Pojedyncza](#single) dyrektywa pozwala określić, że sekcja kodu powinna być wykonywana na pojedynczym wątku, niekoniecznie wątku głównego.

Aby uzyskać więcej informacji, zobacz [główny konstrukcja](../../../parallel/openmp/2-6-1-master-construct.md).

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

## <a name="ordered-openmp-directives"></a>każe

Określa, że kod w ramach równoległej pętli `for` powinien być wykonany jak pętla sekwencyjna.

```cpp
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>Uwagi

Dyrektywa `ordered` musi znajdować się w zakresie dynamicznym konstrukcji [for](#for-openmp) lub `parallel for` z klauzulą `ordered`.

Dyrektywa `ordered` nie obsługuje klauzul.

Aby uzyskać więcej informacji, zobacz [2.6.6 uporządkowana konstrukcja](../../../parallel/openmp/2-6-6-ordered-construct.md).

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

## <a name="parallel"></a>równoległ

Definiuje region równoległy, który jest kodem, który będzie wykonywany równolegle przez wiele wątków.

```cpp
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*warunki*<br/>
Obowiązkowe Zero lub więcej klauzul, zobacz sekcję **uwagi** .

### <a name="remarks"></a>Uwagi

Dyrektywa `parallel` obsługuje następujące klauzule:

- [przypadku](openmp-clauses.md#if-openmp)
- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [default](openmp-clauses.md#default-openmp)
- [udostępniać](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [reduction](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel` można również używać z dyrektywami [for](#for-openmp) i [](#sections-openmp) .

Aby uzyskać więcej informacji, zobacz [2,3 równoległa konstrukcja](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak ustawić liczbę wątków i zdefiniować region równoległy. Liczba wątków jest równa domyślnie liczbie procesorów logicznych na komputerze. Na przykład jeśli masz maszynę z jednym procesorem fizycznym, który ma włączoną funkcję wielowątkowości, będzie on miał dwa procesory logiczne i dwa wątki. Kolejność danych wyjściowych może się różnić w zależności od różnych maszyn.

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

## <a name="sections-openmp"></a>poszczególne

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

*warunki*<br/>
Obowiązkowe Zero lub więcej klauzul, zobacz sekcję **uwagi** .

### <a name="remarks"></a>Uwagi

Dyrektywa `sections` może zawierać co najmniej zero dyrektywy `section`.

Dyrektywa `sections` obsługuje następujące klauzule:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [nowait](openmp-clauses.md#nowait)

Jeśli określono również `parallel`, `clauses` może być dowolną klauzulą akceptowaną przez dyrektywy `parallel` lub `sections`, z wyjątkiem `nowait`.

Aby uzyskać więcej informacji, [Zobacz sekcję](../../../parallel/openmp/2-4-2-sections-construct.md).

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

## <a name="single"></a>wiersz

Pozwala określić, że sekcja kodu powinna być wykonywana na pojedynczym wątku, niekoniecznie w wątku głównym.

```cpp
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*warunki*<br/>
Obowiązkowe Zero lub więcej klauzul, zobacz sekcję **uwagi** .

### <a name="remarks"></a>Uwagi

Dyrektywa `single` obsługuje następujące klauzule:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [nowait](openmp-clauses.md#nowait)

Dyrektywa [główna](#master) pozwala określić, że sekcja kodu powinna być wykonywana tylko w wątku głównym.

Aby uzyskać więcej informacji, zobacz [2.4.3 Single konstrukcja](../../../parallel/openmp/2-4-3-single-construct.md).

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

## <a name="threadprivate"></a>threadprivate

Określa, że zmienna jest prywatna do wątku.

```cpp
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Rozdzielana przecinkami lista zmiennych, które mają być prywatne w wątku. wartość *var* musi być zmienną o zakresie globalnym lub przestrzeni nazw lub lokalną zmienną statyczną.

### <a name="remarks"></a>Uwagi

Dyrektywa `threadprivate` nie obsługuje klauzul.

Dyrektywa `threadprivate` jest oparta na atrybucie [wątku](../../../cpp/thread.md) za pomocą słowa kluczowego [__declspec](../../../cpp/declspec.md) ; Limity dotyczące `__declspec(thread)` dotyczą `threadprivate`. Na przykład zmienna `threadprivate` będzie istnieć w dowolnym wątku uruchomionym w procesie, a nie tylko w wątkach, które są częścią zespołu wątków duplikowanego przez region równoległy. Należy pamiętać o tym szczegółach implementacji; można zauważyć, że konstruktory dla `threadprivate` typu zdefiniowanego przez użytkownika są wywoływane częściej niż oczekiwano.

Można użyć `threadprivate` w bibliotece DLL, która jest statycznie załadowana podczas uruchamiania procesu, ale nie można używać `threadprivate` w żadnej z bibliotek DLL, które będą ładowane za pomocą funkcji [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) , takich jak biblioteki DLL, które są ładowane z [/DELAYLOAD (opóźnione Importowanie ładowania)](../../../build/reference/delayload-delay-load-import.md), które również używają `LoadLibrary`.

Zmienna `threadprivate` typu *zniszczalnych* nie gwarantuje, że jego destruktor został wywołany. Na przykład:

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

Użytkownicy nie mają kontroli, gdy wątki tworzące region równoległy zakończą działanie. Jeśli te wątki istnieją po zakończeniu procesu, wątki nie będą powiadamiane o zakończeniu procesu, a destruktor nie zostanie wywołany dla `threaded_var` w żadnym wątku, z wyjątkiem tego, który zostanie zakończony (w tym miejscu). Dlatego kod nie powinien liczyć przy właściwym zniszczeniu zmiennych `threadprivate`.

Aby uzyskać więcej informacji, zobacz [2.7.1 threadprivate dyrektywie](../../../parallel/openmp/2-7-1-threadprivate-directive.md).

### <a name="example"></a>Przykład

Aby uzyskać przykład użycia `threadprivate`, zobacz [Private](openmp-clauses.md#private-openmp).
