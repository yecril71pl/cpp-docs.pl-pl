---
title: 3. Funkcje bibliotek środowiska uruchomieniowego
ms.date: 05/13/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 553c9ff2ceff02dc7b72e9f11899dac9d1f0f612
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857960"
---
# <a name="3-run-time-library-functions"></a>3. funkcje biblioteki wykonawczej

Ta sekcja zawiera opis funkcji OpenMP C C++ i biblioteki wykonawczej. Nagłówek **\<OMP. h >** deklaruje dwa typy, kilka funkcji, które mogą służyć do kontrolowania i wykonywania zapytań dotyczących środowiska wykonywania równoległego oraz blokowania funkcji, których można użyć do synchronizowania dostępu do danych.

Typ `omp_lock_t` jest typem obiektu, który może reprezentować, że blokada jest dostępna lub że wątek jest Zablokowani. Te blokady są określane jako *proste blokady*.

Typ `omp_nest_lock_t` jest typem obiektu, który może reprezentować, że blokada jest dostępna lub zarówno tożsamość wątku będącego właścicielem blokady, jak i *liczby zagnieżdżenia* (opisane poniżej). Te blokady są nazywane *blokadami zagnieżdżenia*.

Funkcje biblioteki są funkcjami zewnętrznymi z powiązaniem "C".

Opisy zawarte w tym rozdziale są podzielone na następujące tematy:

- [Funkcje środowiska wykonawczego](#31-execution-environment-functions)
- [Funkcje blokowania](#32-lock-functions)
- [Procedury chronometrażu](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>Funkcje środowiska wykonywania 3,1

Funkcje opisane w tej sekcji dotyczą i monitorują wątki, procesory i środowisko równoległe:

- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_get_max_threads](#313-omp_get_max_threads-function)
- [omp_get_thread_num](#314-omp_get_thread_num-function)
- [omp_get_num_procs](#315-omp_get_num_procs-function)
- [omp_in_parallel](#316-omp_in_parallel-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [omp_get_dynamic](#318-omp_get_dynamic-function)
- [omp_set_nested](#319-omp_set_nested-function)
- [omp_get_nested](#3110-omp_get_nested-function)

### <a name="311-omp_set_num_threads-function"></a>3.1.1 omp_set_num_threads funkcja

Funkcja `omp_set_num_threads` ustawia domyślną liczbę wątków do użycia w nowszych regionach równoległych, które nie określają klauzuli `num_threads`. Format jest następujący:

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

Wartość parametru *num_threads* musi być dodatnią liczbą całkowitą. Jego wpływ zależy od tego, czy włączone jest dynamiczne dopasowanie liczby wątków. Aby uzyskać kompleksowy zestaw reguł dotyczących interakcji między funkcją `omp_set_num_threads` i dynamiczne dostosowywanie wątków, zobacz [sekcję 2,3](2-directives.md#23-parallel-construct).

Ta funkcja ma efekty opisane powyżej, gdy jest wywoływana z części programu, w której funkcja `omp_in_parallel` zwraca zero. Jeśli jest wywoływana z części programu, w której funkcja `omp_in_parallel` zwraca wartość różną od zera, zachowanie tej funkcji jest niezdefiniowane.

To wywołanie ma pierwszeństwo przed zmienną środowiskową `OMP_NUM_THREADS`. Wartość domyślna liczby wątków, które mogą zostać ustanowione przez wywołanie `omp_set_num_threads` lub przez ustawienie zmiennej środowiskowej `OMP_NUM_THREADS`, można jawnie przesłonić w jednej dyrektywie `parallel`, określając klauzulę `num_threads`.

Aby uzyskać więcej informacji, zobacz [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Odsyłacze

- Funkcja [omp_set_dynamic](#317-omp_set_dynamic-function)
- Funkcja [omp_get_dynamic](#318-omp_get_dynamic-function)
- Zmienna środowiskowa [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- klauzula [num_threads](2-directives.md#23-parallel-construct)

### <a name="312-omp_get_num_threads-function"></a>3.1.2 omp_get_num_threads funkcja

Funkcja `omp_get_num_threads` zwraca liczbę wątków aktualnie znajdujących się w zespole wykonujących równoległy region, z którego jest wywoływany. Format jest następujący:

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

Klauzula `num_threads`, funkcja `omp_set_num_threads` i zmienna środowiskowa `OMP_NUM_THREADS` decydują o liczbie wątków w zespole.

Jeśli liczba wątków nie została jawnie ustawiona przez użytkownika, wartością domyślną jest zdefiniowana implementacja. Ta funkcja wiąże się z najbliższą dołączaną dyrektywą `parallel`. Jeśli wywoływana z części szeregowej programu lub z zagnieżdżonego równoległego regionu, który jest serializowany, ta funkcja zwraca 1.

Aby uzyskać więcej informacji, zobacz [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Odsyłacze

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a>3.1.3 Funkcja omp_get_max_threads

Funkcja `omp_get_max_threads` zwraca liczbę całkowitą, która gwarantuje, że jest równa co najmniej tak dużej liczbie wątków, która mogłaby zostać użyta w celu utworzenia zespołu, jeśli w tym momencie w kodzie nie były widoczne regiony równoległe bez klauzuli `num_threads`. Format jest następujący:

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

Poniżej przedstawiono dolną granicę wartości `omp_get_max_threads`:

```

threads-used-for-next-team
<= omp_get_max_threads
```

Należy zauważyć, że jeśli inny region równoległy używa klauzuli `num_threads`, aby zażądać określonej liczby wątków, gwarancja w dolnej granicy wyniku `omp_get_max_threads` nie jest długi.

Wartość zwracana przez funkcję `omp_get_max_threads` może służyć do dynamicznego przydzielania wystarczającej ilości miejsca dla wszystkich wątków w zespole utworzonych w następnym regionie równoległym.

#### <a name="cross-references"></a>Odsyłacze

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a>3.1.4 omp_get_thread_num funkcja

Funkcja `omp_get_thread_num` zwraca numer wątku, w ramach którego zespół wykonuje funkcję. Numer wątku należy do przedziału od 0 do `omp_get_num_threads()`-1 włącznie. Głównym wątkiem zespołu jest wątek 0.

Format jest następujący:

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

W przypadku wywołania z regionu szeregowego `omp_get_thread_num` zwraca wartość 0. Jeśli wywoływana z w zagnieżdżonym równoległym regionie, który jest serializowany, ta funkcja zwraca wartość 0.

#### <a name="cross-references"></a>Odsyłacze

- Funkcja [omp_get_num_threads](#312-omp_get_num_threads-function)

### <a name="315-omp_get_num_procs-function"></a>3.1.5 omp_get_num_procs funkcja

Funkcja `omp_get_num_procs` zwraca liczbę procesorów, które są dostępne dla programu w momencie wywołania funkcji. Format jest następujący:

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a>3.1.6 — funkcja omp_in_parallel

Funkcja `omp_in_parallel` zwraca wartość różną od zera, jeśli jest wywoływana w dynamicznym obszarze równoległego wykonywania równolegle; w przeciwnym razie zwraca wartość 0. Format jest następujący:

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

Ta funkcja zwraca wartość różną od zera, gdy wywoływana z poziomu regionu wykonuje równolegle, w tym zagnieżdżonych regionów, które są serializowane.

### <a name="317-omp_set_dynamic-function"></a>3.1.7 — funkcja omp_set_dynamic

Funkcja `omp_set_dynamic` włącza lub wyłącza dynamiczne dopasowanie liczby wątków dostępnych na potrzeby wykonywania regionów równoległych. Format jest następujący:

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Jeśli *dynamic_threads* ma wartość różną od zera, liczba wątków, które są używane do wykonywania nadchodzących regionów równoległych, może być automatycznie dostosowywana przez środowisko uruchomieniowe, aby najlepiej wykorzystać zasoby systemowe. W związku z tym liczba wątków określona przez użytkownika to maksymalna liczba wątków. Liczba wątków w zespole wykonujących równoległe regiony pozostaje stała na czas trwania tego regionu równoległego i jest raportowana przez funkcję `omp_get_num_threads`.

Jeśli *dynamic_threads* ma wartość 0, dynamiczne dopasowanie jest wyłączone.

Ta funkcja ma efekty opisane powyżej, gdy jest wywoływana z części programu, w której funkcja `omp_in_parallel` zwraca zero. Jeśli jest wywoływana z części programu, w której funkcja `omp_in_parallel` zwraca wartość różną od zera, zachowanie tej funkcji jest niezdefiniowane.

Wywołanie `omp_set_dynamic` ma pierwszeństwo przed zmienną środowiskową `OMP_DYNAMIC`.

Wartość domyślna dla dynamicznego dostosowania wątków jest definiowana przez implementację. W związku z tym kody użytkowników, które zależą od określonej liczby wątków do prawidłowego wykonania, powinny jawnie wyłączyć wątki dynamiczne. Implementacje nie są wymagane, aby zapewnić możliwość dynamicznego dostosowywania liczby wątków, ale są one wymagane, aby zapewnić obsługę przenośności na wszystkich platformach.

#### <a name="microsoft-specific"></a>specyficzne dla firmy Microsoft

Bieżąca obsługa `omp_get_dynamic` i `omp_set_dynamic` jest następująca: 

Parametr wejściowy, który ma `omp_set_dynamic` nie ma wpływu na zasady wątkowości i nie zmienia liczby wątków. `omp_get_num_threads` zawsze zwraca numer zdefiniowany przez użytkownika, jeśli jest ustawiony, lub domyślny numer wątku. W bieżącej implementacji firmy Microsoft `omp_set_dynamic(0)` powoduje wyłączenie wątku dynamicznego, dzięki czemu istniejący zestaw wątków może być ponownie używany przez następujący równoległy region. `omp_set_dynamic(1)` włącza wielowątkowość dynamiczną przez odrzucenie istniejącego zestawu wątków i utworzenie nowego zestawu dla nadchodzącego regionu równoległego. Liczba wątków w nowym zestawie jest taka sama jak w starym zestawie i jest oparta na wartości zwracanej `omp_get_num_threads`. W związku z tym w celu uzyskania najlepszej wydajności Użyj `omp_set_dynamic(0)`, aby ponownie wykorzystać istniejące wątki.

#### <a name="cross-references"></a>Odsyłacze

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a>3.1.8 — funkcja omp_get_dynamic

Funkcja `omp_get_dynamic` zwraca wartość różną od zera, jeśli włączono dynamiczne dostosowywanie wątków i zwraca wartość 0 w przeciwnym razie. Format jest następujący:

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

Jeśli implementacja nie implementuje dynamicznego dostosowywania liczby wątków, ta funkcja zawsze zwróci wartość 0. Aby uzyskać więcej informacji, zobacz [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Odsyłacze

- Opis dostosowania wątku dynamicznego można znaleźć w temacie [omp_set_dynamic](#317-omp_set_dynamic-function).

### <a name="319-omp_set_nested-function"></a>3.1.9 — funkcja omp_set_nested

Funkcja `omp_set_nested` włącza lub wyłącza zagnieżdżoną równoległość. Format jest następujący:

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

Jeśli wartość *zagnieżdżona* jest równa 0, zagnieżdżona równoległość jest wyłączona, co jest ustawieniem domyślnym, a zagnieżdżone regiony równoległe są serializowane i wykonywane przez bieżący wątek. W przeciwnym razie zagnieżdżona równoległość jest włączona, a równoległe regiony mogą wdrożyć dodatkowe wątki do tworzenia zagnieżdżonych zespołów.

Ta funkcja ma efekty opisane powyżej, gdy jest wywoływana z części programu, w której funkcja `omp_in_parallel` zwraca zero. Jeśli jest wywoływana z części programu, w której funkcja `omp_in_parallel` zwraca wartość różną od zera, zachowanie tej funkcji jest niezdefiniowane.

To wywołanie ma pierwszeństwo przed zmienną środowiskową `OMP_NESTED`.

Gdy włączona jest zagnieżdżona równoległość, liczba wątków używanych do wykonywania zagnieżdżonych regionów równoległych jest definiowana przez implementację. W rezultacie implementacje zgodne ze standardem OpenMP mogą serializować zagnieżdżone regiony równoległe nawet wtedy, gdy włączona jest zagnieżdżona równoległość.

#### <a name="cross-references"></a>Odsyłacze

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a>3.1.10 — Funkcja omp_get_nested

Funkcja `omp_get_nested` zwraca wartość różną od zera, jeśli jest włączona zagnieżdżona równoległa i 0, jeśli jest wyłączona. Aby uzyskać więcej informacji na temat zagnieżdżonej równoległości, zobacz [omp_set_nested](#319-omp_set_nested-function). Format jest następujący:

```cpp
#include <omp.h>
int omp_get_nested(void);
```

Jeśli implementacja nie implementuje zagnieżdżonej równoległości, ta funkcja zawsze zwróci wartość 0.

## <a name="32-lock-functions"></a>3,2 funkcji blokowania

Funkcje opisane w tej sekcji manipulują blokadami używanymi do synchronizacji.

Dla następujących funkcji zmienna Lock musi mieć typ `omp_lock_t`. Dostęp do tej zmiennej należy uzyskać tylko za poorednictwem tych funkcji. Wszystkie funkcje blokowania wymagają argumentu, który ma wskaźnik do `omp_lock_t` typu.

- Funkcja [omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) inicjuje prostą blokadę.
- Funkcja [omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) usuwa prostą blokadę.
- Funkcja [omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) czeka na dostęp do prostej blokady.
- Funkcja [omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) zwalnia prostą blokadę.
- Funkcja [omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) testuje prostą blokadę.

Dla następujących funkcji zmienna Lock musi mieć typ `omp_nest_lock_t`.  Dostęp do tej zmiennej należy uzyskać tylko za poorednictwem tych funkcji. Wszystkie funkcje blokowania zagnieżdżenia wymagają argumentu, który ma wskaźnik do typu `omp_nest_lock_t`.

- Funkcja [omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) inicjuje blokadę zagnieżdżenia.
- Funkcja [omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) usuwa blokadę zagnieżdżenia.
- Funkcja [omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) czeka na dostęp do zagnieżdżenia blokady.
- Funkcja [omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) zwalnia blokadę zagnieżdżenia.
- Funkcja [omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) sprawdza blokadę zagnieżdżenia.

Funkcje blokowania OpenMP uzyskują dostęp do zmiennej blokady w taki sposób, aby zawsze odczytywać i aktualizować najbardziej aktualną wartość zmiennej blokady. W związku z tym nie jest konieczne, aby program OpenMP zawierał jawne dyrektywy `flush`, aby upewnić się, że wartość zmiennej blokady jest spójna wśród różnych wątków. (Może istnieć potrzeba, aby `flush` dyrektywy, aby wartości innych zmiennych były spójne).

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a>3.2.1 omp_init_lock i funkcje omp_init_nest_lock

Te funkcje zapewniają jedynym sposobem zainicjowania blokady. Każda funkcja inicjuje blokadę skojarzoną z *blokadą* parametru do użycia w nadchodzących wywołaniach. Format jest następujący:

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

Stan początkowy jest odblokowany (oznacza to, że żaden wątek nie jest właścicielem blokady). W przypadku blokady z zagnieżdżeniem początkowa liczba zagnieżdżenia wynosi zero. Nie jest on zgodny z wywołaniem jednej z tych procedur z zmienną blokady, która została już zainicjowana.

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a>3.2.2 omp_destroy_lock i omp_destroy_nest_lock Functions

Te funkcje upewniają *się, że blokada zmiennej nie* została zainicjowana. Format jest następujący:

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

Nie jest on zgodny z wywołaniem jednej z tych procedur z zmienną blokady, która nie została zainicjowana lub odblokowana.

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a>3.2.3 omp_set_lock i funkcje omp_set_nest_lock

Każda z tych funkcji blokuje wątek wykonujący funkcję do momentu udostępnienia określonej blokady, a następnie ustawia blokadę. Prosta blokada jest dostępna w przypadku jej odblokowania. Blokada zagnieżdżona jest dostępna w przypadku jej odblokowania lub, jeśli jest już własnością wątku wykonującego funkcję. Format jest następujący:

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

W przypadku prostej blokady argument funkcji `omp_set_lock` musi wskazywać zainicjowaną zmienną blokady. Własność blokady jest przyznawana wątekowi wykonującemu funkcję.

W przypadku blokady z zagnieżdżeniem argument funkcji `omp_set_nest_lock` musi wskazywać zainicjowaną zmienną blokady. Licznik zagnieżdżenia jest zwiększany, a wątek jest przyznany lub utrzymuje własność blokady.

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a>3.2.4 omp_unset_lock i funkcje omp_unset_nest_lock

Te funkcje zapewniają środki zwalniania własności blokady. Format jest następujący:

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

Argument dla każdej z tych funkcji musi wskazywać zainicjowaną zmienną blokady, której właścicielem jest wątek wykonujący funkcję. Zachowanie jest niezdefiniowane, jeśli wątek nie jest jego własnością.

W przypadku prostej blokady funkcja `omp_unset_lock` zwalnia wątek wykonujący funkcję z własności blokady.

W przypadku blokady z zagnieżdżeniem funkcja `omp_unset_nest_lock` zmniejsza liczbę zagnieżdżenia i zwalnia wątek wykonujący funkcję z własności blokady, Jeśli wynikowa liczba wynosi zero.

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a>3.2.5 omp_test_lock i funkcje omp_test_nest_lock

Te funkcje podejmują próbę ustawienia blokady, ale nie blokują wykonywania wątku. Format jest następujący:

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

Argument musi wskazywać zainicjowaną zmienną blokady. Te funkcje podejmują próbę ustawienia blokady w taki sam sposób jak `omp_set_lock` i `omp_set_nest_lock`, z tą różnicą, że nie blokują wykonywania wątku.

W przypadku prostej blokady funkcja `omp_test_lock` zwraca wartość różną od zera, jeśli Blokada została pomyślnie ustawiona; w przeciwnym razie zwraca wartość zero.

W przypadku blokady z zagnieżdżeniem funkcja `omp_test_nest_lock` zwraca nową liczbę zagnieżdżenia, jeśli Blokada została pomyślnie ustawiona; w przeciwnym razie zwraca wartość zero.

## <a name="33-timing-routines"></a>3,3 procedury czasu

Funkcje opisane w tej sekcji obsługują przenośne czasomierze zegarowe:

- Funkcja [omp_get_wtime](#331-omp_get_wtime-function) zwraca czas zegara, który upłynął.
- Funkcja [omp_get_wtick](#332-omp_get_wtick-function) zwraca sekundy między kolejnymi taktami zegara.

### <a name="331-omp_get_wtime-function"></a>3.3.1 funkcja omp_get_wtime

Funkcja `omp_get_wtime` zwraca wartość zmiennoprzecinkową o podwójnej precyzji równą czasowi przekroczenia zegara ściany w sekundach od pewnego czasu w przeszłości.  Rzeczywisty "czas w przeszłości" jest dowolny, ale nie jest on zmieniany podczas wykonywania programu aplikacji. Format jest następujący:

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

Przewiduje się, że funkcja zostanie użyta do mierzenia czasu, który upłynął, jak pokazano w następującym przykładzie:

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Zwracane czasy to "czasy poszczególnych wątków", co oznacza, że nie są one wymagane do globalnej spójności wszystkich wątków uczestniczących w aplikacji.

### <a name="332-omp_get_wtick-function"></a>3.3.2 — Funkcja omp_get_wtick

Funkcja `omp_get_wtick` zwraca wartość zmiennoprzecinkową o podwójnej precyzji równą liczbie sekund między kolejnymi taktami zegara. Format jest następujący:

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
