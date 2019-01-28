---
title: 3. Funkcje biblioteki czasu wykonywania
ms.date: 01/17/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 4e72d2d74bb26f8eeeb422881cabf92630cced43
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087317"
---
# <a name="3-run-time-library-functions"></a>3. Funkcje biblioteki czasu wykonywania

Ten rozdział Opisuje funkcje biblioteki czasu wykonywania OpenMP C i C++. Nagłówek  **\<omp.h >** deklaruje dwa typy, kilka funkcji, które mogą służyć do kontrolowania i wysyłać zapytania do środowiska wykonywania równoległego oraz blokowanie funkcje, które mogą służyć do synchronizowania dostępu do danych.

Typ `omp_lock_t` jest typem obiektu może reprezentować, czy blokada jest dostępny, lub wątek posiada blokadę. Blokadami tymi są określane jako *proste blokad*.

Typ `omp_nest_lock_t` może reprezentować, że typ obiektu blokady jest dostępna lub tożsamość wątku, który jest właścicielem blokady i *zagnieżdżania liczba* (opisanych poniżej). Blokadami tymi są określane jako *zagnieżdżalnych blokad*.

Funkcje biblioteki są zewnętrzne funkcji z powiązaniem "C".

Opisy w tym rozdziale są podzielone na następujące tematy:

- [Funkcje środowiska wykonawczego](#31-execution-environment-functions)
- [Funkcje blokady wielowątkowości](#32-lock-functions)
- [Procedury chronometrażu](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 funkcje środowiska wykonawczego

Funkcje opisane w tej sekcji mają wpływ na i monitorować wątków, procesory i środowisko równoległe:

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

### <a name="311-ompsetnumthreads-function"></a>3.1.1 omp_set_num_threads — funkcja

`omp_set_num_threads` Funkcja ustawia domyślną liczbę wątków używanych na potrzeby później regionów równoległych, które nie określają `num_threads` klauzuli. Format jest następujący:

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

Wartość parametru *num_threads* musi być dodatnią liczbą całkowitą. Jego efektem zależy od tego, czy włączona jest dynamiczne Dostosowywanie liczby wątków. Aby uzyskać kompleksowy zestaw reguł o interakcji między `omp_set_num_threads` funkcji i dynamiczne Dostosowywanie wątków, zobacz [sekcji 2.3](2-directives.md#23-parallel-construct).

Funkcja ta ma wpływ opisanych powyżej, gdy wywoływana z części programu gdzie `omp_in_parallel` funkcja zwraca wartość zero. Jeśli jest wywoływana z części programu gdzie `omp_in_parallel` funkcja zwraca wartość różną od zera, zachowanie tej funkcji jest niezdefiniowane.

To wywołanie ma pierwszeństwo przed `OMP_NUM_THREADS` zmiennej środowiskowej. Wartość domyślna liczba wątków, które mogą być ustanowione przez wywołanie metody `omp_set_num_threads` lub poprzez skonfigurowanie `OMP_NUM_THREADS` zmiennej środowiskowej, może być jawnie przesłonięte na pojedynczym `parallel` dyrektywy, określając `num_threads` klauzuli.

#### <a name="cross-references"></a>Odsyłacze

- [omp_set_dynamic](#317-omp_set_dynamic-function) — funkcja
- [omp_get_dynamic](#318-omp_get_dynamic-function) — funkcja
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) zmiennej środowiskowej
- [num_threads](2-directives.md#23-parallel-construct) — klauzula

### <a name="312-ompgetnumthreads-function"></a>3.1.2 funkcja omp_get_num_threads

`omp_get_num_threads` Funkcja zwraca liczbę wątków obecnie w zespole wykonywania równoległego regionu, w którym jest wywoływana. Format jest następujący:

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

`num_threads` Klauzuli `omp_set_num_threads` funkcji i `OMP_NUM_THREADS` zmiennej środowiskowej kontrolować liczbę wątków w zespole.

Jeśli liczba wątków nie została jawnie ustawiona przez użytkownika, wartość domyślna to zdefiniowane w implementacji. Ta funkcja jest powiązana najbliższej otaczającej `parallel` dyrektywy. Wywoływana z serial część programu lub zagnieżdżone równoległego regionu, który jest serializowany, ta funkcja zwraca wartość 1.

#### <a name="cross-references"></a>Odsyłacze

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-ompgetmaxthreads-function"></a>3.1.3 omp_get_max_threads — funkcja

`omp_get_max_threads` Funkcji zwraca liczbę całkowitą, która ma musi być przynajmniej tak duże jak liczba wątków, które byłyby używane do utworzenia zespołu, jeśli równoległego regionu bez `num_threads` klauzuli były wyświetlane w tym momencie w kodzie. Format jest następujący:

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

Następujące określa dolną granicę dla wartości `omp_get_max_threads`:

```

threads-used-for-next-team
<= omp_get_max_threads
```

Pamiętaj, że jeśli inny równoległe używa regionu `num_threads` klauzuli żądania określoną liczbę wątków, gwarancji na dolnej granicy wynik `omp_get_max_threads` nie przechowuje długie.

`omp_get_max_threads` Wartość zwracaną przez funkcję można dynamicznie przydzielić wystarczającej ilości miejsca dla wszystkich wątków w zespole, utworzony w następnym równoległego regionu.

#### <a name="cross-references"></a>Odsyłacze

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num — funkcja

`omp_get_thread_num` Funkcja zwraca liczbę wątków, w w ramach jego zespołu wątku wykonującego funkcji. Polega liczba wątków między 0 a `omp_get_num_threads()`-1 (włącznie). Główny wątek zespołu znajduje się wątek 0.

Format jest następujący:

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

Jeśli wywołania będą regionowi serial `omp_get_thread_num` zwraca wartość 0. Wywołane z wnętrza zagnieżdżonych równoległego regionu, który jest serializowany, ta funkcja zwraca wartość 0.

#### <a name="cross-references"></a>Odsyłacze

- [omp_get_num_threads](#312-omp_get_num_threads-function) — funkcja

### <a name="315-ompgetnumprocs-function"></a>3.1.5 omp_get_num_procs — funkcja

`omp_get_num_procs` Funkcja zwraca liczbę procesorów, które są dostępne dla programu w momencie wywołania funkcji. Format jest następujący:

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-ompinparallel-function"></a>3.1.6 funkcja omp_in_parallel

`omp_in_parallel` Funkcja zwraca wartość różną od zera, jeśli jest to w ramach równoległego regionu wykonywanych równolegle zakres dynamiczny; w przeciwnym razie zwraca wartość 0. Format jest następujący:

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

Ta funkcja zwraca wartość różną od zera, gdy wywoływana z w obrębie regionu wykonywanych równolegle, w tym zagnieżdżone regionów, które są serializowane.

### <a name="317-ompsetdynamic-function"></a>3.1.7 omp_set_dynamic — funkcja

`omp_set_dynamic` Funkcji włącza lub wyłącza dynamiczne Dostosowywanie liczby dostępnych do wykonania regionów równoległych wątków. Format jest następujący:

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Jeśli *dynamic_threads* oblicza wartość różną od zera, liczba wątków, które są używane do wykonywania kolejnych regionów równoległych mogą być automatycznie dostosowywane przez środowisko wykonawcze najlepszego wykorzystania zasobów systemowych. W konsekwencji liczbę wątków, określone przez użytkownika jest maksymalnej liczby wątków. Liczba wątków w zespole wykonywania równoległego regionu pozostaje stały czas trwania tego równoległego regionu i zgłoszonych przez `omp_get_num_threads` funkcji.

Jeśli *dynamic_threads* ocenia 0, dynamiczne Dostosowywanie jest wyłączona.

Funkcja ta ma wpływ opisanych powyżej, gdy wywoływana z części programu gdzie `omp_in_parallel` funkcja zwraca wartość zero. Jeśli jest wywoływana z części programu gdzie `omp_in_parallel` funkcja zwraca wartość różną od zera, zachowanie tej funkcji jest niezdefiniowane.

Wywołanie `omp_set_dynamic` ma pierwszeństwo przed `OMP_DYNAMIC` zmiennej środowiskowej.

Wartość domyślna dla dynamicznego dostosowania wątków jest zdefiniowane w implementacji. W rezultacie kody użytkownika, które są zależne od określonej liczby wątków do wykonania poprawne jawnie Wyłącz dynamiczne wątków. Implementacje nie są wymagane, aby zapewnić możliwość dynamicznego dostosowania liczby wątków, ale są one wymagane zapewnia interfejs do obsługi przenoszenia na wszystkich platformach.

#### <a name="cross-references"></a>Odsyłacze

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-ompgetdynamic-function"></a>3.1.8 omp_get_dynamic — funkcja

`omp_get_dynamic` Funkcja zwraca wartość różną od zera, jeśli dynamiczne Dostosowywanie wątków jest włączona, a w przeciwnym razie zwraca wartość 0. Format jest następujący:

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

Jeśli wdrożenia nie implementuje dynamiczne Dostosowywanie liczby wątków, ta funkcja zawsze zwraca wartość 0.

#### <a name="cross-references"></a>Odsyłacze

- Opis wątku dynamicznego dostosowania, zobacz [omp_set_dynamic](#317-omp_set_dynamic-function).

### <a name="319-ompsetnested-function"></a>3.1.9 omp_set_nested — funkcja

`omp_set_nested` Funkcji włącza lub wyłącza równoległości zagnieżdżonych. Format jest następujący:

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

Jeśli *zagnieżdżonych* wynikiem jest 0, zagnieżdżone równoległości jest wyłączone, co jest ustawieniem domyślnym i zagnieżdżone regionów równoległych są serializowane i wykonywane przez bieżący wątek. W przeciwnym razie zagnieżdżonych równoległości jest włączona i regionów równoległych, które są zagnieżdżone mogą wdrażać dodatkowe wątki w celu utworzenia zagnieżdżonych zespołów.

Funkcja ta ma wpływ opisanych powyżej, gdy wywoływana z części programu gdzie `omp_in_parallel` funkcja zwraca wartość zero. Jeśli jest wywoływana z części programu gdzie `omp_in_parallel` funkcja zwraca wartość różną od zera, zachowanie tej funkcji jest niezdefiniowane.

To wywołanie ma pierwszeństwo przed `OMP_NESTED` zmiennej środowiskowej.

Po włączeniu zagnieżdżonych równoległości liczba wątków używanych do wykonywania zagnieżdżonych regionów równoległych jest zdefiniowane w implementacji. Co w efekcie CLS OpenMP implementacje są dozwolone do serializacji zagnieżdżonych regionów równoległych, nawet wtedy, gdy zagnieżdżony równoległości jest włączona.

#### <a name="cross-references"></a>Odsyłacze

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-ompgetnested-function"></a>3.1.10 funkcja omp_get_nested

`omp_get_nested` Funkcja zwraca wartość różną od zera, jeśli włączono zagnieżdżonych równoległości i 0, jeśli jest ona wyłączona. Aby uzyskać więcej informacji na zagnieżdżonych równoległości, zobacz [omp_set_nested](#319-omp_set_nested-function). Format jest następujący:

```cpp
#include <omp.h>
int omp_get_nested(void);
```

Jeśli implementacja nie implementuje zagnieżdżonych równoległości, ta funkcja zawsze zwraca wartość 0.

## <a name="32-lock-functions"></a>3.2 funkcje blokady

Funkcje opisane w tej sekcji manipulować blokad używane na potrzeby synchronizacji.

Dla następujących funkcji, zmienna blokady musi mieć typ `omp_lock_t`. Ta zmienna musi zostać oceniony jedynie za pomocą tych funkcji. Wszystkie funkcje blokady wymaga argumentu, który zawiera wskaźnik do `omp_lock_t` typu.

- [Funkcje omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) funkcja inicjuje prostą blokadą.
- [Funkcje omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) funkcja usuwa prostą blokadą.
- [Omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) funkcja oczekuje na prostą blokadą dostępne.
- [Funkcje omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) funkcja zwolni prostą blokadą.
- [Funkcje omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) funkcja sprawdza prostą blokadą.

Dla następujących funkcji, zmienna blokady musi mieć typ `omp_nest_lock_t`.  Ta zmienna musi zostać oceniony jedynie za pomocą tych funkcji. Wszystkie funkcje blokadą wymagają argument, który zawiera wskaźnik do `omp_nest_lock_t` typu.

- [Omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) funkcja inicjuje blokadą.
- [Omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) funkcja usuwa blokadą.
- [Omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) funkcja oczekuje na blokadę zagnieżdżalnych dostępne.
- [Omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) funkcja zwalnia blokadę zagnieżdżalnych.
- [Omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) funkcja sprawdza blokadą.

OpenMP — funkcje Zablokuj dostęp do zmiennej blokady w taki sposób, że mogą zawsze odczytywać i aktualizować aktualna wartość zmiennej blokady. W związku z tym, nie jest konieczne dla programu OpenMP uwzględnić jawne `flush` dyrektywy, aby upewnić się, że wartość zmiennej blokady jest spójna wśród różnych wątkach. (Może to być potrzebne `flush` dyrektywy, aby wartości innych zmiennych były spójne.)

### <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 funkcje omp_init_lock i omp_init_nest_lock

Te funkcje zapewniają jedynym sposobem inicjowanie blokadę. Każda funkcja inicjuje blokady skojarzonych z parametrem *blokady* do użycia w kolejnych wywołaniach. Format jest następujący:

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

Początkowy stan jest odblokowana (oznacza to, że żaden wątek nie jest właścicielem blokady). Na blokadę zagnieżdżalnych początkowa liczba zagnieżdżenia wynosi zero. Jest niezgodna, aby wywołać jedną z tych procedur ze zmienną blokady, który został już zainicjowany.

### <a name="322-ompdestroylock-and-ompdestroynestlock-functions"></a>3.2.2 funkcje omp_destroy_lock i omp_destroy_nest_lock

Te funkcje, upewnij się, że wskazywany zablokować zmiennej *blokady* nie został zainicjowany. Format jest następujący:

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

Jest niezgodne do wywoływania jednej z tych procedur, za pomocą zmiennej blokady, która ma niezainicjowane lub odblokować.

### <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 funkcje omp_set_lock i omp_set_nest_lock

Każda z tych funkcji blokuje wątek wykonywania funkcji, dopóki określona blokada jest dostępny, a następnie ustawia blokady. Prostą blokadą jest dostępna, jeśli jest odblokowane. Zagnieżdżalnych blokady jest dostępna, gdy jest odblokowana, czy jest on już własnością wątek wykonywania funkcji. Format jest następujący:

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Dla prostą blokadą argument `omp_set_lock` funkcja musi się odnosić do zmiennej zainicjowane blokady. Własność blokadę zostanie ustanowione wątek wykonywania funkcji.

Dla blokadą argument `omp_set_nest_lock` funkcja musi się odnosić do zmiennej zainicjowane blokady. Zagnieżdżanie licznik jest zwiększany i wątku otrzymuje lub zachowuje własność blokadę.

### <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 funkcje omp_unset_lock i omp_unset_nest_lock

Te funkcje zapewniają oznacza, że przy zwalnianiu własność blokadę. Format jest następujący:

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

Argument do każdej z tych funkcji musi wskazywać na zmienną zainicjowane blokady własnością wątku wykonywania funkcji. Zachowanie jest niezdefiniowane, jeśli wątek nie posiada tego blokady.

Dla prostą blokadą `omp_unset_lock` funkcja zwolni wątek wykonywania funkcji z na własność blokadę.

Na blokadę zagnieżdżalnych `omp_unset_nest_lock` funkcji zmniejsza liczbę zagnieżdżenia i wersji wątek wykonywania funkcji z na własność blokadę, jeśli wynikowy licznik osiągnie wartość zero.

### <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 funkcje omp_test_lock i omp_test_nest_lock

Spróbuj ustawić blokadę tych funkcji, ale nie blokują wykonanie wątku. Format jest następujący:

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

Argument musi wskazywać na zmienną zainicjowane blokady. Tych funkcji, spróbuj ustawić blokadę w taki sam sposób jak `omp_set_lock` i `omp_set_nest_lock`, z tą różnicą, że nie blokują wykonanie wątku.

Dla prostą blokadą `omp_test_lock` funkcja zwraca wartość różną od zera, jeśli pomyślnie ustawiono blokady; w przeciwnym razie zwraca wartość zero.

Na blokadę zagnieżdżalnych `omp_test_nest_lock` funkcja zwraca nową liczbę zagnieżdżenia, jeśli pomyślnie ustawiono blokady; w przeciwnym razie zwraca wartość zero.

## <a name="33-timing-routines"></a>3.3 procedury chronometrażu

Funkcje opisane w tej sekcji obsługują czasomierza przenośnych zgodnie z zegarem:

- [Omp_get_wtime](#331-omp_get_wtime-function) :: gettotalsize() zwróciło czasu upłynęło zgodnie z zegarem.
- [Omp_get_wtick](#332-omp_get_wtick-function) funkcja zwraca sekund między taktami zegara kolejnych.

### <a name="331-ompgetwtime-function"></a>3.3.1 funkcja omp_get_wtime

`omp_get_wtime` Funkcja zwraca wartość punktu zmiennoprzecinkową podwójnej precyzji równa czas zegarowy upłynęło w ciągu kilku sekund, ponieważ niektóre "godziny w przeszłości".  Rzeczywisty "czas w przeszłości" jest dowolną, ale ma gwarancję, nie należy zmieniać podczas wykonywania programu aplikacji. Format jest następujący:

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

Przewiduje się, że funkcja będzie służyć do pomiaru czas, jak pokazano w poniższym przykładzie:

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Zwracane są "Patrol wątku", który składający się nie muszą być globalnie spójne we wszystkich wątkach uczestniczących w aplikacji.

### <a name="332-ompgetwtick-function"></a>3.3.2 funkcja omp_get_wtick

`omp_get_wtick` Funkcja zwraca wartość punktu zmiennoprzecinkową podwójnej precyzji równa liczbie sekund między taktami zegara kolejnych. Format jest następujący:

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
