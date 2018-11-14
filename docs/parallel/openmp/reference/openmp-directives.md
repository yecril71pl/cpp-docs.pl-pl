---
title: OpenMP, dyrektywy
ms.date: 10/22/2018
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
ms.openlocfilehash: a61e74bda4e508bac3c4afd183fa2ab204c629d1
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51333244"
---
# <a name="openmp-directives"></a>OpenMP, dyrektywy

Zawiera łącza do informacji o dyrektywach używany w interfejsie API OpenMP.

Visual C++ obsługuje następujące dyrektywy OpenMP:

|— Dyrektywa|Opis|
|---------|-----------|
|[atomic](#atomic)|Określa, że lokalizacji w pamięci, który będzie aktualizowany niepodzielne.|
|[barrier](#barrier)|Synchronizuje wszystkie wątki w zespole; wszystkie wątki wstrzymać na barierze, dopóki wszystkie wątki wykonania barierę.|
|[critical](#critical)|Określa, czy kod jest wykonywane tylko w jednym wątku w danym momencie.|
|[flush](#flush-openmp)|Określa, że wszystkie wątki mają tego samego widoku pamięci dla wszystkich obiektów udostępnionych.|
|[for](#for-openmp)|Powoduje, że prace wykonane w `for` pętli równoległego regionu podzielony między wątkami.|
|[master](#master)|Określa, że główny wątek powinien zostać wykonany części programu.|
|[Uporządkowane](#ordered-openmp-directives)|Określa, że kod w ramach równoległego `for` pętli ma być wykonany, takich jak pętla Sekwencyjna.|
|[parallel](#parallel)|Definiuje równoległego regionu, czyli kodu wykonywanego przez wiele wątków jednocześnie.|
|[Sekcje](#sections-openmp)|Identyfikuje sekcje kodu w celu podzielone między wszystkie wątki.|
|[single](#single)|Pozwala określić, że sekcji kodu powinna zostać wykonana w jednym wątku, niekoniecznie głównego wątku.|
|[threadprivate](#threadprivate)|Określa, czy zmienna jest prywatnego wątku.|

## <a name="atomic"></a>Atomic

Określa, że lokalizacji w pamięci, który będzie aktualizowany niepodzielne.

```
#pragma omp atomic
   expression
```

### <a name="parameters"></a>Parametry

*Wyrażenie*<br/>
Instrukcja, która ma l-wartości, którego chcesz chronić przed więcej niż jeden zapis lokalizacji w pamięci. Aby uzyskać więcej informacji o formularzach prawne wyrażenia zobacz specyfikację OpenMP.

### <a name="remarks"></a>Uwagi

`atomic` Dyrektywy nie obsługuje żadnych klauzule OpenMP.

Aby uzyskać więcej informacji, zobacz [konstruowania 2.6.4 atomic](../../../parallel/openmp/2-6-4-atomic-construct.md).

### <a name="example"></a>Przykład

```
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

## <a name="barrier"></a>Barrier

Synchronizuje wszystkie wątki w zespole; wszystkie wątki wstrzymać na barierze, dopóki wszystkie wątki wykonania barierę.

```
#pragma omp barrier
```

### <a name="remarks"></a>Uwagi

`barrier` Dyrektywy nie obsługuje żadnych klauzule OpenMP.

Aby uzyskać więcej informacji, zobacz [2.6.3 dyrektywa barrier](../../../parallel/openmp/2-6-3-barrier-directive.md).

### <a name="example"></a>Przykład

Przykład sposobu użycia `barrier`, zobacz [wzorca](#master).

## <a name="critical"></a>Krytyczne

Określa, czy kod jest wykonać tylko w jednym wątku w danym momencie.

```
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*Nazwa*<br/>
(Opcjonalnie) Nazwa do identyfikacji kodu krytycznego. Należy zauważyć, że tej nazwy muszą być ujęte w nawiasy.

### <a name="remarks"></a>Uwagi

`critical` Dyrektywy nie obsługuje żadnych klauzule OpenMP.

Aby uzyskać więcej informacji, zobacz [konstruowania 2.6.2 krytyczne](../../../parallel/openmp/2-6-2-critical-construct.md).

### <a name="example"></a>Przykład

```
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

## <a name="flush-openmp"></a>opróżnianie (OpenMP)

Określa, że wszystkie wątki mają tego samego widoku pamięci dla wszystkich obiektów udostępnionych.

```
#pragma omp flush [(var)]
```

### <a name="parameters"></a>Parametry

*var*<br/>
(Opcjonalnie) Rozdzielana przecinkami lista zmiennych, które reprezentują obiekty, które mają być synchronizowane. Jeśli `var` nie jest określona, jest opróżniany całej pamięci.

### <a name="remarks"></a>Uwagi

`flush` Dyrektywy nie obsługuje żadnych klauzule OpenMP.

Aby uzyskać więcej informacji, zobacz [2.6.5 dyrektywa opróżniania](../../../parallel/openmp/2-6-5-flush-directive.md).

### <a name="example"></a>Przykład

```
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

## <a name="for-openmp"></a>Aby uzyskać (OpenMP)

Powoduje, że prace wykonane w `for` pętli równoległego regionu podzielony między wątkami.

```
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>Parametry

*Klauzule*<br/>
(Opcjonalnie) Zero lub więcej klauzul. Zobacz sekcję Spostrzeżenia, aby uzyskać listę klauzul obsługiwane przez `for`.

*for_statement*<br/>
A `for` pętli. Spowoduje niezdefiniowane zachowanie, jeśli kod użytkownika `for` zmienia się zmienna index pętli.

### <a name="remarks"></a>Uwagi

`for` Dyrektywy obsługuje następujące klauzule OpenMP:

- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [nowait](openmp-clauses.md#nowait)
- [Uporządkowane](openmp-clauses.md#ordered-openmp-clauses)
- [private](openmp-clauses.md#private-openmp)
- [reduction](openmp-clauses.md#reduction)
- [schedule](openmp-clauses.md#schedule)

Jeśli `parallel` również jest określony, `clauses` mogą być klauzuli akceptowane przez `parallel` lub `for` dyrektyw, z wyjątkiem `nowait`.

Aby uzyskać więcej informacji, zobacz [2.4.1 konstrukcji](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Przykład

```
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

## <a name="master"></a>Wzorzec

Określa, że główny wątek powinien zostać wykonany części programu.

```
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>Uwagi

`master` Dyrektywy nie obsługuje żadnych klauzule OpenMP.

[Pojedynczego](#single) dyrektywy pozwala określić, że sekcji kodu powinna zostać wykonana w jednym wątku, niekoniecznie głównego wątku.

Aby uzyskać więcej informacji, zobacz [2.6.1 opanować konstrukcji](../../../parallel/openmp/2-6-1-master-construct.md).

### <a name="example"></a>Przykład

```
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

## <a name="ordered-openmp-directives"></a>uporządkowane (dyrektywy OpenMP)

Określa, że kod w ramach równoległego `for` pętli ma być wykonany, takich jak pętla Sekwencyjna.

```
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>Uwagi

`ordered` Dyrektywy musi należeć do zakresu dynamicznego [dla](#for-openmp) lub `parallel for` skonstruować przy użyciu `ordered` klauzuli.

`ordered` Dyrektywy nie obsługuje żadnych klauzule OpenMP.

Aby uzyskać więcej informacji, zobacz [2.6.6 konstrukcja uporządkowana](../../../parallel/openmp/2-6-6-ordered-construct.md).

### <a name="example"></a>Przykład

```
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

## <a name="parallel"></a>równoległe

Definiuje równoległego regionu, czyli kodu wykonywanego przez wiele wątków jednocześnie.

```
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*Klauzule*<br/>
(Opcjonalnie) Zero lub więcej klauzul.  Zobacz sekcję Spostrzeżenia, aby uzyskać listę klauzul obsługiwane przez `parallel`.

### <a name="remarks"></a>Uwagi

`parallel` Dyrektywy obsługuje następujące klauzule OpenMP:

- [copyin](openmp-clauses.md#copyin)
- [default](openmp-clauses.md#default-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [if](openmp-clauses.md#if-openmp)
- [num_threads](openmp-clauses.md#num-threads)
- [private](openmp-clauses.md#private-openmp)
- [reduction](openmp-clauses.md#reduction)
- [Udostępnione](openmp-clauses.md#shared-openmp)

`parallel` można również za pomocą [sekcje](#sections-openmp) i [dla](#for-openmp) dyrektywy.

Aby uzyskać więcej informacji, zobacz [2.3 konstrukcja równoległa](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak ustawić liczbę wątków i zdefiniuj równoległego regionu. Liczba wątków jest domyślnie równa liczbie procesorów logicznych na maszynie. Na przykład jeśli masz maszyny z jednego procesora fizycznego, który ma włączoną wielowątkowość, ma dwa procesory logiczne i dwoma wątkami.

```
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

### <a name="comment"></a>Komentarz

Należy pamiętać, że kolejność danych wyjściowych może się różnić na różnych maszynach.

## <a name="sections-openmp"></a>sekcje (OpenMP)

Identyfikuje sekcje kodu w celu podzielone między wszystkie wątki.

```
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
(Opcjonalnie) Zero lub więcej klauzul. Zobacz sekcję Spostrzeżenia, aby uzyskać listę klauzul obsługiwane przez `sections`.

### <a name="remarks"></a>Uwagi

`sections` Dyrektywy może zawierać zero lub więcej `section` dyrektywy.

`sections` Dyrektywy obsługuje następujące klauzule OpenMP:

- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [nowait](openmp-clauses.md#nowait)
- [private](openmp-clauses.md#private-openmp)
- [reduction](openmp-clauses.md#reduction)

Jeśli `parallel` również jest określony, `clauses` mogą być klauzuli akceptowane przez `parallel` lub `sections` dyrektyw, z wyjątkiem `nowait`.

Aby uzyskać więcej informacji, zobacz [2.4.2 konstrukcja sections](../../../parallel/openmp/2-4-2-sections-construct.md).

### <a name="example"></a>Przykład

```
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

## <a name="single"></a>Pojedynczy

Pozwala określić, że sekcji kodu powinna zostać wykonana w jednym wątku, niekoniecznie głównego wątku.

```
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parametry

*Klauzule*<br/>
(Opcjonalnie) Zero lub więcej klauzul. Zobacz sekcję Spostrzeżenia, aby uzyskać listę klauzul obsługiwane przez `single`.

### <a name="remarks"></a>Uwagi

`single` Dyrektywy obsługuje następujące klauzule OpenMP:

- [copyprivate](openmp-clauses.md#copyprivate)
- [firstprivate](openmp-clauses.md#firstprivate)
- [nowait](openmp-clauses.md#nowait)
- [private](openmp-clauses.md#private-openmp)

[Wzorca](#master) dyrektywy pozwala określić, że część kodu mają zostać wykonane tylko w wątku głównym.

Aby uzyskać więcej informacji, zobacz [konstruowania 2.4.3 pojedynczego](../../../parallel/openmp/2-4-3-single-construct.md).

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

Określa, czy zmienna jest prywatnego wątku.

```
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Rozdzielana przecinkami lista zmiennych, które mają być prywatnego wątku. `var` musi być globalne lub przestrzeń nazw — zmienną o zakresie lub zmiennej lokalnej statycznej.

### <a name="remarks"></a>Uwagi

`threadprivate` Dyrektywy nie obsługuje żadnych klauzule OpenMP.

Aby uzyskać więcej informacji, zobacz [2.7.1 dyrektywa threadprivate](../../../parallel/openmp/2-7-1-threadprivate-directive.md).

`threadprivate` Dyrektywy opiera się na [wątku](../../../cpp/thread.md) atrybutu przy użyciu [__declspec](../../../cpp/declspec.md) — słowo kluczowe; limity `__declspec(thread)` dotyczą `threadprivate`.

Nie można użyć `threadprivate` w każdej biblioteki DLL, który zostanie załadowany za pośrednictwem [LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya).  Zakaz ten zawiera biblioteki dll, które są ładowane z [/delayload (Opóźnij importowanie ładowania)](../../../build/reference/delayload-delay-load-import.md), która także korzysta `LoadLibrary`.

Możesz użyć `threadprivate` w bibliotece DLL, który statycznie jest ładowany podczas uruchamiania procesu.

Ponieważ `threadprivate` opiera się na `__declspec(thread)`, `threadprivate` zmienna istnieje w żadnym z wątków pracę w toku, nie tylko te wątki, które są częścią zespołu wątku zduplikowany przez równoległego regionu.  Należy pamiętać o tym szczegółowo opisuje implementacja; Należy zauważyć, na przykład, że konstruktory `threadprivate` typu zdefiniowanego przez użytkownika są nazywane więcej często, a następnie oczekuje.

A `threadprivate` zmienną typu destructable nie jest gwarantowana mieć jej wywołania destruktora.  Na przykład:

```
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

Użytkownicy mają nie kontrolę tego kiedy spowoduje przerwanie działania wątków stanowiące równoległego regionu.  Jeśli te wątki istnieje podczas procesu, wątki nie zostaną powiadomieni o zakończenie procesu i destruktor nie będzie można wywołać dla `threaded_var` dotyczące dowolnego wątku, z wyjątkiem tego, który zamyka (tutaj, wątek główny).  Dlatego kod nie powinien liczyć na właściwe zniszczenie `threadprivate` zmiennych.

### <a name="example"></a>Przykład

Przykład użycia `threadprivate`, zobacz [prywatnej](openmp-clauses.md#private-openmp).
