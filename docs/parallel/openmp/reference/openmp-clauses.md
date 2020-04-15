---
title: Klauzule OpenMP
ms.date: 03/20/2019
f1_keywords:
- OpenMP clauses
- copyin
- copyprivate
- default
- firstprivate
- lastprivate
- nowait
- num_threads
- ordered
- private
- reduction
- schedule
- shared
helpviewer_keywords:
- OpenMP clauses
- copyin OpenMP clause
- copyprivate OpenMP clause
- default OpenMP clause
- defaults, OpenMP clause
- firstprivate OpenMP clause
- if OpenMP clause
- lastprivate OpenMP clause
- nowait OpenMP clause
- num_threads OpenMP clause
- ordered OpenMP clause
- private OpenMP clause
- reduction OpenMP clause
- schedule OpenMP clause
- shared OpenMP clause
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
ms.openlocfilehash: 1c4c7961a173eb47394d03e9aabdd14574e62b08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363898"
---
# <a name="openmp-clauses"></a>Klauzule OpenMP

Zawiera łącza do klauzul używanych w interfejsie API OpenMP.

Visual C++ obsługuje następujące klauzule OpenMP.

Dla atrybutów ogólnych:

|Klauzula|Opis|
|------|-----------|
|[if](#if-openmp)|Określa, czy pętla ma być wykonywana równolegle, czy szeregowo.|
|[num_threads](#num-threads)|Ustawia liczbę wątków w zespole wątków.|
|[Zamówione](#ordered-openmp-clauses)|Wymagane na równolegle [dla](openmp-directives.md#for-openmp) instrukcji, jeśli [uporządkowana](openmp-directives.md#ordered-openmp-directives) dyrektywa ma być używany w pętli.|
|[Harmonogram](#schedule)|Dotyczy dyrektywy [for.](openmp-directives.md#for-openmp)|
|[nowait](#nowait)|Zastępuje barierę niejawną w dyrektywie.|

W przypadku atrybutów udostępniania danych:

|Klauzula|Opis|
|------|-----------|
|[private](#private-openmp)|Określa, że każdy wątek powinien mieć własne wystąpienie zmiennej.|
|[firstprivate](#firstprivate)|Określa, że każdy wątek powinien mieć własne wystąpienie zmiennej i że zmienna powinna być inicjowana z wartością zmiennej, ponieważ istnieje przed konstrukcją równoległą.|
|[lastprivate](#lastprivate)|Określa, że otaczająca wersja kontekstu zmiennej jest równa wersji prywatnej wątku, który wykonuje ostateczną iterację (konstrukcja dla pętli) lub ostatnią sekcję (#pragma sekcje).|
|[Udostępnionych](#shared-openmp)|Określa, że jedna lub więcej zmiennych powinny być współużytkowane przez wszystkie wątki.|
|[default](#default-openmp)|Określa zachowanie zmiennych nieskopowych w regionie równoległym.|
|[reduction](#reduction)|Określa, że jedna lub więcej zmiennych, które są prywatne dla każdego wątku są przedmiotem operacji redukcji na końcu regionu równoległego.|
|[copyin](#copyin)|Umożliwia wątkom dostęp do wartości wątku głównego dla zmiennej [threadprivate.](openmp-directives.md#threadprivate)|
|[copyprivate](#copyprivate)|Określa, że jedna lub więcej zmiennych powinny być współużytkowane przez wszystkie wątki.|

## <a name="copyin"></a><a name="copyin"></a>copyin

Umożliwia wątkom dostęp do wartości wątku głównego dla zmiennej [threadprivate.](openmp-directives.md#threadprivate)

```cpp
copyin(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Zmienna, `threadprivate` która zostanie zainicjowana z wartością zmiennej w wątku głównym, ponieważ istnieje przed konstrukcją równoległą.

### <a name="remarks"></a>Uwagi

`copyin`ma zastosowanie do następujących dyrektyw:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [Sekcje](openmp-directives.md#sections-openmp)

Aby uzyskać więcej informacji, zobacz [2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md).

### <a name="example"></a>Przykład

Zobacz [threadprivate](openmp-directives.md#threadprivate) na przykład `copyin`przy użyciu .

## <a name="copyprivate"></a><a name="copyprivate"></a>Copyprivate

Określa, że jedna lub więcej zmiennych powinny być współużytkowane przez wszystkie wątki.

```cpp
copyprivate(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Co najmniej jedna zmienna do udostępnienia. Jeśli określono więcej niż jedną zmienną, należy oddzielić nazwy zmiennych przecinkiem.

### <a name="remarks"></a>Uwagi

`copyprivate`zastosowanie do [jednolitej](openmp-directives.md#single) dyrektywy.

Aby uzyskać więcej informacji, zobacz [2.7.2.8 copyprivate](../../../parallel/openmp/2-7-2-8-copyprivate.md).

### <a name="example"></a>Przykład

```cpp
// omp_copyprivate.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

float x, y, fGlobal = 1.0;
#pragma omp threadprivate(x, y)

float get_float() {
   fGlobal += 0.001;
   return fGlobal;
}

void use_float(float f, int t) {
   printf_s("Value = %f, thread = %d\n", f, t);
}

void CopyPrivate(float a, float b) {
   #pragma omp single copyprivate(a, b, x, y)
   {
      a = get_float();
      b = get_float();
      x = get_float();
      y = get_float();
    }

   use_float(a, omp_get_thread_num());
   use_float(b, omp_get_thread_num());
   use_float(x, omp_get_thread_num());
   use_float(y, omp_get_thread_num());
}

int main() {
   float a = 9.99, b = 123.456;

   printf_s("call CopyPrivate from a single thread\n");
   CopyPrivate(9.99, 123.456);

   printf_s("call CopyPrivate from a parallel region\n");
   #pragma omp parallel
   {
      CopyPrivate(a, b);
   }
}
```

```Output
call CopyPrivate from a single thread
Value = 1.001000, thread = 0
Value = 1.002000, thread = 0
Value = 1.003000, thread = 0
Value = 1.004000, thread = 0
call CopyPrivate from a parallel region
Value = 1.005000, thread = 0
Value = 1.005000, thread = 1
Value = 1.006000, thread = 0
Value = 1.006000, thread = 1
Value = 1.007000, thread = 0
Value = 1.007000, thread = 1
Value = 1.008000, thread = 0
Value = 1.008000, thread = 1
```

## <a name="default"></a><a name="default-openmp"></a>Domyślny

Określa zachowanie zmiennych nieskopowych w regionie równoległym.

```cpp
default(shared | none)
```

### <a name="remarks"></a>Uwagi

`shared`, która obowiązuje, `default` jeśli klauzula jest nieokreślona, oznacza, że każda zmienna w regionie równoległym będzie traktowana tak, jakby została określona za pomocą klauzuli [udostępnionej.](#shared-openmp) `none`oznacza, że wszystkie zmienne używane w regionie równoległym, które nie są objęte [zakresem](#private-openmp)z private , [shared](#shared-openmp), [reduction](#reduction), [firstprivate](#firstprivate)lub [lastprivate](#lastprivate) klauzuli spowoduje błąd kompilatora.

`default`ma zastosowanie do następujących dyrektyw:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [Sekcje](openmp-directives.md#sections-openmp)

Aby uzyskać więcej informacji, zobacz [2.7.2.5 default](../../../parallel/openmp/2-7-2-5-default.md).

### <a name="example"></a>Przykład

Zobacz [prywatny](#private-openmp) przykład użycia `default`.

## <a name="firstprivate"></a><a name="firstprivate"></a>Firstprivate

Określa, że każdy wątek powinien mieć własne wystąpienie zmiennej i że zmienna powinna być inicjowana z wartością zmiennej, ponieważ istnieje przed konstrukcją równoległą.

```cpp
firstprivate(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Zmienna, która ma wystąpienia w każdym wątku i która zostanie zainicjowana z wartością zmiennej, ponieważ istnieje przed konstrukcją równoległą. Jeśli określono więcej niż jedną zmienną, należy oddzielić nazwy zmiennych przecinkiem.

### <a name="remarks"></a>Uwagi

`firstprivate`ma zastosowanie do następujących dyrektyw:

- [for](openmp-directives.md#for-openmp)
- [parallel](openmp-directives.md#parallel)
- [Sekcje](openmp-directives.md#sections-openmp)
- [Pojedynczy](openmp-directives.md#single)

Aby uzyskać więcej informacji, zobacz [2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md).

### <a name="example"></a>Przykład

Na przykład za `firstprivate`pomocą , zobacz przykład w [prywatnych](#private-openmp).

## <a name="if-openmp"></a><a name="if-openmp"></a>jeśli (OpenMP)

Określa, czy pętla ma być wykonywana równolegle, czy szeregowo.

```cpp
if(expression)
```

### <a name="parameters"></a>Parametry

*Wyrażenie*<br/>
Wyrażenie integralne, które, jeśli ma wartość true (nonzero), powoduje, że kod w regionie równoległym jest wykonywany równolegle. Jeśli wyrażenie ma wartość false (zero), region równoległy jest wykonywany szeregowo (przez pojedynczy wątek).

### <a name="remarks"></a>Uwagi

`if`ma zastosowanie do następujących dyrektyw:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [Sekcje](openmp-directives.md#sections-openmp)

Aby uzyskać więcej informacji, zobacz [2.3 konstrukcja równoległa](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Przykład

```cpp
// omp_if.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void test(int val)
{
    #pragma omp parallel if (val)
    if (omp_in_parallel())
    {
        #pragma omp single
        printf_s("val = %d, parallelized with %d threads\n",
                 val, omp_get_num_threads());
    }
    else
    {
        printf_s("val = %d, serialized\n", val);
    }
}

int main( )
{
    omp_set_num_threads(2);
    test(0);
    test(2);
}
```

```Output
val = 0, serialized
val = 2, parallelized with 2 threads
```

## <a name="lastprivate"></a><a name="lastprivate"></a>Lastprivate

Określa, że otaczająca wersja kontekstu zmiennej jest równa wersji prywatnej wątku, który wykonuje ostateczną iterację (konstrukcja dla pętli) lub ostatnią sekcję (#pragma sekcje).

```cpp
lastprivate(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Zmienna, która jest równa wersji prywatnej wątku, który wykonuje ostateczną iterację (konstrukcja dla pętli) lub ostatnią sekcję (#pragma sekcje).

### <a name="remarks"></a>Uwagi

`lastprivate`ma zastosowanie do następujących dyrektyw:

- [for](openmp-directives.md#for-openmp)
- [Sekcje](openmp-directives.md#sections-openmp)

Aby uzyskać więcej informacji, zobacz [2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md).

### <a name="example"></a>Przykład

Zobacz [harmonogram](#schedule) na przykład `lastprivate` using klauzuli.

## <a name="nowait"></a><a name="nowait"></a>Nowait

Zastępuje barierę niejawną w dyrektywie.

```cpp
nowait
```

### <a name="remarks"></a>Uwagi

`nowait`ma zastosowanie do następujących dyrektyw:

- [for](openmp-directives.md#for-openmp)
- [Sekcje](openmp-directives.md#sections-openmp)
- [Pojedynczy](openmp-directives.md#single)

Aby uzyskać więcej informacji, zobacz [2.4.1 dla konstrukcji,](../../../parallel/openmp/2-4-1-for-construct.md) [2.4.2 sekcje konstrukcji](../../../parallel/openmp/2-4-2-sections-construct.md)i [2.4.3 pojedynczej konstrukcji.](../../../parallel/openmp/2-4-3-single-construct.md)

### <a name="example"></a>Przykład

```cpp
// omp_nowait.cpp
// compile with: /openmp /c
#include <stdio.h>

#define SIZE 5

void test(int *a, int *b, int *c, int size)
{
    int i;
    #pragma omp parallel
    {
        #pragma omp for nowait
        for (i = 0; i < size; i++)
            b[i] = a[i] * a[i];

        #pragma omp for nowait
        for (i = 0; i < size; i++)
            c[i] = a[i]/2;
    }
}

int main( )
{
    int a[SIZE], b[SIZE], c[SIZE];
    int i;

    for (i=0; i<SIZE; i++)
        a[i] = i;

    test(a,b,c, SIZE);

    for (i=0; i<SIZE; i++)
        printf_s("%d, %d, %d\n", a[i], b[i], c[i]);
}
```

```Output
0, 0, 0
1, 1, 0
2, 4, 1
3, 9, 1
4, 16, 2
```

## <a name="num_threads"></a><a name="num-threads"></a>Num_threads

Ustawia liczbę wątków w zespole wątków.

```cpp
num_threads(num)
```

### <a name="parameters"></a>Parametry

*num*<br/>
Liczba wątków

### <a name="remarks"></a>Uwagi

Klauzula `num_threads` ma taką samą funkcjonalność jak [funkcja omp_set_num_threads.](openmp-functions.md#omp-set-num-threads)

`num_threads`ma zastosowanie do następujących dyrektyw:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [Sekcje](openmp-directives.md#sections-openmp)

Aby uzyskać więcej informacji, zobacz [2.3 konstrukcja równoległa](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Przykład

Zobacz [równolegle](openmp-directives.md#parallel) na przykład `num_threads` using klauzuli.

## <a name="ordered"></a><a name="ordered-openmp-clauses"></a>Zamówione

Wymagane na równolegle [dla](openmp-directives.md#for-openmp) instrukcji, jeśli [uporządkowana](openmp-directives.md#ordered-openmp-directives) dyrektywa ma być używany w pętli.

```cpp
ordered
```

### <a name="remarks"></a>Uwagi

`ordered`ma zastosowanie do dyrektywy [for.](openmp-directives.md#for-openmp)

Aby uzyskać więcej informacji, zobacz [2.4.1 dla konstrukcji](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Przykład

Zobacz [uporządkowane](openmp-directives.md#ordered-openmp-directives) na przykład `ordered` przy użyciu klauzuli.

## <a name="private"></a><a name="private-openmp"></a>Prywatny

Określa, że każdy wątek powinien mieć własne wystąpienie zmiennej.

```cpp
private(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Zmienna ma wystąpienia w każdym wątku.

### <a name="remarks"></a>Uwagi

`private`ma zastosowanie do następujących dyrektyw:

- [for](openmp-directives.md#for-openmp)
- [parallel](openmp-directives.md#parallel)
- [Sekcje](openmp-directives.md#sections-openmp)
- [Pojedynczy](openmp-directives.md#single)

Więcej informacji można znaleźć w [2.7.2.1 private](../../../parallel/openmp/2-7-2-1-private.md).

### <a name="example"></a>Przykład

```c
// openmp_private.c
// compile with: /openmp
#include <windows.h>
#include <assert.h>
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define SLEEP_THREAD 1
#define NUM_LOOPS 2

enum Types {
   ThreadPrivate,
   Private,
   FirstPrivate,
   LastPrivate,
   Shared,
   MAX_TYPES
};

int nSave[NUM_THREADS][MAX_TYPES][NUM_LOOPS] = {{0}};
int nThreadPrivate;

#pragma omp threadprivate(nThreadPrivate)
#pragma warning(disable:4700)

int main() {
   int nPrivate = NUM_THREADS;
   int nFirstPrivate = NUM_THREADS;
   int nLastPrivate = NUM_THREADS;
   int nShared = NUM_THREADS;
   int nRet = 0;
   int i;
   int j;
   int nLoop = 0;

   nThreadPrivate = NUM_THREADS;
   printf_s("These are the variables before entry "
           "into the parallel region.\n");
   printf_s("nThreadPrivate = %d\n", nThreadPrivate);
   printf_s("      nPrivate = %d\n", nPrivate);
   printf_s(" nFirstPrivate = %d\n", nFirstPrivate);
   printf_s("  nLastPrivate = %d\n", nLastPrivate);
   printf_s("       nShared = %d\n\n", nShared);
   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel copyin(nThreadPrivate) private(nPrivate) shared(nShared) firstprivate(nFirstPrivate)
   {
      #pragma omp for schedule(static) lastprivate(nLastPrivate)
      for (i = 0 ; i < NUM_THREADS ; ++i) {
         for (j = 0 ; j < NUM_LOOPS ; ++j) {
            int nThread = omp_get_thread_num();
            assert(nThread < NUM_THREADS);

            if (nThread == SLEEP_THREAD)
               Sleep(100);
            nSave[nThread][ThreadPrivate][j] = nThreadPrivate;
            nSave[nThread][Private][j] = nPrivate;
            nSave[nThread][Shared][j] = nShared;
            nSave[nThread][FirstPrivate][j] = nFirstPrivate;
            nSave[nThread][LastPrivate][j] = nLastPrivate;
            nThreadPrivate = nThread;
            nPrivate = nThread;
            nShared = nThread;
            nLastPrivate = nThread;
            --nFirstPrivate;
         }
      }
   }

   for (i = 0 ; i < NUM_LOOPS ; ++i) {
      for (j = 0 ; j < NUM_THREADS ; ++j) {
         printf_s("These are the variables at entry of "
                  "loop %d of thread %d.\n", i + 1, j);
         printf_s("nThreadPrivate = %d\n",
                  nSave[j][ThreadPrivate][i]);
         printf_s("      nPrivate = %d\n",
                  nSave[j][Private][i]);
         printf_s(" nFirstPrivate = %d\n",
                  nSave[j][FirstPrivate][i]);
         printf_s("  nLastPrivate = %d\n",
                  nSave[j][LastPrivate][i]);
         printf_s("       nShared = %d\n\n",
                  nSave[j][Shared][i]);
      }
   }

   printf_s("These are the variables after exit from "
            "the parallel region.\n");
   printf_s("nThreadPrivate = %d (The last value in the "
            "master thread)\n", nThreadPrivate);
   printf_s("      nPrivate = %d (The value prior to "
            "entering parallel region)\n", nPrivate);
   printf_s(" nFirstPrivate = %d (The value prior to "
            "entering parallel region)\n", nFirstPrivate);
   printf_s("  nLastPrivate = %d (The value from the "
            "last iteration of the loop)\n", nLastPrivate);
   printf_s("       nShared = %d (The value assigned, "
            "from the delayed thread, %d)\n\n",
            nShared, SLEEP_THREAD);
}
```

```Output
These are the variables before entry into the parallel region.
nThreadPrivate = 4
      nPrivate = 4
nFirstPrivate = 4
  nLastPrivate = 4
       nShared = 4

These are the variables at entry of loop 1 of thread 0.
nThreadPrivate = 4
      nPrivate = 1310720
nFirstPrivate = 4
  nLastPrivate = 1245104
       nShared = 3

These are the variables at entry of loop 1 of thread 1.
nThreadPrivate = 4
      nPrivate = 4488
nFirstPrivate = 4
  nLastPrivate = 19748
       nShared = 0

These are the variables at entry of loop 1 of thread 2.
nThreadPrivate = 4
      nPrivate = -132514848
nFirstPrivate = 4
  nLastPrivate = -513199792
       nShared = 4

These are the variables at entry of loop 1 of thread 3.
nThreadPrivate = 4
      nPrivate = 1206
nFirstPrivate = 4
  nLastPrivate = 1204
       nShared = 2

These are the variables at entry of loop 2 of thread 0.
nThreadPrivate = 0
      nPrivate = 0
nFirstPrivate = 3
  nLastPrivate = 0
       nShared = 0

These are the variables at entry of loop 2 of thread 1.
nThreadPrivate = 1
      nPrivate = 1
nFirstPrivate = 3
  nLastPrivate = 1
       nShared = 1

These are the variables at entry of loop 2 of thread 2.
nThreadPrivate = 2
      nPrivate = 2
nFirstPrivate = 3
  nLastPrivate = 2
       nShared = 2

These are the variables at entry of loop 2 of thread 3.
nThreadPrivate = 3
      nPrivate = 3
nFirstPrivate = 3
  nLastPrivate = 3
       nShared = 3

These are the variables after exit from the parallel region.
nThreadPrivate = 0 (The last value in the master thread)
      nPrivate = 4 (The value prior to entering parallel region)
nFirstPrivate = 4 (The value prior to entering parallel region)
  nLastPrivate = 3 (The value from the last iteration of the loop)
       nShared = 1 (The value assigned, from the delayed thread, 1)
```

## <a name="reduction"></a><a name="reduction"></a>Redukcji

Określa, że jedna lub więcej zmiennych, które są prywatne dla każdego wątku są przedmiotem operacji redukcji na końcu regionu równoległego.

```cpp
reduction(operation:var)
```

### <a name="parameters"></a>Parametry

*Operacji*<br/>
Operator operacji do wykonania na zmiennych *var* na końcu regionu równoległego.

*var*<br/>
Co najmniej jedna zmienna, na której ma być skalarna redukcja. Jeśli określono więcej niż jedną zmienną, należy oddzielić nazwy zmiennych przecinkiem.

### <a name="remarks"></a>Uwagi

`reduction`ma zastosowanie do następujących dyrektyw:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [Sekcje](openmp-directives.md#sections-openmp)

Więcej informacji można znaleźć w [2.7.2.6 redukcja](../../../parallel/openmp/2-7-2-6-reduction.md).

### <a name="example"></a>Przykład

```cpp
// omp_reduction.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define SUM_START   1
#define SUM_END     10
#define FUNC_RETS   {1, 1, 1, 1, 1}

int bRets[5] = FUNC_RETS;
int nSumCalc = ((SUM_START + SUM_END) * (SUM_END - SUM_START + 1)) / 2;

int func1( ) {return bRets[0];}
int func2( ) {return bRets[1];}
int func3( ) {return bRets[2];}
int func4( ) {return bRets[3];}
int func5( ) {return bRets[4];}

int main( )
{
    int nRet = 0,
        nCount = 0,
        nSum = 0,
        i,
        bSucceed = 1;

    omp_set_num_threads(NUM_THREADS);

    #pragma omp parallel reduction(+ : nCount)
    {
        nCount += 1;

        #pragma omp for reduction(+ : nSum)
        for (i = SUM_START ; i <= SUM_END ; ++i)
            nSum += i;

        #pragma omp sections reduction(&& : bSucceed)
        {
            #pragma omp section
            {
                bSucceed = bSucceed && func1( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func2( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func3( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func4( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func5( );
            }
        }
    }

    printf_s("The parallel section was executed %d times "
             "in parallel.\n", nCount);
    printf_s("The sum of the consecutive integers from "
             "%d to %d, is %d\n", 1, 10, nSum);

    if (bSucceed)
        printf_s("All of the functions, func1 through "
                 "func5 succeeded!\n");
    else
        printf_s("One or more of the functions, func1 "
                 "through func5 failed!\n");

    if (nCount != NUM_THREADS)
    {
        printf_s("ERROR: For %d threads, %d were counted!\n",
                 NUM_THREADS, nCount);
        nRet |= 0x1;
   }

    if (nSum != nSumCalc)
    {
        printf_s("ERROR: The sum of %d through %d should be %d, "
                "but %d was reported!\n",
                SUM_START, SUM_END, nSumCalc, nSum);
        nRet |= 0x10;
    }

    if (bSucceed != (bRets[0] && bRets[1] &&
                     bRets[2] && bRets[3] && bRets[4]))
    {
        printf_s("ERROR: The sum of %d through %d should be %d, "
                 "but %d was reported!\n",
                 SUM_START, SUM_END, nSumCalc, nSum);
        nRet |= 0x100;
    }
}
```

```Output
The parallel section was executed 4 times in parallel.
The sum of the consecutive integers from 1 to 10, is 55
All of the functions, func1 through func5 succeeded!
```

## <a name="schedule"></a><a name="schedule"></a>Harmonogram

Dotyczy dyrektywy [for.](openmp-directives.md#for-openmp)

```cpp
schedule(type[,size])
```

### <a name="parameters"></a>Parametry

*Typu*<br/>
`dynamic`Rodzaj planowania, albo , `guided`, `runtime`, `static`lub .

*Rozmiar*<br/>
(Opcjonalnie) Określa rozmiar iteracji. *rozmiar* musi być liczeniem całkowitym. Nieprawidłowe, *type* gdy `runtime`typ jest .

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [2.4.1 dla konstrukcji](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Przykład

```cpp
// omp_schedule.cpp
// compile with: /openmp
#include <windows.h>
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define STATIC_CHUNK 5
#define DYNAMIC_CHUNK 5
#define NUM_LOOPS 20
#define SLEEP_EVERY_N 3

int main( )
{
    int nStatic1[NUM_LOOPS],
        nStaticN[NUM_LOOPS];
    int nDynamic1[NUM_LOOPS],
        nDynamicN[NUM_LOOPS];
    int nGuided[NUM_LOOPS];

    omp_set_num_threads(NUM_THREADS);

    #pragma omp parallel
    {
        #pragma omp for schedule(static, 1)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nStatic1[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(static, STATIC_CHUNK)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nStaticN[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(dynamic, 1)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nDynamic1[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(dynamic, DYNAMIC_CHUNK)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nDynamicN[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(guided)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nGuided[i] = omp_get_thread_num( );
        }
    }

    printf_s("------------------------------------------------\n");
    printf_s("| static | static | dynamic | dynamic | guided |\n");
    printf_s("|    1   |    %d   |    1    |    %d    |        |\n",
             STATIC_CHUNK, DYNAMIC_CHUNK);
    printf_s("------------------------------------------------\n");

    for (int i=0; i<NUM_LOOPS; ++i)
    {
        printf_s("|    %d   |    %d   |    %d    |    %d    |"
                 "    %d   |\n",
                 nStatic1[i], nStaticN[i],
                 nDynamic1[i], nDynamicN[i], nGuided[i]);
    }

    printf_s("------------------------------------------------\n");
}
```

```Output
------------------------------------------------
| static | static | dynamic | dynamic | guided |
|    1   |    5   |    1    |    5    |        |
------------------------------------------------
|    0   |    0   |    0    |    2    |    1   |
|    1   |    0   |    3    |    2    |    1   |
|    2   |    0   |    3    |    2    |    1   |
|    3   |    0   |    3    |    2    |    1   |
|    0   |    0   |    2    |    2    |    1   |
|    1   |    1   |    2    |    3    |    3   |
|    2   |    1   |    2    |    3    |    3   |
|    3   |    1   |    0    |    3    |    3   |
|    0   |    1   |    0    |    3    |    3   |
|    1   |    1   |    0    |    3    |    2   |
|    2   |    2   |    1    |    0    |    2   |
|    3   |    2   |    1    |    0    |    2   |
|    0   |    2   |    1    |    0    |    3   |
|    1   |    2   |    2    |    0    |    3   |
|    2   |    2   |    2    |    0    |    0   |
|    3   |    3   |    2    |    1    |    0   |
|    0   |    3   |    3    |    1    |    1   |
|    1   |    3   |    3    |    1    |    1   |
|    2   |    3   |    3    |    1    |    1   |
|    3   |    3   |    0    |    1    |    3   |
------------------------------------------------
```

## <a name="shared"></a><a name="shared-openmp"></a>Udostępnionych

Określa, że jedna lub więcej zmiennych powinny być współużytkowane przez wszystkie wątki.

```cpp
shared(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Co najmniej jedna zmienna do udostępnienia. Jeśli określono więcej niż jedną zmienną, należy oddzielić nazwy zmiennych przecinkiem.

### <a name="remarks"></a>Uwagi

Innym sposobem udostępniania zmiennych między wątkami jest z [copyprivate klauzuli.](#copyprivate)

`shared`ma zastosowanie do następujących dyrektyw:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [Sekcje](openmp-directives.md#sections-openmp)

Aby uzyskać więcej informacji, zobacz [2.7.2.4 udostępnione](../../../parallel/openmp/2-7-2-4-shared.md).

### <a name="example"></a>Przykład

Zobacz [prywatny](#private-openmp) przykład użycia `shared`.
