---
title: 2. Dyrektyw
ms.date: 01/18/2019
ms.assetid: d1a69374-6c03-45fb-8c86-e91cea8adae8
ms.openlocfilehash: 125d2d83b277e62d007e3a208e426ea717d52790
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363716"
---
# <a name="2-directives"></a>2. Dyrektyw

Dyrektywy opierają się na `#pragma` dyrektywy zdefiniowana w standardach C i C++.  Kompilatory, które obsługują OpenMP C i C++ interfejsu API będzie zawierać opcji wiersza polecenia, który aktywuje i umożliwia interpretacji wszystkich OpenMP, dyrektywy kompilatora.

## <a name="21-directive-format"></a>2.1 format dyrektywy

Składnia OpenMP — dyrektywa formalnie jest określona przez gramatyki w [dodatek C](c-openmp-c-and-cpp-grammar.md)i nieformalnie w następujący sposób:

```cpp
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

Każda dyrektywa zaczyna się od `#pragma omp`, aby zmniejszyć ryzyko będących w konflikcie z innymi dyrektywy pragma (-OpenMP lub dostawcy rozszerzeń OpenMP) przy użyciu takich samych nazwach. Pozostała część dyrektywy jest zgodna z konwencjami standardów C i C++ dla dyrektywy kompilatora. W szczególności biały znak może służyć przed i po nim `#`, i czasami biały mogą być używane do oddzielania słów w dyrektywie. Przetworzone wstępnie tokeny po `#pragma omp` podlegają wymiana makra.

Dyrektywy jest rozróżniana wielkość liter. Kolejność wyświetlania klauzule w dyrektywach nie jest istotne. Klauzule na dyrektywy może się powtarzać, zgodnie z potrzebami, zgodnie z ograniczeniami wymienionych w opisie każdej klauzuli. Jeśli *liście zmiennych* pojawia się w klauzuli on muszą określać tylko zmienne. Tylko jeden *nazwa dyrektywy* może być określona dla dyrektywy.  Na przykład następująca dyrektywa nie jest dozwolone:

```cpp
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

OpenMP — dyrektywa ma zastosowanie do co najwyżej jeden poniższymi instrukcję, która musi być strukturalnego bloku.

## <a name="22-conditional-compilation"></a>2.2 kompilacja warunkowa

`_OPENMP` Nazwa makra jest zdefiniowany przez implementacje CLS OpenMP jako stałej dziesiętnej *yyyymm*, który będzie stanowić rok i miesiąc specyfikacji zatwierdzone. To makro nie może być przedmiotem `#define` lub `#undef` dyrektywy preprocesora.

```cpp
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

Jeśli dostawców zdefiniować rozszerzenia OpenMP, ich mogą określać dodatkowe wstępnie zdefiniowanych makr.

## <a name="23-parallel-construct"></a>2.3 konstrukcja równoległa

Następująca dyrektywa definiuje równoległego regionu, czyli obszarem program, który ma być wykonane przez wiele wątków jednocześnie. Ta dyrektywa jest podstawowe konstrukcji, która rozpoczyna wykonywanie równoległe.

```cpp
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

*Klauzuli* jest jednym z następujących czynności:

- `if(` *scalar-expression* `)`
- `private(` *Lista zmiennych* `)`
- `firstprivate(` *Lista zmiennych* `)`
- `default(shared | none)`
- `shared(` *Lista zmiennych* `)`
- `copyin(` *Lista zmiennych* `)`
- `reduction(` *operator* `:` *liście zmiennych* `)`
- `num_threads(` *wyrażenie całkowite* `)`

Kiedy wątek uzyskuje się konstrukcja równoległa, zespół wątków jest tworzone, jeśli jest spełniony jeden z następujących przypadkach:

- Nie `if` klauzula jest obecny.
- `if` Wyrażenie ma wartość różną od zera.

Ten wątek staje się główny wątek zespołu, wprowadzając szereg wątek 0, i regionu równolegle uruchomić wszystkie wątki w zespole, łącznie z wątku głównego. Jeśli wartość `if` wyrażenie jest równe zeru, region jest serializowana.

Aby określić liczbę wątków, które są wymagane, następujące reguły zostanie uwzględniony w kolejności. Pierwsza reguła, której warunek jest spełniony, zostaną zastosowane:

1. Jeśli `num_threads` klauzula jest obecna, a następnie wartość wyrażenia typu całkowitego jest liczba wątków zażądano.

1. Jeśli `omp_set_num_threads` została wywołana funkcja biblioteki, a następnie wartość argumentu w wywołaniu ostatnio wykonywanych jest liczba wątków żądanie.

1. Jeśli zmienna środowiskowa `OMP_NUM_THREADS` jest zdefiniowana, a następnie wartość tej zmiennej środowiskowej liczbę wątków, żądanie.

1. Jeśli żaden z powyższych metod jest używany, liczbę wątków, wymagane jest zdefiniowane w implementacji.

Jeśli `num_threads` klauzula jest obecna, a następnie zastępuje ona liczbę wątków, żądane przez `omp_set_num_threads` funkcja biblioteki lub `OMP_NUM_THREADS` zmiennej środowiskowej tylko w przypadku równoległego regionu jest stosowany do. Później regionów równoległych nie ma wpływu na jej.

Liczba wątków, które są wykonywane równoległego regionu również zależy od tego, czy włączono dynamiczne Dostosowywanie liczby wątków. Wyłączenie dynamiczne Dostosowywanie żądana liczba wątków będzie wykonywał równoległego regionu. Po włączeniu dynamicznego dostosowania żądana liczba wątków jest maksymalna liczba wątków, które może zostać wykonany równoległego regionu.

Jeśli równoległego regionu podczas dynamicznego dostosowania liczby wątków jest wyłączona, a liczba wątków żądany dla równoległego regionu jest większa niż liczba, która może dostarczyć systemu środowiska wykonawczego, jest zachowanie programu zdefiniowane w implementacji. Implementacja może na przykład przerywa wykonywanie programu, lub może serializować, równoległego regionu.

`omp_set_dynamic` Funkcja biblioteki i `OMP_DYNAMIC` zmiennej środowiskowej można włączać i wyłączać dynamiczne Dostosowywanie liczby wątków.

Liczba procesorów fizycznych, w rzeczywistości hostingu wątki w danym momencie jest zdefiniowane w implementacji. Po utworzeniu liczbę wątków w zespole pozostają stałe na czas trwania tego równoległego regionu. Można zmienić, jawnie przez użytkownika lub automatycznie przez system środowiska wykonawczego z jednego regionu równoległego do innego.

Instrukcje zawarte w obrębie zakresu dynamicznego równoległego regionu są wykonywane przez poszczególne wątki, a każdy wątek może wykonać ścieżkę instrukcji, która różni się od innych wątków. Dyrektywy napotkano poza zakres leksykalne równoległego regionu są określane jako oddzielony dyrektywy.

Brak dorozumianych barierę na końcu równoległego regionu. Główny wątek zespół kontynuuje wykonywanie na końcu równoległego regionu.

Jeśli wątek w zespole wykonywania równoległego regionu napotka inna konstrukcja równoległa, powoduje to utworzenie nowego zespołu i staje się główną tego nowego zespołu. Zagnieżdżone regionów równoległych są serializowane domyślnie. Co w efekcie domyślnie zagnieżdżonych równoległego regionu jest wykonywana przez zespół składa się z jednego wątku. Domyślne zachowanie może zostać zmieniona przez przy użyciu albo funkcja biblioteki uruchomieniowej `omp_set_nested` lub zmiennej środowiskowej `OMP_NESTED`. Jednak liczbę wątków w zespołach, które są wykonywane zagnieżdżonych równoległego regionu jest zdefiniowane w implementacji.

Ograniczenia `parallel` dyrektywy jest następująca:

- Co najwyżej jeden `if` klauzula może występować w dyrektywie.

- Jest nieokreślony, czy po dowolnej stronie efekty w przypadku wyrażenia lub `num_threads` występować wyrażenie.

- A `throw` wykonywana wewnątrz równoległego regionu musi spowodować wykonanie można wznowić w ramach dynamicznej stopnia tego samego bloku ze strukturą, a musi być przechwycony przez tego samego wątku, który wygenerował wyjątek.

- Tylko jeden `num_threads` klauzula może występować w dyrektywie. `num_threads` Wyrażenie jest szacowana poza kontekstem równoległego regionu, a musi być dodatnią liczbą całkowitą.

- Kolejność obliczania `if` i `num_threads` klauzule jest nieokreślona.

### <a name="cross-references"></a>Odsyłacze

- `private`, `firstprivate`, `default`, `shared`, `copyin`, i `reduction` klauzule ([sekcji 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) zmiennej środowiskowej
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) funkcja biblioteki
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) zmiennej środowiskowej
- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) — funkcja
- [OMP_NESTED](4-environment-variables.md#44-omp_nested) zmiennej środowiskowej
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function) funkcja biblioteki

## <a name="24-work-sharing-constructs"></a>2.4 konstrukcje podziału pracy

Konstrukcji podziału pracy dystrybuuje wykonywania skojarzoną instrukcję wśród członków zespołu, napotykane go. Dyrektyw podziału pracy nie uruchamiaj nowe wątki, i nie bez problemu dorozumianych przy uruchamianiu konstrukcji podziału pracy.

Tworzy sekwencję podziału pracy i `barrier` dyrektywy napotkano musi być taka sama dla każdego wątku w zespole.

OpenMP definiuje następujące konstrukcje podziału pracy i te konstrukcje są opisane w kolejnych sekcjach:

- [Aby uzyskać](#241-for-construct) — dyrektywa
- [sekcje](#242-sections-construct) — dyrektywa
- [pojedynczy](#243-single-construct) — dyrektywa

### <a name="241-for-construct"></a>2.4.1 konstrukcja for

`for` Dyrektywy identyfikuje iteracyjne konstrukcji podziału pracy określający, że iteracje pętli skojarzone będą wykonywane równolegle. Iteracje `for` pętli są rozmieszczone na wątki, które już istnieją w zespołach, wykonywanie równoległe konstrukcji, która wiąże. Składnia `for` konstrukcja jest w następujący sposób:

```cpp
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

Klauzula jest jedną z następujących czynności:

- `private(` *Lista zmiennych* `)`
- `firstprivate(` *Lista zmiennych* `)`
- `lastprivate(` *Lista zmiennych* `)`
- `reduction(` *operator* `:` *liście zmiennych* `)`
- `ordered`
- `schedule(` *rodzaj* [`,` *chunk_size*] `)`
- `nowait`

`for` Dyrektywy stosuje ograniczenia dla struktury odpowiadającego `for` pętli. W szczególności odpowiednich `for` pętli musi mieć kształtu kanoniczny:

`for (` *wyrażenie inicjowania* `;` *b logiczne op var* `;` *incr — wyrażenie* `)`

*init-expr*<br/>
Jeden z poniższych:

- *var* = *lb*
- *Typ liczby całkowitej var* = *modułu równoważenia obciążenia*

*incr-expr*<br/>
Jeden z poniższych:

- `++` *var*
- *var* `++`
- `--` *var*
- *var* `--`
- *var* `+=` *incr*
- *var* `-=` *incr*
- *var* `=` *var* `+` *incr*
- *var* `=` *incr* `+` *var*
- *var* `=` *var* `-` *incr*

*var*<br/>
Zmienna liczba całkowita ze znakiem. Jeśli ta zmienna, w przeciwnym razie mogłyby być udostępniane, niejawnie staje się prywatnych na czas trwania `for`. Nie należy modyfikować tej zmiennej w treści `for` instrukcji. Jeśli nie określono zmiennej `lastprivate`, jego wartość po pętli jest nieokreślony.

*logical-op*<br/>
Jeden z poniższych:

- `<`
- `<=`
- `>`
- `>=`

*lb*, *b*, i *incr*<br>
Pętla wyrażeń niezmiennej liczby całkowitej. Jest brak synchronizacji podczas obliczania wartości tych wyrażeń, dlatego wszelkie ocenianą efekty uboczne generują nieokreślone wyniki.

Forma kanoniczna umożliwia liczby iteracji pętli, które ma zostać obliczony przy uruchamianiu pętli. To obliczenie jest wykonywane przy użyciu wartości w typie *var*, po promocji typu całkowitego. W szczególności jeśli wartość *b* `-` *lb* `+` *incr* nie może być przedstawiony w tym typu, wynik jest nieokreślony. Dodatkowo Jeśli *logiczne op* jest `<` lub `<=`, następnie *incr expr* mogą powodować *var* zwiększyć w każdej iteracji pętli.   Jeśli *logiczne op* jest `>` lub `>=`, następnie *incr expr* mogą powodować *var* można pobrać mniejsze w każdej iteracji pętli.

`schedule` Klauzula określa sposób iteracje `for` pętli są podzielone między wątki zespołu. Poprawność programu nie może zależeć od których wątek wykonuje konkretnej iteracji. Wartość *chunk_size*, jeśli określony, musi być wyrażeniem niezmiennej całkowitą pętli z wartością dodatnią. Jest brak synchronizacji podczas obliczania wyrażenia, dlatego wszelkie ocenianą efekty uboczne generują nieokreślone wyniki. Harmonogram *rodzaj* może być jedną z następujących wartości:

Tabela 2-1: `schedule` klauzuli *rodzaj* wartości

|||
|-|-|
|static|Gdy `schedule(static,` *chunk_size* `)` określono iteracji są podzielone na fragmenty o rozmiarze określonym przez *chunk_size*. Fragmenty są statycznie przypisane do wątków w zespole w okrężne zgodnie z kolejnością liczba wątków. Gdy nie *chunk_size* określono miejsca iteracji jest podzielony na fragmenty, które są w przybliżeniu taki sam rozmiar, z jednym fragmencie przypisane do każdego wątku.|
|dynamic|Gdy `schedule(dynamic,` *chunk_size* `)` określono iteracje są podzielone na szereg fragmenty, zawierających *chunk_size* iteracji. Każdy fragment jest przypisany do wątku, który oczekuje na przydzielenie. Wątek wykonuje fragmentów iteracji, a następnie czeka na przypisania dalej, dopóki nie pozostaną bez fragmentów do przypisania. Ostatni fragment do przypisania, może mieć mniejszej liczby iteracji. Gdy nie *chunk_size* jest określony, jego wartość domyślna to 1.|
|krok po kroku|Gdy `schedule(guided,` *chunk_size* `)` określono iteracje są przypisane do wątków we fragmentach, z malejącymi rozmiarów. Po zakończeniu jego przypisane fragmentów iteracji wątku go jest dynamicznie przypisywany innym fragmencie, dopóki nie pozostanie. Aby uzyskać *chunk_size* 1, rozmiar każdego fragmentu jest około liczby iteracji nieprzypisane dzielona przez liczbę wątków. Te rozmiary prawie wykładniczo zmniejszyć do 1. Dla *chunk_size* wartością *k* większy niż 1, rozmiary zmniejszyć prawie wykładniczo do *k*, z tą różnicą, że ostatni fragment może być mniejsza niż *k* iteracji. Gdy nie *chunk_size* jest określony, jego wartość domyślna to 1.|
|środowisko uruchomieniowe|Gdy `schedule(runtime)` jest określony, decyzji dotyczących planowania jest odroczone do czasu środowiska uruchomieniowego. Harmonogram *rodzaj* i rozmiar fragmentów można wybrać w czasie wykonywania przez ustawienie zmiennej środowiskowej `OMP_SCHEDULE`. Jeśli ta zmienna środowiskowa nie jest ustawiona, wynikowy harmonogram jest zdefiniowane w implementacji. Gdy `schedule(runtime)` jest określony, *chunk_size* nie może być określony.|

W przypadku braku jawnie zdefiniowanych `schedule` klauzuli, domyślnym `schedule` jest zdefiniowane w implementacji.

Program zgodny z OpenMP nie należy polegać na konkretny harmonogram wykonywania poprawne. Program nie należy traktować zgodnie z harmonogramem *rodzaj* odpowiadających dokładnie opis podanej powyżej, ponieważ istnieje możliwość zmiany w implementacji tego samego harmonogramu *rodzaj* między różne kompilatory. Opisy może służyć do wybierz harmonogram, który jest odpowiedni dla danej sytuacji.

`ordered` Klauzuli musi być obecny, kiedy `ordered` dyrektywy powiązać `for` konstruowania.

Na końcu ma niejawne barierę `for` konstruowania, chyba że `nowait` jest określona klauzula.

Ograniczenia `for` dyrektywy jest następująca:

- `for` Pętli musi być strukturalnego bloku, a ponadto, jego wykonanie nie musi się kończyć znakiem `break` instrukcji.

- Wartości pętli kontrolować wyrażeń `for` pętli skojarzony `for` dyrektywa musi być taka sama dla wszystkich wątków w zespole.

- `for` Zmienna iteracji pętli musi mieć typ liczby całkowitej ze znakiem.

- Tylko jeden `schedule` klauzula może występować na `for` dyrektywy.

- Tylko jeden `ordered` klauzula może występować na `for` dyrektywy.

- Tylko jeden `nowait` klauzula może występować na `for` dyrektywy.

- Jest nieokreślony, jeśli lub jak często wpływ dowolnej stronie w obrębie *chunk_size*, *lb*, *b*, lub *incr* wyrażenia wystąpić.

- Wartość *chunk_size* wyrażenie musi być taka sama dla wszystkich wątków w zespole.

#### <a name="cross-references"></a>Odsyłacze

- `private`, `firstprivate`, `lastprivate`, i `reduction` klauzule ([sekcji 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule) zmiennej środowiskowej
- [uporządkowane](#266-ordered-construct) konstruowania
- [Harmonogram](d-using-the-schedule-clause.md) — klauzula

### <a name="242-sections-construct"></a>2.4.2 sekcje konstrukcja

`sections` Dyrektywy identyfikuje noniterative konstrukcji podziału pracy, który określa zestaw konstrukcji, które są podzielone między wątkami w zespole. Każda sekcja jest wykonywane raz przez wątek w zespole. Składnia `sections` dyrektywy jest następująca:

```cpp
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

Klauzula jest jedną z następujących czynności:

- `private(` *Lista zmiennych* `)`
- `firstprivate(` *Lista zmiennych* `)`
- `lastprivate(` *Lista zmiennych* `)`
- `reduction(` *operator* `:` *liście zmiennych* `)`
- `nowait`

Każda sekcja jest poprzedzony `section` dyrektywy, mimo że `section` dyrektywa jest opcjonalna w pierwszej sekcji. `section` Dyrektywy musi znajdować się w obrębie zakresu leksykalne `sections` dyrektywy. Na końcu ma niejawne barierę `sections` konstruowania, chyba że `nowait` jest określony.

Ograniczenia `sections` dyrektywy jest następująca:

- A `section` dyrektywy nie musi znajdować się poza zakres leksykalne `sections` dyrektywy.

- Tylko jeden `nowait` klauzula może występować na `sections` dyrektywy.

#### <a name="cross-references"></a>Odsyłacze

- `private`, `firstprivate`, `lastprivate`, i `reduction` klauzule ([sekcji 2.7.2](#272-data-sharing-attribute-clauses))

### <a name="243-single-construct"></a>2.4.3 konstrukcja single

`single` Dyrektywy identyfikuje konstrukcja, która określa, czy skojarzony ze strukturalnego bloku jest wykonywana przez tylko jeden wątek w zespole (niekoniecznie głównego wątku). Składnia `single` dyrektywy jest następująca:

```cpp
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

Klauzula jest jedną z następujących czynności:

- `private(` *Lista zmiennych* `)`
- `firstprivate(` *Lista zmiennych* `)`
- `copyprivate(` *Lista zmiennych* `)`
- `nowait`

Niejawne problemu po `single` konstruowania, chyba że `nowait` jest określona klauzula.

Ograniczenia `single` dyrektywy jest następująca:

- Tylko jeden `nowait` klauzula może występować na `single` dyrektywy.
- `copyprivate` Nie można używać klauzuli z `nowait` klauzuli.

#### <a name="cross-references"></a>Odsyłacze

- `private`, `firstprivate`, i `copyprivate` klauzule ([sekcji 2.7.2](#272-data-sharing-attribute-clauses))

## <a name="25-combined-parallel-work-sharing-constructs"></a>2.5 połączone równoległe konstrukcje podziału pracy

Połączone równoległe konstrukcje podziału pracy to skróty do określania równoległego regionu, który ma tylko jedną konstrukcji podziału pracy. Semantyka te dyrektywy są takie same, jak jawne określenie `parallel` dyrektywy następuje pojedynczy konstrukcji podziału pracy.

W poniższych sekcjach opisano połączone równoległe konstrukcje podziału pracy:

- [równoległe w](#251-parallel-for-construct) — dyrektywa
- [sekcji równoległych](#252-parallel-sections-construct) — dyrektywa

### <a name="251-parallel-for-construct"></a>2.5.1 konstrukcja równoległa

`parallel for` Dyrektywa jest skrót `parallel` region, który zawiera tylko jeden `for` dyrektywy. Składnia `parallel for` dyrektywy jest następująca:

```cpp
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

Ta dyrektywa zezwala na wszystkie klauzule `parallel` dyrektywy i `for` dyrektywy, z wyjątkiem `nowait` klauzuli przy użyciu identycznych znaczenie i ograniczeń. Semantyka jest taka sama jak jawne określenie `parallel` dyrektywy bezpośrednio następuje `for` dyrektywy.

#### <a name="cross-references"></a>Odsyłacze

- [równoległe](#23-parallel-construct) — dyrektywa
- [Aby uzyskać](#241-for-construct) — dyrektywa
- [Klauzule atrybutu danych](#272-data-sharing-attribute-clauses)

### <a name="252-parallel-sections-construct"></a>2.5.2 konstrukcja sekcji równoległych

`parallel sections` Postaci skrótów zapewnia dyrektywa określająca `parallel` regionem, który ma tylko jeden `sections` dyrektywy. Semantyka jest taka sama jak jawne określenie `parallel` dyrektywy bezpośrednio następuje `sections` dyrektywy. Składnia `parallel sections` dyrektywy jest następująca:

```cpp
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

*Klauzuli* może być jedną z klauzul zaakceptowane przez `parallel` i `sections` dyrektyw, z wyjątkiem `nowait` klauzuli.

#### <a name="cross-references"></a>Odsyłacze

- [równoległe](#23-parallel-construct) — dyrektywa
- [sekcje](#242-sections-construct) — dyrektywa

## <a name="26-master-and-synchronization-directives"></a>2.6 dyrektywy głównego i synchronizacji

W poniższych sekcjach opisano:

- [główny](#261-master-construct) konstruowania
- [krytyczne](#262-critical-construct) konstruowania
- [bariera](#263-barrier-directive) — dyrektywa
- [Atomic](#264-atomic-construct) konstruowania
- [Flush](#265-flush-directive) — dyrektywa
- [uporządkowane](#266-ordered-construct) konstruowania

### <a name="261-master-construct"></a>2.6.1, konstrukcja master

`master` Dyrektywy identyfikuje konstrukcja, która określa ze strukturą blok, który jest wykonywany przez główny wątek zespołu. Składnia `master` dyrektywy jest następująca:

```cpp
#pragma omp master new-linestructured-block
```

Inne wątki w zespole nie wykonać skojarzone ze strukturalnego bloku. Bez problemu dorozumianych na wpis do lub wyjście z konstrukcja master nie istnieje.

### <a name="262-critical-construct"></a>2.6.2, konstrukcja critical

`critical` Dyrektywy identyfikuje konstrukcja, która ogranicza wykonywania skojarzone ze strukturalnego bloku do pojedynczego wątku w danym momencie. Składnia `critical` dyrektywy jest następująca:

```cpp
#pragma omp critical [(name)]  new-linestructured-block
```

Opcjonalny *nazwa* może służyć do identyfikowania krytyczne regionu. Identyfikatory używane do identyfikowania krytyczne region mają powiązania zewnętrzne i znajdują się w przestrzeni nazw, który jest oddzielony od przestrzeni nazw używanych przez etykiety, tagi, członków i zwykłymi identyfikatorami.

Wątek oczekuje się na początku krytyczne region, aż żadnego innymi wątku jest wykonywany krytyczne region (w dowolnym miejscu program) o takiej samej nazwie. Wszystkie nienazwane `critical` dyrektywy mapowania tej samej nazwie nieokreślony.

### <a name="263-barrier-directive"></a>2.6.3 bariera, dyrektywa

`barrier` Dyrektywy synchronizuje wszystkie wątki w zespole. W przypadku każdego wątku w zespole czeka, aż wszystkie pozostałe on osiągnąć tego punktu. Składnia `barrier` dyrektywy jest następująca:

```cpp
#pragma omp barrier new-line
```

Po wszystkie wątki w zespole wystąpił barierę, rozpoczyna się każdy wątek w zespole, wykonywania instrukcji po dyrektywie barierę równolegle. Ponieważ `barrier` dyrektywy nie zawiera instrukcję języka C w ramach jego składni, istnieją pewne ograniczenia dotyczące jego położenie w obrębie programu. Aby uzyskać więcej informacji dotyczących gramatyki formalny, zobacz [dodatek C](c-openmp-c-and-cpp-grammar.md). W poniższym przykładzie przedstawiono te ograniczenia.

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

### <a name="264-atomic-construct"></a>2.6.4, konstrukcja atomic

`atomic` Dyrektywy oznacza, że lokalizacja pamięci niepodzielne, aktualizowane zamiast uwidaczniania go do możliwości wielu jednoczesnych, zapisywanie wątków. Składnia `atomic` dyrektywy jest następująca:

```cpp
#pragma omp atomic new-lineexpression-stmt
```

Instrukcja wyrażeń musi mieć jedną z następujących form:

- *x binop* `=` *expr*
- *x* `++`
- `++` *x*
- *x* `--`
- `--` *x*

W poprzednim wyrażenia:

- *x* jest wyrażeniem l-wartości o typie skalarnym.

- *wyrażenie* to wyrażenie skalarne typu, a nie odwołuje się obiekcie wyznaczonym przez *x*.

- *binop* nie jest przeciążony operator i jest jednym z `+`, `*`, `-`, `/`, `&`, `^`, `|`, `<<`, lub `>>`.

Mimo że jest zdefiniowane w implementacji tego, czy implementacja zastępuje wszystkie `atomic` dyrektyw z `critical` dyrektyw, które mają taki sam unikatowy *nazwa*, `atomic` zezwala lepsza Optymalizacja — dyrektywa . Często sprzętu instrukcje są dostępne, można wykonać aktualizację atomic o najmniejszej obciążenie.

Tylko obciążenia i magazynu obiekcie wyznaczonym przez *x* są niepodzielne; oceny *expr* nie są niepodzielne. Aby uniknąć Sytuacje wyścigu, wszystkie aktualizacje lokalizacji, w sposób równoległy powinny być chronione przy użyciu `atomic` dyrektywy, z wyjątkiem tych, które są znane jako bez wyścigu.

Ograniczenia `atomic` dyrektywy jest następująca:

- Wszystkie odwołania niepodzielną do lokalizacji magazynu x w całym programie muszą mieć zgodne z typem.

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

### <a name="265-flush-directive"></a>2.6.5 dyrektywa opróżniania

`flush` Dyrektywy, czy jawnych ani dorozumianych, określa punktu sekwencji "międzywątkowe" jaką wdrożenia jest wymagany do upewnij się, że wszystkie wątki w zespole spójny widok niektórych obiektów (wymienionymi poniżej) w pamięci. Oznacza to, że spełniono poprzednie wersje ewaluacyjne wyrażeń, które odwołują się do tych obiektów, a kolejne oceny nie zostało jeszcze rozpoczęte. Na przykład kompilatory należy przywrócić wartości obiektów z rejestrów w pamięci i sprzętu może być konieczne opróżnienia buforów zapisu w pamięci i ponownie załaduj wartości obiektów z pamięci.

Składnia `flush` dyrektywy jest następująca:

```cpp
#pragma omp flush [(variable-list)]  new-line
```

Jeśli obiekty, które wymagają synchronizacji mogą wszystkie zostać wyznaczony przez zmienne, a następnie tych zmiennych można określić opcjonalny *liście zmiennych*. Jeśli wskaźnik jest obecny w *liście zmiennych*, wskaźnika, sama jest opróżniany, nie obiekt wskaźnika odwołuje się do.

A `flush` dyrektywy bez *liście zmiennych* synchronizuje wszystkich udostępnionych obiektów, z wyjątkiem niedostępnych obiektów z automatycznym okresem magazynu. (Jest to prawdopodobnie mają większe obciążenie niż `flush` z *liście zmiennych*.) A `flush` dyrektywy bez *liście zmiennych* jest implikowane dla następujących dyrektywach:

- `barrier`
- Wpis i wyjścia z `critical`
- Wpis i wyjścia z `ordered`
- Wpis i wyjścia z `parallel`
- Przy wyjściu z `for`
- Przy wyjściu z `sections`
- Przy wyjściu z `single`
- Wpis i wyjścia z `parallel for`
- Wpis i wyjścia z `parallel sections`

Dyrektywa nie jest implikowane, jeśli `nowait` klauzula jest obecny. Należy zauważyć, że `flush` dyrektywy nie jest implikowana dla żadnego z następujących czynności:

- Na wpis `for`
- Wpis do lub wyjście z `master`
- Na wpis `sections`
- Na wpis `single`

Odwołania, który uzyskuje dostęp do wartości obiektu z typem kwalifikowana volatile zachowuje się jak w przypadku `flush` dyrektywy określenie tego obiektu w poprzednim punkcie sekwencji. Odwołania, która modyfikuje wartość obiektu o typie kwalifikowana volatile zachowuje się jak w przypadku `flush` dyrektywy określenie tego obiektu w momencie kolejnych sekwencji.

Ponieważ `flush` dyrektywy nie zawiera instrukcję języka C w ramach jego składni, istnieją pewne ograniczenia dotyczące jego położenie w obrębie programu. Aby uzyskać więcej informacji dotyczących gramatyki formalny, zobacz [dodatek C](c-openmp-c-and-cpp-grammar.md). W poniższym przykładzie przedstawiono te ograniczenia.

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

Ograniczenia `flush` dyrektywy jest następująca:

- Określone w zmiennej `flush` dyrektywy nie może mieć typu referencyjnego.

### <a name="266-ordered-construct"></a>2.6.6 uporządkowany konstrukcja

Następujący blok strukturalny `ordered` dyrektywa jest wykonywany w kolejności, w którym będzie można wykonywać iteracje, w pętli sekwencyjnej. Składnia `ordered` dyrektywy jest następująca:

```cpp
#pragma omp ordered new-linestructured-block
```

`ordered` Dyrektywy musi należeć do zakresu dynamicznego `for` lub `parallel for` konstruowania. `for` Lub `parallel for` dyrektywy, do którego `ordered` powiązań konstrukcja musi mieć `ordered` klauzulę zgodnie z opisem w [sekcji 2.4.1](#241-for-construct). W trakcie wykonania `for` lub `parallel for` skonstruować przy użyciu `ordered` klauzuli `ordered` konstrukcji są wykonywane wyłącznie w kolejności, w którym będzie można wykonywać w wykonanie sekwencyjne pętli.

Ograniczenia `ordered` dyrektywy jest następująca:

- Iteracji pętli za pomocą `for` konstrukcja nie musi wykonać uporządkowane dyrektywa więcej niż jeden raz i nie musisz wykonać więcej niż jedną `ordered` dyrektywy.

## <a name="27-data-environment"></a>2.7 środowisko danych

W tej sekcji przedstawiono dyrektywy i kilka klauzul do kontrolowania środowiska danych podczas wykonywania równoległego regionów, w następujący sposób:

- A [threadprivate](#271-threadprivate-directive) dyrektywy znajduje się zakres pliku, zakresie przestrzeni nazw lub zakresie bloku statyczne zmienne lokalne do wątku.

- Klauzule, które mogą być określone dla dyrektywy do kontrolowania udostępniania atrybutów zmienne w czasie trwania konstrukcje równoległego lub podziału pracy zostały opisane w [sekcji 2.7.2](#272-data-sharing-attribute-clauses).

### <a name="271-threadprivate-directive"></a>2.7.1 dyrektywa threadprivate

`threadprivate` Dyrektywy sprawia, że nazwany zakres pliku, zakresie przestrzeni nazw lub zmiennych statycznych zasięgiem bloku określone w *liście zmiennych* prywatnego wątku. *Lista zmiennej* znajduje się lista rozdzielonych przecinkami zmiennych, które nie mają niekompletnego typu. Składnia `threadprivate` dyrektywy jest następująca:

```cpp
#pragma omp threadprivate(variable-list) new-line
```

Każda kopia `threadprivate` zmienna jest inicjowana raz, w momencie nieokreślony w programie przed pierwszym odwołaniu do tej kopii, jak i w zwykły sposób (czyli jako kopia główna może być inicjowane w wykonanie szeregowe programu). Należy pamiętać, że jeśli obiekt jest wywoływane w inicjatorze jawne z `threadprivate` zmienną i wartość obiektu zostanie zmodyfikowany przed pierwszym odwołaniu kopię zmiennej, a następnie zachowanie jest nieokreślone.

Jak za pomocą dowolnej zmiennej prywatnej wątek nie może odwoływać się inny wątek kopię `threadprivate` obiektu. W regionach szeregowych i regiony głównego programu odwołania zostaną kopii obiektu głównego wątku.

Po wykonaniu pierwszej równoległego regionu, dane w `threadprivate` obiektów jest gwarantowane do utrwalenia, tylko jeśli dynamicznej wątki mechanizm został wyłączony, a jeśli liczba wątków pozostaje niezmieniona dla wszystkich regionów równoległych.

Ograniczenia do `threadprivate` dyrektywy jest następująca:

- A `threadprivate` dyrektywy dla zmiennych w zakresie pliku lub zakresie przestrzeni nazw musi znajdować się poza deklaracji lub definicji i leksykalnie musi poprzedzać wszystkie odwołania do tych zmiennych na liście.

- Każdej zmiennej w *liście zmiennych* z `threadprivate` dyrektywy w zakresie pliku lub przestrzeni nazw musi odwoływać się do deklaracji zmiennej w zakresie pliku lub przestrzeni nazw, leksykalnie poprzedzającym dyrektywy.

- A `threadprivate` dyrektywy zmiennych statycznych zakresie bloku musi znajdować się w zakresie zmiennej i nie znajduje się w zakresie zagnieżdżonych. Dyrektywa leksykalnie musi poprzedzać wszystkie odwołania do tych zmiennych na liście.

- Każdej zmiennej w *liście zmiennych* z `threadprivate` dyrektywy w zakresie bloku musi odwoływać się do deklaracji zmiennej w tym samym zakresie, leksykalnie poprzedzającym dyrektywy. Deklaracja zmiennej, należy użyć specyfikator statycznej klasy magazynowania.

- Jeśli zmienna jest określona w `threadprivate` dyrektywy w jednostce translacji jeden, musi być określona w `threadprivate` dyrektywy w każdej jednostce translacji, w którym jest zdeklarowana.

- A `threadprivate` zmiennej nie musi znajdować się w żadnej klauzuli, z wyjątkiem `copyin`, `copyprivate`, `schedule`, `num_threads`, lub `if` klauzuli.

- Adres `threadprivate` zmienna nie jest stałą adresu.

- A `threadprivate` zmiennej nie może mieć typu niekompletnego lub typu odwołania.

- A `threadprivate` zmienna typu non-POD klasy musi mieć konstruktora kopiującego dostępny, jednoznaczną, jeśli jest zadeklarowana za pomocą jawnego inicjatora.

Poniższy przykład ilustruje sposób modyfikowania zmienną, która pojawia się w inicjatorze może spowodować nieokreślone zachowanie oraz sposób uniknąć tego problemu za pomocą konstruktora kopiującego i pomocnicze w ramach obiektu.

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

- [dynamiczne wątków](3-run-time-library-functions.md#317-omp_set_dynamic-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) zmiennej środowiskowej

### <a name="272-data-sharing-attribute-clauses"></a>2.7.2 klauzule atrybutu udostępniania danych

Kilka dyrektyw zaakceptować klauzul, które umożliwiają użytkownikowi na kontrolowanie udostępniania atrybutów zmienne w czasie trwania regionu. Klauzule atrybutu udostępniania dotyczą tylko zmienne w zakresie leksykalnym dyrektywy, na której znajduje się klauzuli. Nie wszystkie z następujących klauzul są dozwolone dla wszystkich dyrektyw. Lista klauzul, które są ważne w szczególności dyrektywy są opisane za pomocą dyrektywy.

Jeśli zmienna jest widoczna, gdy równoległego lub konstrukcji podziału pracy zostanie osiągnięty, a zmienna nie jest określona w klauzuli udostępniania atrybutu lub `threadprivate` dyrektywy, następnie zmienna jest udostępniony. Statyczne zmienne zadeklarowane wewnątrz zakresu dynamicznego równoległego regionu są udostępnione. Sterty przydzielonej pamięci (na przykład za pomocą `malloc()` w języku C lub C++ lub `new` operatora w języku C++) jest udostępniony. (Wskaźnik pamięci, jednak może być prywatne lub udostępniony.) Zmienne z automatycznym okresem magazynu zadeklarowaną w ramach zakresu dynamicznego równoległego regionu są prywatne.

Zaakceptuj większość klauzul *liście zmiennych* argumentu, który znajduje się lista rozdzielonych przecinkami zmiennych, które są widoczne. Jeśli zmienna do której odwołuje się klauzulą atrybutu udostępniania danych ma typ pochodzący od szablonu i istnieją nie inne odwołania do tej zmiennej w programie, zachowanie jest niezdefiniowane.

Wszystkie zmienne, które są wyświetlane w klauzulach dyrektywy muszą być widoczne. Klauzule może być powtarzany zgodnie z potrzebami, ale zmiennej nie może być określone w więcej niż jedną klauzulę, z tą różnicą, że zmienna może być określony w obu `firstprivate` i `lastprivate` klauzuli.

W poniższych sekcjach opisano klauzule atrybutu udostępniania danych:

- [private](#2721-private)
- [firstprivate](#2722-firstprivate)
- [lastprivate](#2723-lastprivate)
- [Udostępnione](#2724-shared)
- [default](#2725-default)
- [reduction](#2726-reduction)
- [copyin](#2727-copyin)
- [copyprivate](#2728-copyprivate)

#### <a name="2721-private"></a>2.7.2.1 — prywatny

`private` Klauzuli deklarujemy zmienne na liście zmiennych można używać prywatnego każdy wątek w zespole. Składnia `private` klauzula jest w następujący sposób:

```cpp
private(variable-list)
```

Zachowanie określone w zmiennej `private` klauzula jest w następujący sposób. Nowy obiekt z automatycznym okresem magazynu jest przydzielany dla konstrukcji. Rozmiar i wyrównanie nowego obiektu są określane przez typ zmiennej. Ten przydział wykonywana jeden raz dla każdego wątku w zespole, a domyślny konstruktor jest wywoływana dla obiektu klasy, w razie potrzeby; w przeciwnym razie wartość początkowa jest nieokreślony.  Oryginalny obiekt odwołuje się zmienna ma nieokreśloną wartość po wejściu do konstrukcja nie mogą zostać zmodyfikowane w ramach zakresu dynamiczna konstrukcja i ma nieokreśloną wartość przy zamykaniu z konstrukcja.

W zakresie leksykalnym dyrektywy konstrukcji zmienna odwołuje się do nowego obiektu prywatnej przydzielonej przez wątek.

Ograniczenia do `private` klauzuli są następujące:

- Zmiennej z typu klasy, która została określona w `private` klauzuli musi mieć dostęp, jednoznaczną domyślnego konstruktora.

- Określone w zmiennej `private` nie mogą zawierać klauzuli `const`-wykwalifikowany typ, chyba że jego klasa to typ `mutable` elementu członkowskiego.

- Określone w zmiennej `private` klauzuli nie może mieć typu niekompletnego lub typu odwołania.

- Zmienne, które pojawiają się w `reduction` klauzuli `parallel` dyrektywy nie można określić w `private` klauzuli w dyrektywie podziału pracy, która jest powiązywana z konstrukcja równoległa.

#### <a name="2722-firstprivate"></a>2.7.2.2 — firstprivate

`firstprivate` Klauzuli stanowi nadzbiór funkcje udostępniane przez `private` klauzuli. Składnia `firstprivate` klauzula jest w następujący sposób:

```cpp
firstprivate(variable-list)
```

Zmienne określone w *liście zmiennych* mają `private` klauzuli semantykę, zgodnie z opisem w [sekcji 2.7.2.1](#2721-private). Inicjowanie lub konstrukcji odbywa się tak, jakby były wykonywane raz na wątek przed wykonanie wątku konstrukcja. Aby uzyskać `firstprivate` klauzuli na konstrukcję równoległych, początkowa wartość nowego obiektu prywatnego jest wartością oryginalny obiekt, który występuje bezpośrednio przed równoległe konstrukcji dla wątku, który je napotka. Aby uzyskać `firstprivate` klauzuli w konstrukcji podziału pracy, początkowa wartość nowy obiekt prywatny dla każdego wątku, który jest wykonywany konstrukcji podziału pracy jest wartością oryginalny obiekt, który istnieje przed punktu w czasie, że takie same wątek napotka konstrukcji podziału pracy. Ponadto dla obiektów C++, nowy obiekt prywatny dla każdego wątku jest kopia skonstruowany na podstawie oryginalnego obiektu.

Ograniczenia do `firstprivate` klauzuli są następujące:

- Określone w zmiennej `firstprivate` klauzuli nie może mieć typu niekompletnego lub typu odwołania.

- Zmiennej z typu klasy, która jest określona jako `firstprivate` musi mieć konstruktora kopiującego dostępny, jednoznaczną.

- Zmienne, które są prywatne w ramach równoległego regionu lub które są widoczne w `reduction` klauzuli `parallel` dyrektywy nie można określić w `firstprivate` klauzuli w dyrektywie podziału pracy, która jest powiązywana z konstrukcja równoległa.

#### <a name="2723-lastprivate"></a>2.7.2.3 ostatnia prywatna

`lastprivate` Klauzuli stanowi nadzbiór funkcje udostępniane przez `private` klauzuli. Składnia `lastprivate` klauzula jest w następujący sposób:

```cpp
lastprivate(variable-list)
```

Zmienne określone w *liście zmiennych* mają `private` semantyki klauzuli. Gdy `lastprivate` klauzuli pojawia się na dyrektywę, który identyfikuje konstrukcji podziału pracy, wartość każdego `lastprivate` zmiennej z sekwencyjnie ostatniej iteracji pętli skojarzone lub leksykalnie ostatnią dyrektywą sekcji, jest przypisany do oryginalny obiekt w zmiennej. Zmienne, które nie są przypisane wartości w ostatniej iteracji `for` lub `parallel for`, lub przez leksykalnie ostatnią sekcję `sections` lub `parallel sections` dyrektywy, mają wartości nieokreślone po konstrukcji. Nieprzypisane podobiektów również mieć nieokreślona wartość po konstrukcji.

Ograniczenia do `lastprivate` klauzuli są następujące:

- Wszystkie ograniczenia dla `private` zastosowania.

- Zmiennej z typu klasy, która jest określona jako `lastprivate` musi być dostępny, jednoznaczną kopia operatora przypisania.

- Zmienne, które są prywatne w ramach równoległego regionu lub które są widoczne w `reduction` klauzuli `parallel` dyrektywy nie można określić w `lastprivate` klauzuli w dyrektywie podziału pracy, która jest powiązywana z konstrukcja równoległa.

#### <a name="2724-shared"></a>2.7.2.4 — udostępnione

Ta klauzula udostępnia zmiennych, które pojawiają się w *liście zmiennych* przez wszystkie wątki w zespole. Wszystkie wątki w zespole dostęp do tego samego obszaru pamięci masowej `shared` zmiennych.

Składnia `shared` klauzula jest w następujący sposób:

```cpp
shared(variable-list)
```

#### <a name="2725-default"></a>2.7.2.5 — domyślne

`default` Klauzuli umożliwia użytkownikowi mają wpływ na atrybuty udostępnianie danych zmiennych. Składnia `default` klauzula jest w następujący sposób:

```cpp
default(shared | none)
```

Określanie `default(shared)` jest odpowiednikiem jawnego określania każdej zmiennej aktualnie widoczne w `shared` klauzuli, chyba że jest to `threadprivate` lub `const`-kwalifikowaną. W przypadku braku jawnego `default` klauzuli, zachowanie domyślne jest taka sama jak if `default(shared)` zostały określone.

Określanie `default(none)` wymaga, że co najmniej jedną z następujących muszą być spełnione dla każdego odwołania do zmiennej w zakresie leksykalnym konstrukcja równoległa:

- Zmienna jawnie znajduje się w konstrukcji, która zawiera odwołanie do klauzuli atrybutu udostępniania danych.

- Ta zmienna została zgłoszona w ramach równoległego konstrukcji.

- Zmienna jest `threadprivate`.

- Zmienna posiada `const`-kwalifikowaną typu.

- Zmienna jest zmienna sterująca pętli for `for` pętli, który poprzedza `for` lub `parallel for` dyrektywy i odwołanie do zmiennej pojawia się wewnątrz pętli.

Określenie zmiennej na `firstprivate`, `lastprivate`, lub `reduction` klauzuli ujęty dyrektywy powoduje niejawne odwołanie do zmiennej w otaczającym kontekście. Takie odwołań niejawnych są również w zależności od wymagań wymienionych powyżej.

Tylko jeden `default` klauzuli mogą być określone dla `parallel` dyrektywy.

Zmienna domyślnego atrybutu udostępniania danych, można zastąpić przy użyciu `private`, `firstprivate`, `lastprivate`, `reduction`, i `shared` zdań, jak pokazano na poniższym przykładzie:

```cpp
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```

#### <a name="2726-reduction"></a>2.7.2.6 — redukcja

Ta klauzula wykonuje zmniejszenie na zmienne skalarne, które pojawiają się w *liście zmiennych*, za pomocą operatora *op*. Składnia `reduction` klauzula jest w następujący sposób:

`reduction(` *Op* `:` *liście zmiennych* `)`

Ograniczenie jest zazwyczaj określana dla instrukcji przy użyciu jednego z następujących form:

- *x* `=` *x* *op* *expr*
- *x* *binop* `=` *expr*
- *x* `=` *expr* *op* *x* (z wyjątkiem odejmowania)
- *x* `++`
- `++` *x*
- *x* `--`
- `--` *x*

gdzie:

*x*<br/>
Jedna ze zmiennych redukcji określonych na liście.

*variable-list*<br/>
Rozdzielana przecinkami lista zmiennych redukcja skalaru.

*expr*<br/>
Wyrażenie skalarne typu, który nie odwołuje się do *x*.

*OP*<br/>
Nie przeciążonego operatora, ale jeden z `+`, `*`, `-`, `&`, `^`, `|`, `&&`, lub `||`.

*binop*<br/>
Nie przeciążonego operatora, ale jeden z `+`, `*`, `-`, `&`, `^`, lub `|`.

Oto przykład `reduction` klauzuli:

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

Jak pokazano w przykładzie, operator może być ukryta wewnątrz wywołania funkcji. Użytkownik należy zachować ostrożność, że operator określona w `reduction` klauzuli odpowiada operację redukcji.

Mimo że prawy operand `||` operator ma żadnych efektów ubocznych, w tym przykładzie, jest dozwolone, ale powinna być stosowana z rozwagą. W tym kontekście efekt uboczny, który ma gwarancję występują podczas wykonywania sekwencyjnego pętli mogą wystąpić podczas wykonywania równoległego. Różnica ta może być fakt, że kolejność wykonywania iteracji jest nieokreślony.

Operator jest używany do określenia początkowej wartości żadnych zmiennych prywatnego używany przez kompilator do zmniejszenia oraz określeniem operator finalizacji jest zakończona. Jawne określenie operator umożliwia instrukcji redukcji przekraczających zakres leksykalne konstrukcja. Dowolną liczbę `reduction` klauzule mogą być określone dla dyrektywy, ale zmiennej może występować w co najwyżej jeden `reduction` klauzula dla tej dyrektywy.

Prywatną kopię każdej zmiennej w *liście zmiennych* zostanie utworzony, jeden dla każdego wątku, tak jakby `private` została użyta klauzula. Zainicjowano prywatnej kopii zgodnie z operatora (patrz poniższa tabela).

Na koniec region, dla którego `reduction` określono klauzulę, oryginalny obiekt jest aktualizowany w celu odzwierciedlenia wynikiem połączenia oryginalnej wartości z końcowa wartość każdego prywatne kopie za pomocą operatora określono. Operatory redukcji są wszystkie asocjacyjnych (z wyjątkiem odejmowania), a kompilator swobodnie ponownie skojarzyć obliczenie wartości końcowej. (Wyniki częściowe redukcji odejmowania są dodawane do utworzenia końcowej).

Wartość obiektu oryginalnego staje się nieokreślony, gdy pierwszy wątek osiągnie zawierających klauzulę i pozostaje, więc przed zakończeniem obliczania redukcji.  Zwykle obliczeń zostanie wykonana na końcu konstrukcji; Jednak jeśli `reduction` na konstrukcję, do której jest używana klauzula `nowait` jest również stosowane wartości oryginalnego obiektu pozostanie nieokreślone do czasu, aby upewnić się, że wszystkie wątki zostały ukończone zostaławykonanasynchronizacjabarierę`reduction`klauzuli.

W poniższej tabeli wymieniono operatory, które są prawidłowe i ich wartości canonical inicjowania. Wartość rzeczywista inicjalizacji będzie zgodny z typem danych zmiennej redukcji.

|Operator|Inicjalizacja|
|--------------|--------------------|
|`+`|0|
|`*`|1|
|`-`|0|
|`&`|~0|
|`|`|0|
|`^`|0|
|`&&`|1|
|`||`|0|

Ograniczenia do `reduction` klauzuli są następujące:

- Typ zmiennych w `reduction` klauzula musi mieć prawidłowy dla operatorem redukcji, z tą różnicą, że nigdy nie są dozwolone typy wskaźników i odwołań.

- Zmienna, która została określona w `reduction` klauzuli nie może być `const`-kwalifikowaną.

- Zmienne, które są prywatne w ramach równoległego regionu lub które są widoczne w `reduction` klauzuli `parallel` dyrektywy nie można określić w `reduction` klauzuli w dyrektywie podziału pracy, która jest powiązywana z konstrukcja równoległa.

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

`copyin` Klauzuli zapewnia mechanizm, aby przypisać tę samą wartość, aby `threadprivate` zmienne dla każdego wątku w zespole wykonywania równoległego regionu. Dla każdej zmiennej, określone w `copyin` klauzuli, wartość zmiennej w głównym wątku zespołu, jest kopiowany, tak, jakby przez przypisanie do kopii prywatnego wątku na początku równoległego regionu. Składnia `copyin` klauzula jest w następujący sposób:

```cpp

copyin(
variable-list
)
```

Ograniczenia do `copyin` klauzuli są następujące:

- Zmienna, która została określona w `copyin` klauzula musi mieć operatora przypisania kopiowania dostępny, jednoznaczną.

- Zmienna, która została określona w `copyin` musi mieć klauzulę `threadprivate` zmiennej.

#### <a name="2728-copyprivate"></a>2.7.2.8 — prywatna kopia

`copyprivate` Klauzuli udostępnia mechanizm do zmiennej prywatnej umożliwia emitowanie wartości z jednego członka zespołu do innych członków. Jest to alternatywa dla użycia w udostępnionej zmiennej wartości, gdy dostarczanie w udostępnionej zmiennej może sprawiać trudności (na przykład w rekursji, wymagających inną zmienną na każdym poziomie). `copyprivate` Klauzuli może się pojawić tylko `single` dyrektywy.

Składnia `copyprivate` klauzula jest w następujący sposób:

```cpp

copyprivate(
variable-list
)
```

Efekt `copyprivate` klauzuli zmiennych na swojej liście zmiennych występuje po wykonaniu strukturalnego bloku skojarzone z `single` konstruowania, i przed wszystkich wątków w zespole pozostało barierę na końcu konstrukcja. Następnie w innych wątków w zespole, dla każdej zmiennej w *liście zmiennych*, zmienna staje się definicją (tak, jakby przypisanie) z wartością odpowiadającego zmiennej w wątku, który jest wykonywany konstrukcja użytkownika ze strukturą blok.

Ograniczenia `copyprivate` klauzuli są następujące:

- Zmienna, która została określona w `copyprivate` klauzuli nie musi znajdować się w `private` lub `firstprivate` klauzulę dla tego samego `single` dyrektywy.

- Jeśli `single` dyrektywy z `copyprivate` klauzuli napotkaniu dynamicznego zakresu równoległego regionu, wszystkie zmienne określone w `copyprivate` klauzuli musi być prywatna w otaczającym kontekście.

- Zmienna, która została określona w `copyprivate` klauzula musi mieć operatora przypisania kopiowania jednoznaczną dostępne.

## <a name="28-directive-binding"></a>2.8 powiązania dyrektywy

Dynamiczne powiązanie dyrektyw określających muszą być zgodne z następującymi zasadami:

- `for`, `sections`, `single`, `master`, I `barrier` dyrektywy powiązać dynamicznie otaczający `parallel`, jeśli taki istnieje, niezależnie od wartości dowolnych `if` klauzula, która może być obecny na tym dyrektywa. Jeśli obecnie jest wykonywana nie równoległego regionu, dyrektywy są wykonywane przez zespół składa się z głównego wątku.

- `ordered` Dyrektywy wiąże dynamicznie otaczający `for`.

- `atomic` Dyrektywy wymusza wyłącznego dostępu w odniesieniu do `atomic` dyrektywy w wszystkie wątki, nie tylko zespół.

- `critical` Dyrektywy wymusza wyłącznego dostępu w odniesieniu do `critical` dyrektywy w wszystkie wątki, nie tylko zespół.

- Dyrektywy może nigdy nie mają powiązań każdej dyrektywy poza najbardziej dynamicznie otaczający `parallel`.

## <a name="29-directive-nesting"></a>2.9 zagnieżdżanie dyrektywy

Dynamiczne zagnieżdżanie dyrektyw muszą być zgodne z następującymi zasadami:

- A `parallel` dyrektywy dynamicznie wewnątrz innego `parallel` logicznie ustanawia nowy zespół, który składa się z bieżącym wątkiem, chyba że zagnieżdżone równoległości jest włączona.

- `for`, `sections`, i `single` dyrektyw, które powiązania do tej samej `parallel` nie mogą być zagnieżdżone wewnątrz siebie nawzajem.

- `critical` dyrektywy o takiej samej nazwie, nie mogą być zagnieżdżone wewnątrz siebie nawzajem. Należy pamiętać, że to ograniczenie nie jest wystarczające do uniknięcia zakleszczenia.

- `for`, `sections`, i `single` dyrektywy nie są dozwolone w zakresie dynamiczne `critical`, `ordered`, i `master` regionów, jeśli dyrektywy powiązania do tej samej `parallel` jako regionów.

- `barrier` dyrektywy nie są dozwolone w zakresie dynamiczne `for`, `ordered`, `sections`, `single`, `master`, i `critical` regionów, jeśli dyrektywy powiązania do tej samej `parallel` jako regionów.

- `master` dyrektywy nie są dozwolone w zakresie dynamiczne `for`, `sections`, i `single` dyrektywy Jeśli `master` dyrektywy powiązania do tej samej `parallel` jako dyrektyw podziału pracy.

- `ordered` dyrektywy nie są dozwolone w zakres dynamiczny `critical` regionów, jeśli dyrektywy powiązania do tej samej `parallel` jako regionów.

- Wszystkie dyrektywy, które są dozwolone podczas wykonywania dynamicznie w ramach równoległego regionu również jest dozwolone, gdy wykonywane poza równoległego regionu. Po wykonaniu dynamicznie, poza regionem równolegle z określonych przez użytkownika, dyrektywa jest wykonywana przez zespół składa się z głównego wątku.
