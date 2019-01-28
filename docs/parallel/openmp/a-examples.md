---
title: A. Przykłady
ms.date: 01/18/2019
ms.assetid: c0f6192f-a205-449b-b84c-cb30dbcc8b8f
ms.openlocfilehash: 061490d34829175bfbdcd84d6208aa396bb19671
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087304"
---
# <a name="a-examples"></a>A. Przykłady

Poniżej przedstawiono przykłady konstrukcje zdefiniowane w tym dokumencie. Instrukcja następujące dyrektywy jest złożone, tylko wtedy, gdy jest to konieczne, a tworzone jest wcięcie instrukcję bez złożony z dyrektywą przed nim.

## <a name="a1-a-simple-loop-in-parallel"></a>A.1 A prostej pętli równoległych

Poniższy przykład pokazuje, jak zrównoleglić pętlę przy użyciu [równoległe w](2-directives.md#251-parallel-for-construct) dyrektywy. Zmienna iteracji pętli jest domyślnie prywatny, dzięki czemu nie trzeba jawnie określić je w klauzuli prywatnej.

```cpp
#pragma omp parallel for
    for (i=1; i<n; i++)
        b[i] = (a[i] + a[i-1]) / 2.0;
```

## <a name="a2-conditional-compilation"></a>A.2 kompilacja warunkowa

Poniższe przykłady pokazują korzystanie z kompilacji warunkowej, użycie makra OpenMP [_OPENMP](2-directives.md#22-conditional-compilation). Za pomocą kompilacji OpenMP `_OPENMP` makro staje się zdefiniowane.

```cpp
# ifdef _OPENMP
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

Zdefiniowane — operator preprocesora umożliwia więcej niż jednego makro testować w pojedynczej dyrektywy.

```cpp
# if defined(_OPENMP) && defined(VERBOSE)
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

## <a name="a3-parallel-regions"></a>A.3 regionów równoległych

[Równoległe](2-directives.md#23-parallel-construct) dyrektywa może być używana w zgrubnym ziarna programów do równoległego przetwarzania. W poniższym przykładzie każdy wątek w równoległego regionu decyduje, jaka część globalnej tablicy `x` do pracy, na podstawie liczby wątków:

```cpp
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)
{
    iam = omp_get_thread_num();
    np =  omp_get_num_threads();
    ipoints = npoints / np;
    subdomain(x, iam, ipoints);
}
```

## <a name="a4-the-nowait-clause"></a>A.4 klauzuli nowait

Jeśli istnieje wiele niezależnych pętli w ramach równoległego regionu, możesz użyć [nowait](2-directives.md#241-for-construct) klauzulę, aby uniknąć dorozumianych barierę na końcu `for` dyrektywy w następujący sposób:

```cpp
#pragma omp parallel
{
    #pragma omp for nowait
        for (i=1; i<n; i++)
             b[i] = (a[i] + a[i-1]) / 2.0;
    #pragma omp for nowait
        for (i=0; i<m; i++)
            y[i] = sqrt(z[i]);
}
```

## <a name="a5-the-critical-directive"></a>A.5 dyrektywy critical

Poniższy przykład zawiera kilka [krytyczne](2-directives.md#262-critical-construct) dyrektywy. W przykładzie pokazano kolejkowania modelu, w którym zadanie jest usuwane z kolejki i pracuje. Aby zabezpieczyć się przed wiele wątków tego samego zadania usuwania z kolejki, operacji usuwania z kolejki musi należeć do `critical` sekcji. Ponieważ dwie kolejki w tym przykładzie są niezależne, jest chroniony przez `critical` dyrektywy pod różnymi nazwami *liczbowa* i *yaxis*.

```cpp
#pragma omp parallel shared(x, y) private(x_next, y_next)
{
    #pragma omp critical ( xaxis )
        x_next = dequeue(x);
    work(x_next);
    #pragma omp critical ( yaxis )
        y_next = dequeue(y);
    work(y_next);
}
```

## <a name="a6-the-lastprivate-clause"></a>A.6 klauzuli lastprivate

Czasami prawidłowe wykonanie zależy od wartości ostatniej iteracji pętli jest przypisywany do zmiennej. Programów, które musi zawierać takich zmiennych jako argumenty [lastprivate](2-directives.md#2723-lastprivate) klauzuli tak, aby wartości zmiennych są takie same jak kiedy pętla jest wykonywana sekwencyjnie.

```cpp
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

W poprzednim przykładzie wartość `i` na końcu równoległego regionu będzie równa `n-1`, jak w przypadku sekwencyjnych.

## <a name="a7-the-reduction-clause"></a>A.7 klauzuli reduction

W poniższym przykładzie pokazano [redukcji](2-directives.md#2726-reduction) klauzuli:

```cpp
#pragma omp parallel for private(i) shared(x, y, n) \
                         reduction(+: a, b)
    for (i=0; i<n; i++) {
        a = a + x[i];
        b = b + y[i];
    }
```

## <a name="a8-parallel-sections"></a>A.8 sekcji równoległych

W poniższym przykładzie (dla [sekcji 2.4.2](2-directives.md#242-sections-construct)), funkcje *liczbowa*, *yaxis*, i *zaxis* mogą być wykonywane jednocześnie. Pierwszy `section` dyrektywa jest opcjonalne.  Wszystkie `section` dyrektyw, musi ono być widoczne w zakresie leksykalnym `parallel sections` konstruowania.

```cpp
#pragma omp parallel sections
{
    #pragma omp section
        xaxis();
    #pragma omp section
        yaxis();
    #pragma omp section
        zaxis();
}
```

## <a name="a9-single-directives"></a>A.9 pojedynczej dyrektywy

W poniższym przykładzie pokazano [pojedynczego](2-directives.md#243-single-construct) dyrektywy. W przykładzie, tylko jednego wątku (zazwyczaj pierwszy wątek napotka `single` dyrektywy) wyświetla komunikat o postępie. Użytkownik musi nie należy czynić żadnych założeń jako do wątku, który będzie wykonywał `single` sekcji. Wszystkie inne wątki pozwoli na pominięcie `single` sekcji, a następnie zatrzyma barierę na końcu `single` konstruowania. Jeśli inne wątki mogą kontynuować bez oczekiwania na wykonanie wątku `single` sekcji `nowait` można określić klauzuli w `single` dyrektywy.

```cpp
#pragma omp parallel
{
    #pragma omp single
        printf_s("Beginning work1.\n");
    work1();
    #pragma omp single
        printf_s("Finishing work1.\n");
    #pragma omp single nowait
        printf_s("Finished work1 and beginning work2.\n");
    work2();
}
```

## <a name="a10-sequential-ordering"></a>A.10 porządku porządkowanie sekwencyjne

[Uporządkowane sekcje](2-directives.md#266-ordered-construct) są przydatne w przypadku sekwencyjne porządkowanie danych wyjściowych z pracy, która została wykonana równolegle. Indeksy w kolejności sekwencyjnej wyświetla następujący program:

```cpp
#pragma omp for ordered schedule(dynamic)
    for (i=lb; i<ub; i+=st)
        work(i);
void work(int k)
{
    #pragma omp ordered
        printf_s(" %d", k);
}
```

## <a name="a11-a-fixed-number-of-threads"></a>A.11 A stałej liczby wątków

Niektóre programy, zależy od stałej, prespecified liczbę wątków jest wykonywany poprawnie.  Ustawieniem domyślnym dla dynamicznego dostosowania liczby wątków jest zdefiniowane w implementacji, programów, które można wyłączyć możliwość dynamicznego wątków i ustaw liczbę wątków, które jawnie, aby zachować przenoszenia. Poniższy przykład pokazuje, jak to zrobić za pomocą [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function), i [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function):

```cpp
omp_set_dynamic(0);
omp_set_num_threads(16);
#pragma omp parallel shared(x, npoints) private(iam, ipoints)
{
    if (omp_get_num_threads() != 16)
      abort();
    iam = omp_get_thread_num();
    ipoints = npoints/16;
    do_by_16(x, iam, ipoints);
}
```

W tym przykładzie program będzie działać prawidłowo tylko wtedy, gdy jest wykonywana przez 16 wątki. Jeśli wdrożenia nie może obsłużyć 16 wątków, zachowanie w tym przykładzie jest zdefiniowane w implementacji.

Liczba wątków wykonywania równoległego regionu pozostają stałe podczas równoległego regionu, niezależnie od tego, wątki dynamicznej, ustawienie. Mechanizm dynamiczne wątków określa liczbę wątków używanych podczas uruchamiania równoległego regionu i utrzymuje stały czas trwania regionu.

## <a name="a12-the-atomic-directive"></a>A.12 dyrektywy niepodzielnej

Poniższy przykład pozwala uniknąć wyścigu (równoczesnych aktualizacji elementu *x* przez wiele wątków) przy użyciu [atomic](2-directives.md#264-atomic-construct) dyrektywy:

```cpp
#pragma omp parallel for shared(x, y, index, n)
    for (i=0; i<n; i++)
    {
        #pragma omp atomic
            x[index[i]] += work1(i);
        y[i] += work2(i);
    }
```

Zaletą korzystania z `atomic` dyrektywy w tym przykładzie jest możliwość aktualizacji dwóch różnych elementów x są wykonywane równolegle. Jeśli [krytyczne](2-directives.md#262-critical-construct) — dyrektywa zamian jest używana, a następnie aktualizuje wszystkie elementy *x* są wykonywane szeregowo (choć nie w żadnym gwarantowana kolejność).

`atomic` Dyrektywy dotyczy tylko instrukcja C lub C++ następujący bezpośrednio po nim.  W rezultacie elementy *y* nie zostaną zaktualizowane niepodzielne w tym przykładzie.

## <a name="a13-a-flush-directive-with-a-list"></a>A.13 A dyrektywy flush z listą

W poniższym przykładzie użyto `flush` dyrektywę dla typu punkt-punkt synchronizacji określonych obiektów między parami wątków:

```cpp
int   sync[NUMBER_OF_THREADS];
float work[NUMBER_OF_THREADS];
#pragma omp parallel private(iam,neighbor) shared(work,sync)
{
    iam = omp_get_thread_num();
    sync[iam] = 0;
    #pragma omp barrier

    // Do computation into my portion of work array
    work[iam] = ...;

    //  Announce that I am done with my work
    // The first flush ensures that my work is
    // made visible before sync.
    // The second flush ensures that sync is made visible.
    #pragma omp flush(work)
    sync[iam] = 1;
    #pragma omp flush(sync)

    // Wait for neighbor
    neighbor = (iam>0 ? iam : omp_get_num_threads()) - 1;
    while (sync[neighbor]==0)
    {
        #pragma omp flush(sync)
    }

    // Read neighbor's values of work array
    ... = work[neighbor];
}
```

## <a name="a14-a-flush-directive-without-a-list"></a>A.14 A dyrektywy flush bez listy

Poniższy przykład (dla [sekcji 2.6.5](2-directives.md#265-flush-directive)) rozróżnia obiekty udostępnione wpływ `flush` dyrektywy z nie listy obiektów udostępnionych, które nie ma wpływu na:

```cpp
// omp_flush_without_list.c
#include <omp.h>

int x, *p = &x;

void f1(int *q)
{
    *q = 1;
    #pragma omp flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

void f2(int *q)
{
    #pragma omp barrier
    *q = 2;

    #pragma omp barrier
    // a barrier implies a flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

int g(int n)
{
    int i = 1, j, sum = 0;
    *p = 1;

    #pragma omp parallel reduction(+: sum) num_threads(10)
    {
        f1(&j);
        // i, n and sum were not flushed
        //   because they were not accessible in f1
        // j was flushed because it was accessible
        sum += j;
        f2(&j);
        // i, n, and sum were not flushed
        //   because they were not accessible in f2
        // j was flushed because it was accessible
        sum += i + j + *p + n;
    }
    return sum;
}

int main()
{
}
```

## <a name="a15-the-number-of-threads-used"></a>A.15 liczby wykorzystywanych wątków

Rozważmy następujący przykład niepoprawny (dla [sekcji 3.1.2](3-run-time-library-functions.md#312-omp_get_num_threads-function)):

```cpp
np = omp_get_num_threads(); // misplaced
#pragma omp parallel for schedule(static)
    for (i=0; i<np; i++)
        work(i);
```

`omp_get_num_threads()` Wywołania zwraca 1 serial sekcji kodu, więc *potoki* zawsze będzie równy 1 w powyższym przykładzie. Aby określić liczbę wątków, które zostaną wdrożone do równoległego regionu, wywołanie powinno być w ramach równoległego regionu.

Poniższy przykład pokazuje, jak ponownie zapisać ten program bez uwzględniania zapytanie dotyczące liczby wątków:

```cpp
#pragma omp parallel private(i)
{
    i = omp_get_thread_num();
    work(i);
}
```

## <a name="a16-locks"></a>A.16 blokad

W poniższym przykładzie (dla [sekcji 3.2](3-run-time-library-functions.md#32-lock-functions)), typ argumentu dla funkcji blokady powinien być `omp_lock_t`, i że nie ma potrzeby opróżnić go.  Funkcje blokady spowodować, że wątki ze stanu bezczynności podczas oczekiwania na wpis do pierwszej sekcję krytyczną, ale także wykonywanie innych zadań podczas oczekiwania na zapis do drugiego.  `omp_set_lock` Bloków funkcji, ale `omp_test_lock` funkcja nie jest zaznaczone, dzięki czemu praca w `skip()` do zrobienia.

```cpp
// omp_using_locks.c
// compile with: /openmp /c
#include <stdio.h>
#include <omp.h>

void work(int);
void skip(int);

int main() {
   omp_lock_t lck;
   int id;

   omp_init_lock(&lck);
   #pragma omp parallel shared(lck) private(id)
   {
      id = omp_get_thread_num();

      omp_set_lock(&lck);
      printf_s("My thread id is %d.\n", id);

      // only one thread at a time can execute this printf
      omp_unset_lock(&lck);

      while (! omp_test_lock(&lck)) {
         skip(id);   // we do not yet have the lock,
                     // so we must do something else
      }
      work(id);     // we now have the lock
                    // and can do the work
      omp_unset_lock(&lck);
   }
   omp_destroy_lock(&lck);
}
```

## <a name="a17-nestable-locks"></a>A.17 Zagnieżdżalnych blokad

Poniższy przykład (dla [sekcji 3.2](3-run-time-library-functions.md#32-lock-functions)) pokazuje, jak zagnieżdżalnych blokady może służyć do synchronizowania aktualizacji zarówno do całej struktury, jak i do jednej z jej członków.

```cpp
#include <omp.h>
typedef struct {int a,b; omp_nest_lock_t lck;} pair;

void incr_a(pair *p, int a)
{
    // Called only from incr_pair, no need to lock.
    p->a += a;
}

void incr_b(pair *p, int b)
{
    // Called both from incr_pair and elsewhere,
    // so need a nestable lock.

    omp_set_nest_lock(&p->lck);
    p->b += b;
    omp_unset_nest_lock(&p->lck);
}

void incr_pair(pair *p, int a, int b)
{
    omp_set_nest_lock(&p->lck);
    incr_a(p, a);
    incr_b(p, b);
    omp_unset_nest_lock(&p->lck);
}

void f(pair *p)
{
    extern int work1(), work2(), work3();
    #pragma omp parallel sections
    {
        #pragma omp section
            incr_pair(p, work1(), work2());
        #pragma omp section
            incr_b(p, work3());
    }
}
```

## <a name="a18-nested-for-directives"></a>Zagnieżdżone A.18 dla dyrektyw

Poniższy przykład `for` [zagnieżdżanie dyrektywy](2-directives.md#29-directive-nesting) jest zgodne, ponieważ wewnętrznych i zewnętrznych `for` dyrektywy powiązać z różnych regionów równoległych:

```cpp
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
        {
            #pragma omp parallel shared(i, n)
            {
                #pragma omp for
                    for (j=0; j<n; j++)
                        work(i, j);
            }
        }
}
```

Następujące zmiany powyższego przykładu jest również zgodne:

```cpp
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
            work1(i, n);
}

void work1(int i, int n)
{
    int j;
    #pragma omp parallel default(shared)
    {
        #pragma omp for
            for (j=0; j<n; j++)
                work2(i, j);
    }
    return;
}
```

## <a name="a19-examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19 przykłady pokazujące nieprawidłowe zagnieżdżanie podziału pracy dyrektywy

W przykładach w tej sekcji pokazano [zagnieżdżanie dyrektywy](2-directives.md#29-directive-nesting) reguły.

Poniższy przykład jest niezgodne ponieważ wewnętrznych i zewnętrznych `for` dyrektywy są gnieżdżone i powiązania do tej samej `parallel` dyrektywy:

```cpp
void wrong1(int n)
{
  #pragma omp parallel default(shared)
  {
      int i, j;
      #pragma omp for
      for (i=0; i<n; i++) {
          #pragma omp for
              for (j=0; j<n; j++)
                 work(i, j);
     }
   }
}
```

Następująca wersja dynamicznie zagnieżdżonych powyższego przykładu jest również niezgodne:

```cpp
void wrong2(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++)
        work1(i, n);
  }
}

void work1(int i, int n)
{
  int j;
  #pragma omp for
    for (j=0; j<n; j++)
      work2(i, j);
}
```

Poniższy przykład jest niezgodne ponieważ `for` i `single` dyrektywy są zagnieżdżone, a następnie powiązać ten sam równoległego regionu:

```cpp
void wrong3(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        #pragma omp single
          work(i);
      }
  }
}
```

Poniższy przykład jest niezgodne ponieważ `barrier` dyrektywy wewnątrz `for` może doprowadzić do zakleszczenia:

```cpp
void wrong4(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        work1(i);
        #pragma omp barrier
        work2(i);
      }
  }
}
```

Poniższy przykład jest niezgodne ponieważ `barrier` skutkuje zakleszczenie z faktu, że tylko jeden wątek jednocześnie można wprowadzić sekcję krytyczną:

```cpp
void wrong5()
{
  #pragma omp parallel
  {
    #pragma omp critical
    {
       work1();
       #pragma omp barrier
       work2();
    }
  }
}
```

Poniższy przykład jest niezgodne ponieważ `barrier` skutkuje zakleszczenie z faktu, że tylko jeden wątek wykonuje `single` sekcji:

```cpp
void wrong6()
{
  #pragma omp parallel
  {
    setup();
    #pragma omp single
    {
      work1();
      #pragma omp barrier
      work2();
    }
    finish();
  }
}
```

## <a name="a20-bind-barrier-directives"></a>A.20 powiązanie barierę dyrektywy

Powiązania dyrektywy reguł wywołanie `barrier` dyrektywy, aby powiązać najbliższej otaczającej `parallel` dyrektywy. Aby uzyskać więcej informacji na temat powiązania dyrektywy, zobacz [sekcji 2.8](2-directives.md#28-directive-binding).

W poniższym przykładzie, wywołanie funkcji z *głównego* do *sub2* jest zgodne, ponieważ `barrier` (w *sub3*) wiąże równoległego regionu w *sub2* . Wywołanie funkcji z *głównego* do *sub1* jest zgodne, ponieważ `barrier` wiąże równoległego regionu w podprocedury *sub2*.  Wywołanie funkcji z *głównego* do *sub3* jest zgodne, ponieważ `barrier` nie jest powiązana do dowolnego regionu równoległe i jest ignorowana. Ponadto `barrier` synchronizuje tylko zespół wątków w otaczającej równoległego regionu i nie wszystkie wątki, które są tworzone w *sub1*.

```cpp
int main()
{
    sub1(2);
    sub2(2);
    sub3(2);
}

void sub1(int n)
{
    int i;
    #pragma omp parallel private(i) shared(n)
    {
        #pragma omp for
        for (i=0; i<n; i++)
            sub2(i);
    }
}

void sub2(int k)
{
     #pragma omp parallel shared(k)
     sub3(k);
}

void sub3(int n)
{
    work(n);
    #pragma omp barrier
    work(n);
}
```

## <a name="a21-scope-variables-with-the-private-clause"></a>A.21 zmienne zakresu z klauzulą prywatną

Wartości `i` i `j` w poniższym przykładzie zdefiniowano przy zamykaniu z równoległego regionu:

```cpp
int i, j;
i = 1;
j = 2;
#pragma omp parallel private(i) firstprivate(j)
{
  i = 3;
  j = j + 2;
}
printf_s("%d %d\n", i, j);
```

Aby uzyskać więcej informacji na temat `private` klauzuli, zobacz [sekcji 2.7.2.1](2-directives.md#2721-private).

## <a name="a22-the-defaultnone-clause"></a>A.22 klauzulą default(none)

Poniższy przykład wyróżnia zmienne, których dotyczy `default(none)` klauzuli ze zmiennych, które nie są:

```cpp
// openmp_using_clausedefault.c
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int x, y, z[1000];
#pragma omp threadprivate(x)

void fun(int a) {
   const int c = 1;
   int i = 0;

   #pragma omp parallel default(none) private(a) shared(z)
   {
      int j = omp_get_num_thread();
             //O.K.  - j is declared within parallel region
      a = z[j];       // O.K.  - a is listed in private clause
                      //      - z is listed in shared clause
      x = c;          // O.K.  - x is threadprivate
                      //      - c has const-qualified type
      z[i] = y;       // C3052 error - cannot reference i or y here

      #pragma omp for firstprivate(y)
         for (i=0; i<10 ; i++) {
            z[i] = y;  // O.K. - i is the loop control variable
                       // - y is listed in firstprivate clause
          }
       z[i] = y;   // Error - cannot reference i or y here
   }
}
```

Aby uzyskać więcej informacji na temat `default` klauzuli, zobacz [sekcji 2.7.2.5](2-directives.md#2725-default).

## <a name="a23-examples-of-the-ordered-directive"></a>A.23 przykłady dyrektyw uporządkowanych

Można mieć wiele uporządkowanych sekcje z `for` określenia `ordered` klauzuli. Pierwszy przykład jest niezgodne, ponieważ interfejs API określa następujące reguły:

"Iteracji pętli za pomocą `for` konstrukcja nie należy wykonać takie same `ordered` dyrektywy więcej niż jeden raz, a nie musisz wykonać więcej niż jedną `ordered` dyrektywy." (Zobacz [sekcji 2.6.6](2-directives.md#266-ordered-construct).)

W tym przykładzie niezgodnych wszystkich iteracji wykonać dwie sekcje uporządkowane:

```cpp
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    #pragma omp ordered
    { ... }
    ...
    #pragma omp ordered
    { ... }
    ...
}
```

W poniższym przykładzie zgodne przedstawiono `for` z więcej niż jednym uporządkowane sekcji:

```cpp
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    if (i <= 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
    (i > 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
}
```

## <a name="a24-example-of-the-private-clause"></a>A.24 przykład klauzuli prywatnej

[Prywatnej](2-directives.md#2721-private) klauzuli równoległego regionu działa tylko w dla zakresu leksykalne regionu, a nie dla zakresu dynamicznego regionu.  W związku z tym w następującym przykładzie, wszelkie używa zmiennej *a* w `for` pętli w procedurze *f* odwołuje się do prywatnej kopii *a*, podczas użycia w Procedura *g* odwołuje się do globalnej *a*.

```cpp
int a;

void f(int n)
{
    a = 0;

    #pragma omp parallel for private(a)
    for (int i=1; i<n; i++)
    {
        a = i;
        g(i, n);
        d(a);     // Private copy of "a"
        ...
    }
    ...

void g(int k, int n)
{
    h(k,a); // The global "a", not the private "a" in f
}
```

## <a name="a25-examples-of-the-copyprivate-data-attribute-clause"></a>A.25 przykłady klauzuli atrybutu danych prywatnej kopii

**Przykład 1:** [Copyprivate](2-directives.md#2728-copyprivate) klauzuli może służyć do emisji wartości uzyskanych przez pojedynczy wątek bezpośrednio do wszystkich wystąpień w zmiennych prywatnych w innych wątków.

```cpp
float x, y;
#pragma omp threadprivate(x, y)

void init( )
{
    float a;
    float b;

    #pragma omp single copyprivate(a,b,x,y)
    {
        get_values(a,b,x,y);
    }

    use_values(a, b, x, y);
}
```

W przypadku rutynowych *init* jest wywoływana z regionu szeregowe, jego zachowanie nie ma wpływu na obecność dyrektywy. Po wywołaniu *get_values* procedury zostało wykonane przez jeden wątek, żadnego wątku pozostawia konstrukcja do prywatnego obiekty wskazywany przez *a*, *b*, *x*, i *y* w wszystkie wątki zdefiniowano stają się przy użyciu wartości do odczytu.

**Przykład 2:** W przeciwieństwie do poprzedniego przykładu załóżmy, że odczytu muszą być wykonywane przez określonego wątku, załóżmy, że głównego wątku. W tym przypadku `copyprivate` nie można używać klauzuli w celu emisji bezpośrednio, ale może służyć do zapewnienia dostępu do udostępnionych obiektów tymczasowych.

```cpp
float read_next( )
{
    float * tmp;
    float return_val;

    #pragma omp single copyprivate(tmp)
    {
        tmp = (float *) malloc(sizeof(float));
    }

    #pragma omp master
    {
        get_float( tmp );
    }

    #pragma omp barrier
    return_val = *tmp;
    #pragma omp barrier

    #pragma omp single
    {
       free(tmp);
    }

    return return_val;
}
```

**Przykład 3:** Załóżmy, że liczba obiektów blokady wymaganymi w ramach równoległego regionu łatwo nie można ustalić przed jej wprowadzeniem. `copyprivate` Klauzuli może służyć do zapewnienia dostępu do blokady współużytkowanej obiektów, które są przydzielane w ramach równoległego regionu.

```cpp
#include <omp.h>

omp_lock_t *new_lock()
{
    omp_lock_t *lock_ptr;

    #pragma omp single copyprivate(lock_ptr)
    {
        lock_ptr = (omp_lock_t *) malloc(sizeof(omp_lock_t));
        omp_init_lock( lock_ptr );
    }

    return lock_ptr;
}
```

## <a name="a26-the-threadprivate-directive"></a>A.26 dyrektywy threadprivate

W poniższych przykładach pokazano sposób użycia [threadprivate](2-directives.md#271-threadprivate-directive) dyrektywy, aby nadać każdy wątek oddzielne licznika.

### <a name="example-1"></a>Przykład 1

```cpp
int counter = 0;
#pragma omp threadprivate(counter)

int sub()
{
    counter++;
    return(counter);
}
```

### <a name="example-2"></a>Przykład 2

```cpp
int sub()
{
    static int counter = 0;
    #pragma omp threadprivate(counter)
    counter++;
    return(counter);
}
```

## <a name="a27-c99-variable-length-arrays"></a>A.27 C99 o zmiennej długości tablic

Poniższy przykład pokazuje sposób użycia tablice o długości zmiennej C99 (VLAs) w [firstprivate](2-directives.md#2722-firstprivate) dyrektywy.

> [!NOTE]
> Tablice o zmiennej długości, nie są obecnie obsługiwane w programie Visual C++.

```cpp
void f(int m, int C[m][m])
{
    double v1[m];
    ...
    #pragma omp parallel firstprivate(C, v1)
    ...
}
```

## <a name="a28-the-numthreads-clause"></a>A.28 klauzuli num_threads

W poniższym przykładzie pokazano [num_threads](2-directives.md#23-parallel-construct) klauzuli. Równoległego regionu jest wykonywane przy użyciu maksymalnie 10 wątków.

```cpp
#include <omp.h>
main()
{
    omp_set_dynamic(1);
    ...
    #pragma omp parallel num_threads(10)
    {
        ... parallel region ...
    }
}
```

## <a name="a29-work-sharing-constructs-inside-a-critical-construct"></a>A.29 konstrukcje podziału pracy w konstrukcji krytycznej

Poniższy przykład demonstruje użycie konstrukcji podziału pracy w ramach `critical` konstruowania. W tym przykładzie jest zgodne, ponieważ konstruowania podziału pracy i `critical` konstrukcja nie powiązać z tym samym regionie równoległych.

```cpp
void f()
{
  int i = 1;
  #pragma omp parallel sections
  {
    #pragma omp section
    {
      #pragma omp critical (name)
      {
        #pragma omp parallel
        {
          #pragma omp single
          {
            i++;
          }
        }
      }
    }
  }
}
```

## <a name="a30-reprivatization"></a>A.30 Reprivatization

W poniższym przykładzie pokazano reprivatization zmiennych. Mogą zostać oznaczone jako zmienne prywatne `private` ponownie w dyrektywie zagnieżdżonych. Nie należy udostępniać tych zmiennych w otaczającej równoległego regionu.

```cpp
int i, a;
...
#pragma omp parallel private(a)
{
  ...
  #pragma omp parallel for private(a)
  for (i=0; i<10; i++)
     {
       ...
     }
}
```

## <a name="a31-thread-safe-lock-functions"></a>A.31 funkcje blokady wielowątkowości metodą o bezpiecznych wątkach

W poniższym przykładzie C++ pokazuje, jak inicjowanie tablicy blokady w równoległego regionu za pomocą [funkcje omp_init_lock](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions).

```cpp
// A_13_omp_init_lock.cpp
// compile with: /openmp
#include <omp.h>

omp_lock_t *new_locks() {
   int i;
   omp_lock_t *lock = new omp_lock_t[1000];
   #pragma omp parallel for private(i)
   for (i = 0 ; i < 1000 ; i++)
      omp_init_lock(&lock[i]);

   return lock;
}

int main () {}
```
