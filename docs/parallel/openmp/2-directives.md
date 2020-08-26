---
title: 2. Dyrektyw
ms.date: 01/18/2019
ms.assetid: d1a69374-6c03-45fb-8c86-e91cea8adae8
ms.openlocfilehash: 5b2649a65efd3368cf8a4d2649a424b1a539f1ef
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841977"
---
# <a name="2-directives"></a>2. Dyrektywy

Dyrektywy są oparte na `#pragma` dyrektywach zdefiniowanych w standardach C i C++.  Kompilatory obsługujące interfejs API OpenMP i C++ będą zawierać opcję wiersza polecenia, która aktywuje i umożliwia interpretację wszystkich dyrektyw kompilatora OpenMP.

## <a name="21-directive-format"></a>2,1 — format dyrektywy

Składnia dyrektywy OpenMP jest formalnie określona przez gramatykę w [dodatku C](c-openmp-c-and-cpp-grammar.md)i nieformalnie w następujący sposób:

```cpp
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

Każda dyrektywa zaczyna się od  `#pragma omp` , aby zmniejszyć prawdopodobieństwo konfliktu z innymi (rozszerzeniami non-OpenMP lub Vendor do OpenMP) dyrektywy pragma o tych samych nazwach. Pozostała część dyrektywy jest zgodna z konwencjami standardu C i C++ dla dyrektyw kompilatora. W szczególności można użyć białego znaku przed i po `#` , i czasami do oddzielenia wyrazów w dyrektywie należy użyć białych znaków. Wstępne przetwarzanie tokenów po stronie `#pragma omp` podlega wymianie makr.

W dyrektywach jest rozróżniana wielkość liter. Kolejność, w której klauzule pojawiają się w dyrektywach, nie jest istotna. Klauzule dotyczące dyrektyw mogą być powtarzane w razie potrzeby, zgodnie z ograniczeniami wymienionymi w opisie każdej klauzuli. Jeśli w klauzuli występuje *zmienna list* , musi ona określać tylko zmienne. Dla każdej dyrektywy można określić tylko jedną *nazwę dyrektywy* .  Na przykład następująca dyrektywa nie jest dozwolona:

```cpp
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

Dyrektywa OpenMP stosuje się do co najwyżej jednej instrukcji, która się powiedzie, która musi być blokiem strukturalnym.

## <a name="22-conditional-compilation"></a>Kompilacja warunkowa 2,2

`_OPENMP`Nazwa makra jest definiowana przez implementacje zgodne ze standardem OpenMP jako stała dziesiętna *yyyymm*, która będzie rok i miesiąc zatwierdzonej specyfikacji. To makro nie może być podmiotem `#define` lub `#undef` dyrektywą preprocesora.

```cpp
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

Jeśli dostawcy definiują rozszerzenia OpenMP, mogą określić dodatkowe wstępnie zdefiniowane makra.

## <a name="23-parallel-construct"></a>2,3 konstrukcja równoległa

Poniższa dyrektywa definiuje region równoległy, który jest regionem programu, który ma być wykonywany przez wiele wątków równolegle. Ta dyrektywa to podstawowa konstrukcja, która uruchamia wykonywanie równoległe.

```cpp
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

*Klauzula* ma jedną z następujących wartości:

- `if(`*wyrażenie skalarne*`)`
- `private(`*lista zmiennych*`)`
- `firstprivate(`*lista zmiennych*`)`
- `default(shared | none)`
- `shared(`*lista zmiennych*`)`
- `copyin(`*lista zmiennych*`)`
- `reduction(`*operator* `:` *lista zmiennych*  `)`
- `num_threads(`*wyrażenie typu Integer*`)`

Gdy wątek jest przyjdzie do konstrukcji równoległej, zespół wątków jest tworzony, jeśli jest spełniony jeden z następujących przypadków:

- Żadna `if` klauzula nie jest obecna.
- `if`Wyrażenie daje w wyniku wartość różną od zera.

Ten wątek stał się głównym wątkiem zespołu, z numerem wątku równym 0, a wszystkie wątki w zespole, łącznie z wątkiem głównym, wykonują równolegle region. Jeśli wartość `if` wyrażenia jest równa zero, region jest serializowany.

Aby określić liczbę żądanych wątków, zostaną uznane następujące reguły. Pierwsza reguła, której warunek jest spełniony, zostanie zastosowana:

1. Jeśli `num_threads` klauzula jest obecna, wartość wyrażenia Integer jest liczbą żądanych wątków.

1. Jeśli `omp_set_num_threads` Funkcja biblioteki została wywołana, wartość argumentu w ostatnio wykonywanym wywołaniu jest liczbą żądanych wątków.

1. Jeśli zmienna środowiskowa `OMP_NUM_THREADS` jest zdefiniowana, wartość tej zmiennej środowiskowej jest liczbą żądanych wątków.

1. Jeśli żadna z powyższych metod nie zostanie użyta, Liczba żądanych wątków jest definiowana przez implementację.

Jeśli `num_threads` klauzula jest obecna, zastępuje liczbę wątków żądanych przez `omp_set_num_threads` funkcję biblioteki lub `OMP_NUM_THREADS` zmienną środowiskową tylko dla regionu równoległego, do którego jest stosowana. Nie ma to wpływu na więcej regionów równoległych.

Liczba wątków, które wykonują równoległy region, zależy również od tego, czy włączono dynamiczne dopasowanie liczby wątków. Jeśli korekta dynamiczna jest wyłączona, żądana liczba wątków będzie wykonywać równoległy region. Jeśli dopasowanie dynamiczne jest włączone, żądana liczba wątków to maksymalna liczba wątków, które mogą wykonywać równoległy region.

Jeśli zostanie wykryty region równoległy, gdy dynamiczne dopasowanie liczby wątków jest wyłączone, a liczba wątków żądanych dla regionu równoległego jest większa niż liczba, którą system może dostarczyć, zachowanie programu jest zdefiniowane przez implementację. Implementacja może na przykład przerwać wykonywanie programu lub serializować region równoległy.

`omp_set_dynamic`Funkcja Library i `OMP_DYNAMIC` zmienna środowiskowa mogą służyć do włączania i wyłączania dynamicznego dostosowywania liczby wątków.

Liczba procesorów fizycznych w rzeczywistości hostowania wątków w danym momencie jest definiowana przez implementację. Po utworzeniu liczba wątków w zespole pozostaje stała na czas trwania tego regionu równoległego. Można go zmienić jawnie przez użytkownika lub automatycznie przez system czasu wykonywania z jednego regionu równoległego na inny.

Instrukcje zawarte w dynamicznym zakresie regionu równoległego są wykonywane przez każdy wątek, a każdy wątek może wykonać ścieżkę do instrukcji, które różnią się od innych wątków. Dyrektywy napotkane poza leksykalnym zakresem regionu równoległego są określane jako dyrektywy oddzielone.

Istnieje implikowana bariera na końcu równoległego regionu. Tylko wątek główny zespołu kontynuuje wykonywanie na końcu równoległego regionu.

Jeśli wątek w zespole wykonujący równoległy region napotka kolejną konstrukcję równoległą, tworzy nowy zespół i stał się jego wzorcem. Zagnieżdżone regiony równoległe są domyślnie serializowane. W związku z tym domyślnie zagnieżdżony region równoległy jest wykonywany przez zespół składający się z jednego wątku. Zachowanie domyślne można zmienić przy użyciu funkcji biblioteki środowiska uruchomieniowego `omp_set_nested` lub zmiennej środowiskowej `OMP_NESTED` . Jednak liczba wątków w zespole, które wykonują zagnieżdżony region równoległy, jest definiowana przez implementację.

Ograniczenia dotyczące `parallel` dyrektywy są następujące:

- Co najwyżej jedna `if` klauzula może pojawić się w dyrektywie.

- Nie określono, czy występują efekty uboczne wewnątrz wyrażenia IF lub `num_threads` wyrażenia.

- `throw`Wykonanie wewnątrz równoległego regionu musi spowodować wznowienie działania w dynamicznym zakresie tego samego bloku strukturalnego i musi być przechwycone przez ten sam wątek, który wywołał wyjątek.

- `num_threads`W dyrektywie może występować tylko pojedyncza klauzula. `num_threads`Wyrażenie jest oceniane poza kontekstem równoległego regionu i musi być szacowane do dodatniej wartości całkowitej.

- `if` `num_threads` Nie określono kolejności obliczania klauzul i.

### <a name="cross-references"></a>Odsyłacze

- `private`, `firstprivate` ,,, `default` `shared` `copyin` i `reduction` klauzule ([sekcja 2.7.2](#272-data-sharing-attribute-clauses))
- Zmienna środowiskowa [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- Funkcja biblioteki [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)
- Zmienna środowiskowa [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- Funkcja [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)
- Zmienna środowiskowa [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- Funkcja biblioteki [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)

## <a name="24-work-sharing-constructs"></a>2,4 konstrukcje udostępniania pracy

Konstrukcja udostępniania pracy dystrybuuje wykonywanie skojarzonej instrukcji wśród członków zespołu, który go wystąpi. Dyrektywy udostępniania pracy nie uruchamiają nowych wątków i nie ma implikowanej bariery dla wpisu do konstrukcji udostępniania pracy.

Kolejność, w której `barrier` zostały napotkane konstrukcje i dyrektywy udostępniania pracy, musi być taka sama dla każdego wątku w zespole.

OpenMP definiuje następujące konstrukcje podziału pracy, a konstrukcje te są opisane w poniższych sekcjach:

- [dla](#241-for-construct) dyrektywy
- sections [— dyrektywa](#242-sections-construct)
- [Single](#243-single-construct) — dyrektywa

### <a name="241-for-construct"></a>2.4.1 dla konstrukcji

`for`Dyrektywa identyfikuje iteracyjną konstrukcję do udostępniania pracy, która określa, że iteracje skojarzonej pętli będą wykonywane równolegle. Iteracje `for` pętli są dystrybuowane między wątkami, które już istnieją w zespole wykonujących równoległą konstrukcję, z którą jest powiązany. Składnia `for` konstrukcji jest następująca:

```cpp
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

Klauzula ma jedną z następujących wartości:

- `private(`*lista zmiennych*`)`
- `firstprivate(`*lista zmiennych*`)`
- `lastprivate(`*lista zmiennych*`)`
- `reduction(`*operator* `:` *lista zmiennych*`)`
- `ordered`
- `schedule(`*rodzaj* [ `,` *chunk_size*]`)`
- `nowait`

`for`Dyrektywa umieszcza ograniczenia dotyczące struktury odpowiedniej `for` pętli. Odpowiednia `for` Pętla musi mieć kształt kanoniczny:

`for (`*init — wyrażenie* `;` *var logiczne-op b* `;` *incr — wyrażenie*`)`

*init — wyrażenie*<br/>
Jeden z poniższych programów:

- *var*  =  *lb*
- *var*  =  typu Integer *lb*

*Incr — wyrażenie*<br/>
Jeden z poniższych programów:

- `++`*var*
- *var*`++`
- `--`*var*
- *var*`--`
- *var* `+=` *incr*
- *var* `-=` *incr*
- *var* `=` *var* `+` *incr*
- *var* `=` *incr* `+` *var*
- *var* `=` *var* `-` *incr*

*funkcję*<br/>
Zmienna ze znakiem liczby całkowitej. Jeśli ta zmienna będzie w inny sposób udostępniona, zostanie ona niejawnie udostępniona na czas trwania `for` . Nie należy modyfikować tej zmiennej w treści `for` instrukcji. Jeśli zmienna nie jest określona `lastprivate` , jej wartość po pętli jest nieokreślony.

*koniunkcja logiczna*<br/>
Jeden z poniższych programów:

- `<`
- `<=`
- `>`
- `>=`

*lb*, *b*i *incr*<br>
Wyrażenia niezmiennej liczby całkowitej w pętli. Nie ma synchronizacji podczas obliczania tych wyrażeń, dlatego wszelkie ocenione efekty uboczne powodują wygenerowanie nieokreślonych wyników.

Forma kanoniczna umożliwia obliczenia liczby iteracji pętli we wpisie do pętli. To obliczenie jest wykonywane z wartościami w typie *var*po promocjach całkowitych. W szczególności jeśli wartość *b* `-` *lb* `+` *incr* nie może być reprezentowana w tym typie, wynik jest nieokreślony. Dodatkowo, jeśli wartość *logiczna-op* to `<` lub `<=` , funkcja *incr-Expr* musi spowodować, że funkcja *wariancji* ma zwiększyć wartość dla każdej iteracji pętli.   Jeśli *logiczna-op* jest `>` lub `>=` , *incr-Expr* musi spowodować, że *WARIANCJA* będzie mniejsza dla każdej iteracji pętli.

`schedule`Klauzula określa sposób, w jaki iteracja `for` pętli jest dzielona między wątki zespołu. Poprawność programu nie może zależeć od tego, który wątek wykonuje określoną iterację. Wartość *chunk_size*, jeśli określona, musi być wyrażeniem liczby całkowitej w pętli o wartości dodatniej. Nie ma synchronizacji podczas obliczania tego wyrażenia, dlatego wszystkie ocenione efekty uboczne powodują powstanie nieokreślonych wyników. *Typ* harmonogramu może być jedną z następujących wartości:

Tabela 2-1: `schedule` wartości *typu* klauzuli

|Wartość|Opis|
|-|-|
|static|Gdy `schedule(static,` *chunk_size* `)` jest określony, iteracje są dzielone na fragmenty rozmiaru określonego przez *chunk_size*. Fragmenty są statycznie przypisywane do wątków w zespole w sposób okrężny w kolejności numer wątku. Gdy nie określono *chunk_size* , przestrzeń iteracji jest dzielona na fragmenty, które są w przybliżeniu równym rozmiarze, z jednym fragmentem przypisanym do każdego wątku.|
|dynamiczna|Gdy `schedule(dynamic,` *chunk_size* `)` jest określony, iteracje są dzielone na serie fragmentów, z których każda zawiera *chunk_size* iteracji. Każdy fragment jest przypisywany do wątku, który oczekuje na przypisanie. Wątek wykonuje fragment iteracji, a następnie czeka na następne przypisanie, dopóki nie zostaną przypisane żadne fragmenty. Ostatni fragment, który ma zostać przypisany, może mieć mniejszą liczbę iteracji. Gdy nie jest określony żaden *chunk_size* , wartość domyślna to 1.|
|z przewodnikiem|Gdy `schedule(guided,` *chunk_size* `)` jest określony, iteracje są przypisywane do wątków w fragmentach o zmniejszeniu rozmiarów. Gdy wątek kończy przypisane fragmenty iteracji, zostaje dynamicznie przypisany kolejny fragment, dopóki nie pozostanie pozostawiony. W przypadku *chunk_size* 1 rozmiar każdego fragmentu jest w przybliżeniu liczbą nieprzypisanych iteracji podzieloną przez liczbę wątków. Rozmiary te zmniejszają się niemal wykładniczo do 1. Dla *chunk_size* o wartości *k* większej niż 1, rozmiary zmniejszają się niemal wykładniczo do *k*, z tą różnicą, że ostatni fragment może mieć mniej niż *k* iteracji. Gdy nie jest określony żaden *chunk_size* , wartość domyślna to 1.|
|środowisko uruchomieniowe|Gdy `schedule(runtime)` jest określony, decyzja dotycząca planowania jest odroczona do czasu wykonania. *Typ* harmonogramu i rozmiar fragmentów mogą być wybierane w czasie wykonywania przez ustawienie zmiennej środowiskowej `OMP_SCHEDULE` . Jeśli ta zmienna środowiskowa nie jest ustawiona, wynikający z nich harmonogram jest zdefiniowany przez implementację. Gdy  `schedule(runtime)` jest określony, *chunk_size* nie może być określony.|

W przypadku braku jawnie zdefiniowanej `schedule` klauzuli, wartością domyślną `schedule` jest zdefiniowana implementacja.

Program zgodny ze standardem OpenMP nie powinien opierać się na określonym harmonogramie do prawidłowego wykonania. Program nie powinien opierać się na *rodzaju* harmonogramu, który jest dokładnie zgodny z opisem podanym powyżej, ponieważ istnieje możliwość, że istnieją różnice w implementacjach tego samego *rodzaju* harmonogramu w różnych kompilatorach. Opisy mogą służyć do wybierania harmonogramu właściwego dla konkretnej sytuacji.

`ordered`Klauzula musi być obecna, gdy `ordered` dyrektywy są powiązane z konstrukcją `for` .

Istnieje niejawna bariera na końcu konstrukcji, `for` chyba że `nowait` określono klauzulę.

Ograniczenia dotyczące `for` dyrektywy są następujące:

- `for`Pętla musi być blokiem strukturalnym, a ponadto jej wykonanie nie może kończyć się **`break`** instrukcją.

- Wartości wyrażeń kontrolnych pętli `for` skojarzonych z `for` dyrektywą muszą być takie same dla wszystkich wątków w zespole.

- `for`Zmienna iteracji pętli musi mieć typ liczba całkowita ze znakiem.

- `schedule`W dyrektywie może występować tylko pojedyncza klauzula `for` .

- `ordered`W dyrektywie może występować tylko pojedyncza klauzula `for` .

- `nowait`W dyrektywie może występować tylko pojedyncza klauzula `for` .

- Nie określono, jeśli lub jak często występują efekty uboczne w wyrażeniach *chunk_size*, *lb*, *b*lub *incr* .

- Wartość wyrażenia *chunk_size* musi być taka sama dla wszystkich wątków w zespole.

#### <a name="cross-references"></a>Odsyłacze

- `private`, `firstprivate` , `lastprivate` , i `reduction` klauzule ([sekcja 2.7.2](#272-data-sharing-attribute-clauses))
- Zmienna środowiskowa [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule)
- Konstrukcja [uporządkowana](#266-ordered-construct)
- klauzula [Schedule](d-using-the-schedule-clause.md)

### <a name="242-sections-construct"></a>2.4.2 — Konstrukcja sekcji

`sections`Dyrektywa identyfikuje nieiteracyjną konstrukcję udostępniania pracy, która określa zestaw konstrukcji, które mają być podzielone między wątki w zespole. Każda sekcja jest wykonywana raz przez wątek w zespole. Składnia `sections` dyrektywy jest następująca:

```cpp
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

Klauzula ma jedną z następujących wartości:

- `private(`*lista zmiennych*`)`
- `firstprivate(`*lista zmiennych*`)`
- `lastprivate(`*lista zmiennych*`)`
- `reduction(`*operator* `:` *lista zmiennych*  `)`
- `nowait`

Każda sekcja jest poprzedzona `section` dyrektywą, chociaż `section` dyrektywa jest opcjonalna dla pierwszej sekcji. `section`Dyrektywy muszą znajdować się w zakresie leksykalnym `sections` dyrektywy. Istnieje niejawna bariera na końcu `sections` konstrukcji, chyba że `nowait` jest określona.

Ograniczenia dotyczące `sections` dyrektywy są następujące:

- `section`Dyrektywa nie może występować poza leksykalnym zakresem `sections` dyrektywy.

- `nowait`W dyrektywie może występować tylko pojedyncza klauzula `sections` .

#### <a name="cross-references"></a>Odsyłacze

- `private`, `firstprivate` , `lastprivate` , i `reduction` klauzule ([sekcja 2.7.2](#272-data-sharing-attribute-clauses))

### <a name="243-single-construct"></a>2.4.3 pojedyncza konstrukcja

`single`Dyrektywa identyfikuje konstrukcję, która określa, że skojarzony blok strukturalny jest wykonywany przez tylko jeden wątek w zespole (niekoniecznie jest to wątek główny). Składnia `single` dyrektywy jest następująca:

```cpp
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

Klauzula ma jedną z następujących wartości:

- `private(`*lista zmiennych*`)`
- `firstprivate(`*lista zmiennych*`)`
- `copyprivate(`*lista zmiennych*`)`
- `nowait`

Istnieje niejawna bariera po `single` konstrukcji, chyba że `nowait` określono klauzulę.

Ograniczenia dotyczące `single` dyrektywy są następujące:

- `nowait`W dyrektywie może występować tylko pojedyncza klauzula `single` .
- `copyprivate`Klauzula nie może być używana z `nowait` klauzulą.

#### <a name="cross-references"></a>Odsyłacze

- `private`, `firstprivate` , i `copyprivate` klauzule ([sekcja 2.7.2](#272-data-sharing-attribute-clauses))

## <a name="25-combined-parallel-work-sharing-constructs"></a>2,5 połączone równoległe konstrukcje podziału pracy

Połączone równoległe konstrukcje podziału pracy to skróty umożliwiające określenie regionu równoległego, który ma tylko jedną konstrukcję do udostępniania. Semantyka tych dyrektyw jest taka sama jak jawne określenie `parallel` dyrektywy, a następnie jedna konstrukcja udostępniania pracy.

W poniższych sekcjach opisano połączone równoległe konstrukcje podziału pracy:

- [Parallel dla](#251-parallel-for-construct) dyrektywy
- dyrektywy [Parallel](#252-parallel-sections-construct) sections

### <a name="251-parallel-for-construct"></a>2.5.1 Parallel dla konstrukcji

`parallel for`Dyrektywa jest skrótem dla `parallel` regionu, który zawiera tylko jedną `for` dyrektywę. Składnia `parallel for` dyrektywy jest następująca:

```cpp
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

Niniejsza dyrektywa zezwala na wszystkie klauzule `parallel` dyrektywy i `for` dyrektywy, z wyjątkiem `nowait` klauzuli, z identycznymi znaczeniami i ograniczeniami. Semantyka jest taka sama jak jawnie określa `parallel` dyrektywę bezpośrednio po niej po `for` dyrektywie.

#### <a name="cross-references"></a>Odsyłacze

- [Parallel](#23-parallel-construct) — dyrektywa
- [dla](#241-for-construct) dyrektywy
- [Klauzule atrybutu danych](#272-data-sharing-attribute-clauses)

### <a name="252-parallel-sections-construct"></a>Konstrukcja równoległych sekcji 2.5.2

`parallel sections`Dyrektywa zawiera formularz skrótu służący do określania `parallel` regionu, który ma tylko jedną `sections` dyrektywę. Semantyka jest taka sama jak jawnie określa `parallel` dyrektywę bezpośrednio po niej po `sections` dyrektywie. Składnia `parallel sections` dyrektywy jest następująca:

```cpp
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

*Klauzula* może być jedną z klauzul przyjętych przez `parallel` `sections` dyrektywy i, z wyjątkiem `nowait` klauzuli.

#### <a name="cross-references"></a>Odsyłacze

- [Parallel](#23-parallel-construct) — dyrektywa
- sections [— dyrektywa](#242-sections-construct)

## <a name="26-master-and-synchronization-directives"></a>2,6 dyrektywy dotyczące wzorca i synchronizacji

W poniższych sekcjach opisano:

- Konstrukcja [główna](#261-master-construct)
- Konstrukcja [krytyczna](#262-critical-construct)
- [bariera](#263-barrier-directive) — dyrektywa
- Konstrukcja [niepodzielna](#264-atomic-construct)
- [Flush](#265-flush-directive) — dyrektywa
- Konstrukcja [uporządkowana](#266-ordered-construct)

### <a name="261-master-construct"></a>Tworzenie głównej konstrukcji

`master`Dyrektywa identyfikuje konstrukcję, która określa blok strukturalny, który jest wykonywany przez wątek główny zespołu. Składnia `master` dyrektywy jest następująca:

```cpp
#pragma omp master new-linestructured-block
```

Inne wątki w zespole nie wykonują skojarzonego bloku strukturalnego. Brak implikowanej bariery w przypadku wejścia lub wyjścia z konstrukcji głównej.

### <a name="262-critical-construct"></a>Konstrukcja krytyczna 2.6.2

`critical`Dyrektywa identyfikuje konstrukcję ograniczającą wykonywanie skojarzonego bloku strukturalnego do pojedynczego wątku w danym momencie. Składnia `critical` dyrektywy jest następująca:

```cpp
#pragma omp critical [(name)]  new-linestructured-block
```

Opcjonalna *Nazwa* może służyć do identyfikowania regionu krytycznego. Identyfikatory używane do identyfikowania regionu krytycznego mają połączenie zewnętrzne i znajdują się w przestrzeni nazw, która jest oddzielona od przestrzeni nazw używanych przez etykiety, znaczniki, elementy członkowskie i zwykłe identyfikatory.

Wątek czeka na początku regionu krytycznego, dopóki żaden inny wątek nie wykonuje krytycznego regionu (gdziekolwiek w programie) o tej samej nazwie. Wszystkie dyrektywy nienazwanych `critical` są mapowane na tę samą nieokreśloną nazwę.

### <a name="263-barrier-directive"></a>2.6.3 — dyrektywa zapory

`barrier`Dyrektywa synchronizuje wszystkie wątki w zespole. Gdy napotkasz, każdy wątek w zespole czeka, aż wszystkie inne osoby osiągnąli ten punkt. Składnia `barrier` dyrektywy jest następująca:

```cpp
#pragma omp barrier new-line
```

Gdy wszystkie wątki w zespole napotkały barierę, każdy wątek w zespole rozpoczyna wykonywanie instrukcji po równolegle dyrektywie barier. Ponieważ `barrier` dyrektywa nie zawiera instrukcji języka C jako części jej składni, istnieją pewne ograniczenia dotyczące umieszczania w programie. Aby uzyskać więcej informacji na temat formalnej gramatyki, zobacz [dodatek C](c-openmp-c-and-cpp-grammar.md). Poniższy przykład ilustruje te ograniczenia.

```cpp
/* ERROR - The barrier directive cannot be the immediate
*          substatement of an if statement
*/
if (x!=0)
   #pragma omp barrier
...

/* OK - The barrier directive is enclosed in a
*      compound statement.
*/
if (x!=0) {
   #pragma omp barrier
}
```

### <a name="264-atomic-construct"></a>konstrukcja niepodzielna 2.6.4

`atomic`Dyrektywa zapewnia, że określona lokalizacja pamięci jest aktualizowana niepodzielnie, zamiast ujawniać ją w celu wielokrotnego pisania wątków. Składnia `atomic` dyrektywy jest następująca:

```cpp
#pragma omp atomic new-lineexpression-stmt
```

Instrukcja expression musi mieć jedną z następujących form:

- *x binop* `=` *wyrażenie*
- *x*`++`
- `++` *x*
- *x*`--`
- `--` *x*

W poprzednich wyrażeniach:

- *x* jest wyrażeniem lvalue z typem skalarnym.

- *wyrażenie jest* wyrażeniem z typem skalarnym i nie odwołuje się do obiektu wyoznaczonego przez *x*.

- *binop* nie jest przeciążonym operatorem i jest jednym z,,,,,, `+` `*` ,, `-` `/` `&` `^` `|` `<<` lub `>>` .

Chociaż jest definiowana przez implementację, czy implementacja zastępuje wszystkie dyrektywy dyrektywami, `atomic` `critical` które mają taką samą unikatową *nazwę*, `atomic` dyrektywa pozwala na lepszą optymalizację. Często dostępne są instrukcje sprzętu, które mogą wykonywać aktualizację niepodzielną o najniższym obciążeniu.

Tylko obciążenie i magazyn obiektu wyoznaczonego przez *x* są niepodzielne; Ocena *wyrażenia* nie jest niepodzielna. Aby uniknąć sytuacji wyścigu, wszystkie aktualizacje lokalizacji równolegle powinny być chronione za pomocą `atomic` dyrektywy, z wyjątkiem tych, które są nieznane w warunkach wyścigu.

Ograniczenia dotyczące `atomic` dyrektywy są następujące:

- Wszystkie odwołania niepodzielne do lokalizacji magazynu x w ramach programu muszą mieć typ zgodny.

#### <a name="examples"></a>Przykłady

```cpp
extern float a[], *p = a, b;
/* Protect against races among multiple updates. */
#pragma omp atomic
a[index[i]] += b;
/* Protect against races with updates through a. */
#pragma omp atomic
p[i] -= 1.0f;

extern union {int n; float x;} u;
/* ERROR - References through incompatible types. */
#pragma omp atomic
u.n++;
#pragma omp atomic
u.x -= 1.0f;
```

### <a name="265-flush-directive"></a>2.6.5 — Dyrektywa opróżniania

`flush`Dyrektywa, bez względu na to, czy jest jawnie lub implikowana, określa punkt sekwencji "między wątkami", w którym wymagana jest implementacja, aby upewnić się, że wszystkie wątki w zespole mają spójny widok określonych obiektów (określonych poniżej) w pamięci. Oznacza to, że poprzednie oceny wyrażeń, które odwołują się do tych obiektów, są kompletne i kolejne oceny nie zostały jeszcze rozpoczęte. Na przykład kompilatory muszą przywrócić wartości obiektów z rejestrów do pamięci, a sprzęt może wymagać opróżniania buforów zapisu do pamięci i ponownego załadowania wartości obiektów z pamięci.

Składnia `flush` dyrektywy jest następująca:

```cpp
#pragma omp flush [(variable-list)]  new-line
```

Jeśli wszystkie obiekty, które wymagają synchronizacji, można wyznaczyć przez zmienne, wówczas te zmienne można określić na opcjonalnej *liście zmiennych*. Jeśli wskaźnik znajduje się na *liście zmiennych*, wskaźnik jest opróżniany, a nie obiekt, do którego odwołuje się wskaźnik.

`flush`Dyrektywa bez *listy zmiennych* synchronizuje wszystkie obiekty udostępnione z wyjątkiem niedostępnych obiektów z automatycznym okresem przechowywania. (Prawdopodobnie ma więcej nakładów niż `flush` z *listą zmiennych*). `flush` Dyrektywa bez *listy zmiennych* jest implikowana dla następujących dyrektyw:

- `barrier`
- W momencie wejścia i wyjścia z `critical`
- W momencie wejścia i wyjścia z `ordered`
- W momencie wejścia i wyjścia z `parallel`
- Przy wyjściu z `for`
- Przy wyjściu z `sections`
- Przy wyjściu z `single`
- W momencie wejścia i wyjścia z `parallel for`
- W momencie wejścia i wyjścia z `parallel sections`

Dyrektywa nie jest implikowana, jeśli `nowait` jest obecna klauzula. Należy zauważyć, że `flush` dyrektywy nie są implikowane dla żadnego z następujących elementów:

- W pozycji do `for`
- W momencie wejścia lub wyjścia z `master`
- W pozycji do `sections`
- W pozycji do `single`

Odwołanie, które uzyskuje dostęp do wartości obiektu z typem kwalifikowanym nietrwałym, zachowuje się tak, jakby istniała `flush` dyrektywa określająca ten obiekt w poprzednim punkcie sekwencji. Odwołanie, które modyfikuje wartość obiektu z typem kwalifikowanym nietrwałym, zachowuje się tak, jakby istniała `flush` dyrektywa określająca ten obiekt w kolejnym punkcie sekwencji.

Ponieważ `flush` dyrektywa nie zawiera instrukcji języka C jako części jej składni, istnieją pewne ograniczenia dotyczące umieszczania w programie. Aby uzyskać więcej informacji na temat formalnej gramatyki, zobacz [dodatek C](c-openmp-c-and-cpp-grammar.md). Poniższy przykład ilustruje te ograniczenia.

```cpp
/* ERROR - The flush directive cannot be the immediate
*          substatement of an if statement.
*/
if (x!=0)
   #pragma omp flush (x)
...

/* OK - The flush directive is enclosed in a
*      compound statement
*/
if (x!=0) {
   #pragma omp flush (x)
}
```

Ograniczenia dotyczące `flush` dyrektywy są następujące:

- Zmienna określona w `flush` dyrektywie nie może mieć typu referencyjnego.

### <a name="266-ordered-construct"></a>2.6.6 uporządkowana konstrukcja

Blok strukturalny po `ordered` dyrektywie jest wykonywany w kolejności, w której iteracje byłyby wykonywane w pętli sekwencyjnej. Składnia `ordered` dyrektywy jest następująca:

```cpp
#pragma omp ordered new-linestructured-block
```

`ordered`Dyrektywa musi znajdować się w zakresie dynamicznym `for` lub `parallel for` konstrukcji. `for`Dyrektywa lub, `parallel for` do której `ordered` tworzy powiązanie konstrukcja, musi mieć `ordered` określoną klauzulę, zgodnie z opisem w [sekcji 2.4.1](#241-for-construct). W trakcie wykonywania konstrukcji `for` lub `parallel for` z `ordered` klauzulą, `ordered` konstrukcje są wykonywane wyłącznie w kolejności, w jakiej byłyby wykonywane w sekwencyjnym wykonywaniu pętli.

Ograniczenia dotyczące `ordered` dyrektywy są następujące:

- Iteracja pętli z `for` konstrukcyjną nie może wykonać tej samej uporządkowanej dyrektywy więcej niż raz i nie może wykonać więcej niż jednej `ordered` dyrektywy.

## <a name="27-data-environment"></a>środowisko danych 2,7

W tej części przedstawiono dyrektywę i kilka klauzul służących do kontrolowania środowiska danych podczas wykonywania równoległych regionów w następujący sposób:

- Dyrektywa [threadprivate](#271-threadprivate-directive) jest udostępniana w celu udostępnienia w wątku zakresu plików, przestrzeni nazw lub statycznych zmiennych zakresu bloku.

- Klauzule, które mogą być określone w dyrektywach w celu kontrolowania atrybutów udostępniania zmiennych w czasie trwania konstrukcji równoległych lub współdzielących pracy, są opisane w [sekcji 2.7.2](#272-data-sharing-attribute-clauses).

### <a name="271-threadprivate-directive"></a>2.7.1 threadprivate — dyrektywa

`threadprivate`Dyrektywa powoduje, że nazwany zakres plików, przestrzeń nazw lub statyczne zmienne zakresu bloku określone na *liście zmiennych* jako prywatne dla wątku. *zmienna-list* to rozdzielona przecinkami lista zmiennych, które nie mają niekompletnego typu. Składnia `threadprivate` dyrektywy jest następująca:

```cpp
#pragma omp threadprivate(variable-list) new-line
```

Każda kopia `threadprivate` zmiennej jest inicjowana jednokrotnie, w nieokreślonym punkcie programu przed pierwszym odwołaniem do tej kopii, i w zwykły sposób (tj., jako że kopia główna zostanie zainicjowana w ramach wykonywania seryjnego w programie). Należy pamiętać, że jeśli obiekt jest przywoływany w jawnym inicjatorze `threadprivate` zmiennej, a wartość obiektu jest modyfikowana przed pierwszym odwołaniem do kopii zmiennej, zachowanie nie zostanie określone.

Podobnie jak w przypadku dowolnej zmiennej prywatnej, wątek nie może odwoływać się do kopii obiektu innego wątku `threadprivate` . W przypadku regionów szeregowych i regionów głównych programu odwołania będą należeć do kopii obiektu głównego wątku.

Po wykonaniu pierwszego równoległego regionu dane w `threadprivate` obiektach są gwarantowane, tylko wtedy, gdy mechanizm dynamicznego wątków został wyłączony i jeśli liczba wątków pozostanie niezmieniona dla wszystkich regionów równoległych.

Ograniczenia dotyczące `threadprivate` dyrektywy są następujące:

- `threadprivate`Dyrektywa dotycząca zmiennych zakresu plików lub przestrzeni nazw musi znajdować się poza definicją lub deklaracją i musi być w sposób leksykalny poprzedzające wszystkie odwołania do dowolnych zmiennych na liście.

- Każda zmienna na *liście zmiennych* w `threadprivate` dyrektywie w zakresie plików lub przestrzeni nazw musi odwoływać się do deklaracji zmiennej w zakresie plików lub przestrzeni nazw, która jest w sposób leksykalny poprzedzana dyrektywą.

- `threadprivate`Dyrektywa dotycząca statycznych zmiennych zakresu bloku musi znajdować się w zakresie zmiennej, a nie w zakresie zagnieżdżonym. Dyrektywa musi być w sposób leksykalny poprzedzające wszystkie odwołania do dowolnych zmiennych na liście.

- Każda zmienna znajdująca się na *liście zmiennych* w `threadprivate` zakresie bloku musi odwoływać się do deklaracji zmiennej w tym samym zakresie, który jest bardziej specyficzny dla dyrektywy. Deklaracja zmiennej musi używać specyfikatora klasy magazynu static.

- Jeśli zmienna jest określona w `threadprivate` dyrektywie w jednej jednostce translacji, musi być określona w `threadprivate` dyrektywie w każdej jednostce translacji, w której jest zadeklarowana.

- `threadprivate`Zmienna nie może występować w żadnej klauzuli, z wyjątkiem `copyin` `copyprivate` klauzuli,, `schedule` , `num_threads` lub `if` .

- Adres `threadprivate` zmiennej nie jest stałą adresu.

- `threadprivate`Zmienna nie może mieć typu niekompletnego lub typu referencyjnego.

- `threadprivate`Zmienna z typem klasy innym niż pod musi mieć dostępny, jednoznaczny Konstruktor kopiujący, jeśli jest zadeklarowana z jawnym inicjatorem.

Poniższy przykład ilustruje, jak modyfikowanie zmiennej, która pojawia się w inicjatorze może spowodować nieokreślone zachowanie, a także jak uniknąć tego problemu przy użyciu obiektu pomocniczego i konstruktora kopiującego.

```cpp
int x = 1;
T a(x);
const T b_aux(x); /* Capture value of x = 1 */
T b(b_aux);
#pragma omp threadprivate(a, b)

void f(int n) {
   x++;
   #pragma omp parallel for
   /* In each thread:
   * Object a is constructed from x (with value 1 or 2?)
   * Object b is copy-constructed from b_aux
   */
   for (int i=0; i<n; i++) {
      g(a, b); /* Value of a is unspecified. */
   }
}
```

#### <a name="cross-references"></a>Odsyłacze

- [wątki dynamiczne](3-run-time-library-functions.md#317-omp_set_dynamic-function)
- Zmienna środowiskowa [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)

### <a name="272-data-sharing-attribute-clauses"></a>2.7.2 klauzule atrybutu udostępniania danych

Kilka dyrektyw akceptuje klauzule umożliwiające użytkownikowi kontrolowanie atrybutów udostępniania zmiennych na czas trwania regionu. Współużytkowanie klauzul atrybutów ma zastosowanie tylko do zmiennych w zakresie leksykalnym dyrektywy, w której znajduje się klauzula. Nie wszystkie z poniższych klauzul są dozwolone we wszystkich dyrektywach. Lista klauzul, które są prawidłowe w danej dyrektywie, jest opisana w dyrektywie.

Jeśli zmienna jest widoczna w przypadku napotkania konstrukcji równoległej lub w ramach udostępniania pracy, a zmienna nie jest określona w klauzuli atrybutu udostępniania lub `threadprivate` dyrektywie, zmienna jest współdzielona. Zmienne statyczne zadeklarowane w zakresie dynamicznym regionu równoległego są udostępnione. Pamięć przydzielona sterty (na przykład przy użyciu `malloc()` języka C lub c++ lub **`new`** operatora w języku c++) jest udostępniana. (Wskaźnik do tej pamięci, jednak może być prywatny lub udostępniony). Zmienne z automatycznym okresem magazynu zadeklarowane w dynamicznym zakresie regionu równoległego są prywatne.

Większość klauzul akceptuje argument *listy zmiennych* , który jest rozdzielaną przecinkami listą zmiennych, które są widoczne. Jeśli zmienna, do której istnieje odwołanie w klauzuli atrybutu udostępniania danych, ma typ pochodzący z szablonu i nie ma żadnych innych odwołań do tej zmiennej w programie, zachowanie jest niezdefiniowane.

Wszystkie zmienne, które pojawiają się w klauzulach dyrektywy, muszą być widoczne. Klauzule mogą być powtarzane w razie konieczności, ale żadna zmienna nie może być określona w więcej niż jednej klauzuli, z tą różnicą, że zmienna może być określona w `firstprivate` klauzuli a i `lastprivate` .

W poniższych sekcjach opisano klauzule atrybutu udostępniania danych:

- [private](#2721-private)
- [firstprivate](#2722-firstprivate)
- [lastprivate](#2723-lastprivate)
- [udostępniać](#2724-shared)
- [wartooć](#2725-default)
- [reduction](#2726-reduction)
- [copyin](#2727-copyin)
- [copyprivate](#2728-copyprivate)

#### <a name="2721-private"></a>2.7.2.1 — prywatny

`private`Klauzula deklaruje zmienne na liście zmiennych jako prywatne dla każdego wątku w zespole. Składnia `private` klauzuli jest następująca:

```cpp
private(variable-list)
```

Zachowanie zmiennej określonej w `private` klauzuli jest następujące. Nowy obiekt z automatycznym okresem magazynu jest przypisywany dla konstrukcji. Rozmiar i wyrównanie nowego obiektu są określane przez typ zmiennej. Ta alokacja występuje raz dla każdego wątku w zespole, a Konstruktor domyślny jest wywoływany dla obiektu klasy w razie potrzeby; w przeciwnym razie wartość początkowa jest nieokreślona.  Oryginalny obiekt, do którego odwołuje się zmienna, ma nieokreśloną wartość przy wpisie do konstrukcji, nie może być modyfikowany w zakresie dynamicznym konstrukcji i ma nieokreśloną wartość przy wyjściu z konstrukcji.

W zakresie leksykalnym konstrukcji dyrektywy zmienna odwołuje się do nowego obiektu prywatnego przydzielonego przez wątek.

Ograniczenia do `private` klauzuli są następujące:

- Zmienna o typie klasy, która jest określona w `private` klauzuli, musi mieć dostępny, niejednoznaczny Konstruktor domyślny.

- Zmienna określona w `private` klauzuli nie może mieć **`const`** typu kwalifikowanego, chyba że ma typ klasy z `mutable` elementem członkowskim.

- Zmienna określona w `private` klauzuli nie może mieć typu niekompletnego lub typu referencyjnego.

- Zmienne, które pojawiają się w `reduction` klauzuli `parallel` dyrektywy, nie mogą być określone w `private` klauzuli w dyrektywie dotyczącej udostępniania pracy, która jest powiązana z równoległą konstrukcją.

#### <a name="2722-firstprivate"></a>2.7.2.2 — firstprivate

`firstprivate`Klauzula zawiera nadzbiór funkcji dostarczonych przez `private` klauzulę. Składnia `firstprivate` klauzuli jest następująca:

```cpp
firstprivate(variable-list)
```

Zmienne określone w *liście zmiennych* mają `private` semantykę klauzul, zgodnie z opisem w [sekcji 2.7.2.1](#2721-private). Inicjalizacja lub konstrukcja odbywa się tak, jakby była wykonywana raz na wątek przed wykonaniem tej konstrukcji przez wątek. Dla `firstprivate` klauzuli w konstrukcji równoległej wartość początkowa nowego obiektu prywatnego jest wartością oryginalnego obiektu, który istnieje bezpośrednio przed równoległą konstrukcją dla wątku, który go napotka. Dla `firstprivate` klauzuli w konstrukcji udostępniania pracy początkowa wartość nowego obiektu prywatnego dla każdego wątku wykonującego konstrukcję współdzielenia pracy jest wartością oryginalnego obiektu, który istnieje przed punktem w czasie, gdy ten sam wątek napotka konstrukcję udostępniania pracy. Ponadto dla obiektów C++ nowy obiekt prywatny dla każdego wątku jest kopiowany z oryginalnego obiektu.

Ograniczenia do `firstprivate` klauzuli są następujące:

- Zmienna określona w `firstprivate` klauzuli nie może mieć typu niekompletnego lub typu referencyjnego.

- Zmienna o typie klasy, która jest określona jako `firstprivate` musi mieć dostępny, jednoznaczny Konstruktor kopiujący.

- Zmienne, które są prywatne w ramach równoległego regionu lub, które pojawiają się w `reduction` klauzuli `parallel` dyrektywy, nie mogą być określone w `firstprivate` klauzuli w dyrektywie dotyczącej udostępniania pracy, która jest powiązana z równoległą konstrukcją.

#### <a name="2723-lastprivate"></a>2.7.2.3 ostatnia prywatna

`lastprivate`Klauzula zawiera nadzbiór funkcji dostarczonych przez `private` klauzulę. Składnia `lastprivate` klauzuli jest następująca:

```cpp
lastprivate(variable-list)
```

Zmienne określone na *liście zmiennych* mają `private` semantykę klauzul. Gdy `lastprivate` klauzula jest wyświetlana w dyrektywie, która identyfikuje konstrukcję do współdzielenia pracy, wartość każdej `lastprivate` zmiennej z sekwencyjnie Ostatnia iteracja skojarzonej pętli lub dyrektywa "w ostatniej częściowej" jest przypisywana do oryginalnego obiektu zmiennej. Zmienne, które nie mają przypisanej wartości przez ostatnią iterację `for` lub lub `parallel for` przez bardziej leksykalną ostatnią sekcję `sections` `parallel sections` dyrektywy lub, mają nieokreślone wartości po konstrukcji. Nieprzypisane podobiekty również mają nieokreśloną wartość po konstrukcji.

Ograniczenia do `lastprivate` klauzuli są następujące:

- Wszystkie ograniczenia dotyczące `private` zastosowania.

- Zmienna o typie klasy, która jest określona jako `lastprivate` musi mieć dostępny, niejednoznaczny operator przypisania kopiowania.

- Zmienne, które są prywatne w ramach równoległego regionu lub, które pojawiają się w `reduction` klauzuli `parallel` dyrektywy, nie mogą być określone w `lastprivate` klauzuli w dyrektywie dotyczącej udostępniania pracy, która jest powiązana z równoległą konstrukcją.

#### <a name="2724-shared"></a>2.7.2.4 — udostępnione

Ta klauzula udostępnia zmienne, które pojawiają się na *liście zmiennych* wśród wszystkich wątków w zespole. Wszystkie wątki w zespole uzyskują dostęp do tego samego obszaru magazynowania dla `shared` zmiennych.

Składnia `shared` klauzuli jest następująca:

```cpp
shared(variable-list)
```

#### <a name="2725-default"></a>2.7.2.5 — domyślne

`default`Klauzula zezwala użytkownikowi na wpływ atrybutów udostępniania danych zmiennych. Składnia `default` klauzuli jest następująca:

```cpp
default(shared | none)
```

Określanie `default(shared)` jest równoznaczne z jawną listą każdej obecnie widocznej zmiennej w `shared` klauzuli, chyba że jest `threadprivate` lub **`const`** kwalifikowana. W przypadku braku jawnej `default` klauzuli zachowanie domyślne jest takie samo, jak gdyby `default(shared)` zostały określone.

Określenie `default(none)` wymaga, aby co najmniej jeden z następujących elementów musi mieć wartość true dla każdego odwołania do zmiennej w zakresie leksykalnym konstrukcji równoległej:

- Zmienna jest jawnie wymieniona w klauzuli atrybutu udostępniania danych konstrukcji, która zawiera odwołanie.

- Zmienna jest zadeklarowana w konstrukcji równoległej.

- Zmienna ma wartość `threadprivate` .

- Zmienna ma **`const`** Typ kwalifikowany.

- Zmienna to Zmienna sterująca pętli dla `for` pętli, która bezpośrednio następuje `for` `parallel for` po dyrektywie lub, a odwołanie do zmiennej pojawia się wewnątrz pętli.

Określenie zmiennej w `firstprivate` `lastprivate` klauzuli,, lub `reduction` zawartej w niej dyrektywy powoduje niejawne odwołanie do zmiennej w otaczającym kontekście. Takie niejawne odwołania są również uzależnione od wymagań wymienionych powyżej.

`default`W dyrektywie można określić tylko jedną klauzulę `parallel` .

Domyślny atrybut udostępniania danych zmiennej można zastąpić za pomocą `private` `firstprivate` klauzul,, `lastprivate` , `reduction` i `shared` , jak pokazano w następującym przykładzie:

```cpp
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```

#### <a name="2726-reduction"></a>2.7.2.6 — redukcja

Ta klauzula wykonuje redukcję zmiennych skalarnych, które pojawiają się na *liście zmiennych*przy użyciu operatora *op*. Składnia `reduction` klauzuli jest następująca:

`reduction(`*operacja* `:` *lista zmiennych*`)`

Obniżka jest zwykle określona dla instrukcji z jedną z następujących form:

- wyrażenie *x* `=` *x* *op* *expr*
- *x* *binop* `=` *wyrażenie* binop x
- *x* `=` *wyrażenie* *op* *x*  (z wyjątkiem odejmowania)
- *x*`++`
- `++` *x*
- *x*`--`
- `--` *x*

gdzie:

*x*<br/>
Jedna ze zmiennych redukcji określonych na liście.

*Lista zmiennych*<br/>
Rozdzielana przecinkami lista zmiennych redukcji skalarnej.

*wyrażenie*<br/>
Wyrażenie z typem skalarnym, który nie odwołuje się do wartości *x*.

*op*<br/>
Nie jest to przeciążony operator, ale jeden z,,,,,, `+` `*` `-` `&` `^` `|` `&&` , lub `||` .

*binop*<br/>
Nie jest to przeciążony operator, ale jeden z `+` ,, `*` ,, `-` `&` `^` lub `|` .

Poniżej znajduje się przykładowa `reduction` klauzula:

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

Jak pokazano w przykładzie, operator może być ukryty wewnątrz wywołania funkcji. Użytkownik powinien zachować ostrożność, aby operator określony w `reduction` klauzuli pasował do operacji zmniejszania.

Chociaż prawy operand `||` operatora nie ma efektów ubocznych w tym przykładzie, są dozwolone, ale należy go używać z opieką. W tym kontekście efekt uboczny, który nie występuje podczas sekwencyjnego wykonywania pętli, może wystąpić podczas wykonywania równoległego. Różnica taka może wystąpić, ponieważ kolejność wykonywania iteracji jest nieokreślona.

Operator służy do określenia początkowej wartości wszelkich zmiennych prywatnych używanych przez kompilator w celu zmniejszenia i określenia operatora finalizacji. Określenie operatora jawnie zezwala na to, aby instrukcja redukcji była poza leksykalnym zakresem konstrukcji. `reduction`W dyrektywie można określić dowolną liczbę klauzul, ale zmienna może wystąpić w co najwyżej jednej `reduction` klauzuli dla tej dyrektywy.

Prywatna kopia każdej zmiennej w *liście zmiennych* jest tworzona, po jednej dla każdego wątku, tak jakby `private` była używana klauzula. Prywatna kopia jest inicjowana zgodnie z operatorem (patrz Poniższa tabela).

Na końcu regionu, dla którego `reduction` została określona klauzula, oryginalny obiekt jest aktualizowany w celu odzwierciedlenia wyniku połączenia jego pierwotnej wartości z końcową wartością każdej kopii prywatnej przy użyciu określonego operatora. Operatory redukcji są wszystkie skojarzeniami (z wyjątkiem odejmowania), a kompilator może swobodnie ponownie kojarzyć obliczenia wartości końcowej. (Częściowe wyniki zmniejszenia odejmowania są dodawane do postaci końcowej wartości).

Wartość oryginalnego obiektu zostanie nieokreślona, gdy pierwszy wątek osiągnie klauzulę zawierającą i pozostaje tak do momentu zakończenia obliczania obniżki.  Zwykle obliczenia zostaną wykonane na końcu konstrukcji; Jednakże jeśli `reduction` klauzula jest używana w konstrukcji, do której `nowait` jest również stosowana, wartość oryginalnego obiektu pozostaje nieokreślona do momentu wykonania synchronizacji bariery, aby upewnić się, że wszystkie wątki ukończyły `reduction` klauzulę.

W poniższej tabeli wymieniono operatory, które są prawidłowe i ich wartości inicjujące kanoniczne. Rzeczywista wartość inicjowania będzie spójna z typem danych zmiennej redukcyjnej.

|Operator|Inicjalizacja|
|--------------|--------------------|
|`+`|0|
|`*`|1|
|`-`|0|
|`&`|~ 0|
|`|`|0|
|`^`|0|
|`&&`|1|
|`||`|0|

Ograniczenia do `reduction` klauzuli są następujące:

- Typ zmiennych w `reduction` klauzuli musi być prawidłowy dla operatora redukcji, z wyjątkiem tego, że typy wskaźnika i typy odwołań nigdy nie są dozwolone.

- Zmienna określona w `reduction` klauzuli nie może być **`const`** kwalifikowana.

- Zmienne, które są prywatne w ramach równoległego regionu lub, które pojawiają się w `reduction` klauzuli `parallel` dyrektywy, nie mogą być określone w `reduction` klauzuli w dyrektywie dotyczącej udostępniania pracy, która jest powiązana z równoległą konstrukcją.

   ```cpp
   #pragma omp parallel private(y)
   { /* ERROR - private variable y cannot be specified
                in a reduction clause */
      #pragma omp for reduction(+: y)
      for (i=0; i<n; i++)
         y += b[i];
   }

   /* ERROR - variable x cannot be specified in both
              a shared and a reduction clause */
   #pragma omp parallel for shared(x) reduction(+: x)
   ```

#### <a name="2727-copyin"></a>2.7.2.7 kopiowanie

`copyin`Klauzula zawiera mechanizm do przypisywania tej samej wartości do `threadprivate` zmiennych dla każdego wątku w zespole wykonującego region równoległy. Dla każdej zmiennej określonej w `copyin` klauzuli wartość zmiennej w wątku głównym zespołu jest kopiowana, tak jak przez przypisanie, do kopii prywatnych wątku na początku regionu równoległego. Składnia `copyin` klauzuli jest następująca:

```cpp

copyin(
variable-list
)
```

Ograniczenia do `copyin` klauzuli są następujące:

- Zmienna określona w `copyin` klauzuli musi mieć dostępny, niejednoznaczny operator przypisania kopiowania.

- Zmienna określona w `copyin` klauzuli musi być `threadprivate` zmienną.

#### <a name="2728-copyprivate"></a>2.7.2.8 — prywatna kopia

`copyprivate`Klauzula zawiera mechanizm do użycia zmiennej prywatnej do emisji wartości z jednego członka zespołu do innych członków. Alternatywnym rozwiązaniem jest użycie zmiennej udostępnionej dla wartości, gdy udostępnienie takiej zmiennej udostępnionej byłaby trudne (na przykład w rekursji wymagającej innej zmiennej na każdym poziomie). `copyprivate`Klauzula może występować tylko w `single` dyrektywie.

Składnia `copyprivate` klauzuli jest następująca:

```cpp

copyprivate(
variable-list
)
```

Wpływ `copyprivate` klauzuli na zmienne na liście zmiennych występuje po wykonaniu bloku strukturalnego skojarzonego z konstrukcją `single` , a przed jakimkolwiek wątkiem w zespole nie opuścił bariery na końcu konstrukcji. Następnie, we wszystkich innych wątkach w zespole, dla każdej zmiennej na *liście zmiennych*, ta zmienna zostaje zdefiniowana (tak jak przez przypisanie) z wartością odpowiedniej zmiennej w wątku, który wykonał blok strukturalny konstrukcji.

Ograniczenia do `copyprivate` klauzuli są następujące:

- Zmienna określona w `copyprivate` klauzuli nie może występować w `private` `firstprivate` klauzuli OR dla tej samej `single` dyrektywy.

- Jeśli `single` dyrektywa z `copyprivate` klauzulą jest wyszukiwana w dynamicznym zakresie regionu równoległego, wszystkie zmienne określone w `copyprivate` klauzuli muszą być prywatne w otaczającym kontekście.

- Zmienna określona w `copyprivate` klauzuli musi mieć dostępny niejednoznaczny operator przypisania kopii.

## <a name="28-directive-binding"></a>2,8 powiązanie dyrektywy

Dynamiczne powiązanie dyrektyw musi przestrzegać następujących zasad:

- `for`Dyrektywy, `sections` , `single` , `master` i są `barrier` powiązane z dynamicznym otaczającym `parallel` , jeśli taki istnieje, niezależnie od wartości każdej `if` klauzuli, która może być obecna w tej dyrektywie. Jeśli żaden region równoległy nie jest aktualnie wykonywany, dyrektywy są wykonywane przez zespół składający się z tylko z wątku głównego.

- `ordered`Dyrektywa wiąże się z dynamiczną ramką `for` .

- `atomic`Dyrektywa wymusza wyłączny dostęp w odniesieniu do `atomic` dyrektyw we wszystkich wątkach, a nie tylko dla bieżącego zespołu.

- `critical`Dyrektywa wymusza wyłączny dostęp w odniesieniu do `critical` dyrektyw we wszystkich wątkach, a nie tylko dla bieżącego zespołu.

- Dyrektywa może nigdy nie powiązać żadnej dyrektywy poza najbliższym dynamicznie `parallel` .

## <a name="29-directive-nesting"></a>2,9 zagnieżdżenia dyrektywy

Dynamiczne zagnieżdżanie dyrektyw musi przestrzegać następujących zasad:

- `parallel`Dyrektywa dynamicznie wewnątrz innego `parallel` elementu logicznie tworzy nowy zespół, który składa się tylko z bieżącego wątku, chyba że jest włączona zagnieżdżona równoległość.

- `for`, `sections` i `single` dyrektywy, które wiążą się z tym samym, `parallel` nie mogą być zagnieżdżone wewnątrz siebie.

- `critical` dyrektywy o tej samej nazwie nie mogą być zagnieżdżone wewnątrz siebie. Należy zauważyć, że to ograniczenie nie jest wystarczające, aby zapobiec zakleszczeniu.

- `for`, `sections` , i `single` dyrektywy nie są dozwolone w dynamicznym zakresie `critical` , `ordered` i `master` regiony, jeśli dyrektywy są powiązane z tymi samymi `parallel` regionami.

- `barrier` dyrektywy nie są dozwolone w zakresie dynamicznym,,,, `for` `ordered` `sections` `single` `master` i `critical` regionach, jeśli dyrektywy są powiązane z tymi samymi, `parallel` co regiony.

- `master` dyrektywy nie są dozwolone w zakresie dynamicznym `for` , `sections` i dyrektywy, jeśli dyrektywy są powiązane z takimi `single` `master` samymi `parallel` jak dyrektywy dotyczące udostępniania pracy.

- `ordered` dyrektywy nie są dozwolone w dynamicznym zakresie `critical` regionów, jeśli dyrektywy są powiązane z tymi samymi, `parallel` co regiony.

- Każda dyrektywa, która jest dozwolona, gdy jest wykonywana dynamicznie w regionie równoległym, jest również dozwolona, gdy jest wykonywana poza równoległym regionem. W przypadku wykonywania dynamicznego na zewnątrz regionu równoległego określonego przez użytkownika, dyrektywa jest wykonywana przez zespół składający się z tylko wątku głównego.
