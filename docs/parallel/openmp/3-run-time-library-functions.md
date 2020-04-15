---
title: 3. Funkcje bibliotek środowiska uruchomieniowego
ms.date: 05/13/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 767c006b0a2d81af4d1f8f2e23f84d7847326f31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370273"
---
# <a name="3-run-time-library-functions"></a>3. Funkcje biblioteki w czasie wykonywania

W tej sekcji opisano funkcje biblioteki wyklatki OpenMP C i C++. Nagłówek ** \<omp.h>** deklaruje dwa typy, kilka funkcji, które mogą służyć do kontrolowania i wykonywania zapytań środowiska wykonywania równoległego i blokowania funkcji, które mogą służyć do synchronizowania dostępu do danych.

Typ `omp_lock_t` jest typem obiektu, który może reprezentować, że blokada jest dostępna lub że wątek jest właścicielem blokady. Zamki te są określane jako *proste zamki*.

Typ `omp_nest_lock_t` jest typem obiektu, który może reprezentować, że blokada jest dostępna, albo zarówno tożsamość wątku, który jest właścicielem blokady, jak i *liczbę zagnieżdżeń* (opisaną poniżej). Zamki te są określane jako *blokady zagnieżdżone*.

Funkcje biblioteki są funkcjami zewnętrznymi z powiązaniem "C".

Opisy w tym rozdziale są podzielone na następujące tematy:

- [Funkcje środowiska wykonywania](#31-execution-environment-functions)
- [Funkcje blokowania](#32-lock-functions)
- [Procedury pomiaru czasu](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 Funkcje środowiska wykonywania

Funkcje opisane w tej sekcji wpływają na i monitorują wątki, procesory i środowisko równoległe:

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

### <a name="311-omp_set_num_threads-function"></a><a name="311-omp_set_num_threads-function"></a>3.1.1 funkcja omp_set_num_threads

Funkcja `omp_set_num_threads` ustawia domyślną liczbę wątków do użycia dla późniejszych regionów `num_threads` równoległych, które nie określają klauzuli. Format jest następujący:

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

Wartość parametru *num_threads* musi być dodatnią całkowitej liczby. Jego efekt zależy od tego, czy dynamiczna regulacja liczby wątków jest włączona. Aby uzyskać kompleksowy zestaw reguł `omp_set_num_threads` dotyczących interakcji między funkcją a dynamiczną regulacją wątków, zobacz [sekcję 2.3](2-directives.md#23-parallel-construct).

Ta funkcja ma efekty opisane powyżej, gdy wywoływane `omp_in_parallel` z części programu, gdzie funkcja zwraca zero. Jeśli jest wywoływana z części programu, `omp_in_parallel` w której funkcja zwraca wartość niezerową, zachowanie tej funkcji jest niezdefiniowane.

To wywołanie ma `OMP_NUM_THREADS` pierwszeństwo przed zmienną środowiskową. Wartość domyślna dla liczby wątków, które mogą `omp_set_num_threads` być ustanowione `OMP_NUM_THREADS` przez wywołanie lub ustawienie zmiennej `parallel` środowiskowej, można `num_threads` jawnie zastąpić na jednej dyrektywy, określając klauzulę.

Aby uzyskać więcej informacji, zobacz [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Odsyłacze

- [omp_set_dynamic](#317-omp_set_dynamic-function) funkcja
- [omp_get_dynamic](#318-omp_get_dynamic-function) funkcja
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) zmienna środowiskowa
- [num_threads klauzula](2-directives.md#23-parallel-construct)

### <a name="312-omp_get_num_threads-function"></a><a name="312-omp_get_num_threads-function"></a>3.1.2 funkcja omp_get_num_threads

Funkcja `omp_get_num_threads` zwraca liczbę wątków aktualnie w zespole wykonującym region równoległy, z którego jest wywoływana. Format jest następujący:

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

Klauzula, `num_threads` `omp_set_num_threads` funkcja i `OMP_NUM_THREADS` zmienna środowiskowa kontrolują liczbę wątków w zespole.

Jeśli liczba wątków nie została jawnie ustawiona przez użytkownika, wartość domyślna jest zdefiniowana w implementacji. Ta funkcja wiąże się z `parallel` najbliższą otaczającą dyrektywą. Jeśli wywoływane z szeregowej części programu lub z zagnieżdżonego regionu równoległego, który jest serializowany, ta funkcja zwraca 1.

Aby uzyskać więcej informacji, zobacz [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Odsyłacze

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a><a name="313-omp_get_max_threads-function"></a>3.1.3 funkcja omp_get_max_threads

Funkcja `omp_get_max_threads` zwraca liczbę całkowitą, która jest gwarantowana być co najmniej tak duży, jak liczba wątków, które `num_threads` będą używane do tworzenia zespołu, jeśli region równoległy bez klauzuli były widoczne w tym momencie w kodzie. Format jest następujący:

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

Poniżej podaje się dolną granicę `omp_get_max_threads`wartości:

> *wątki używane dla następnego zespołu* <= `omp_get_max_threads`

Należy zauważyć, że jeśli `num_threads` inny region równoległy używa klauzuli, aby zażądać określonej `omp_get_max_threads` liczby wątków, gwarancja w dolnej granicy wyniku nie jest już wstrzymywać.

Wartość `omp_get_max_threads` zwracana funkcji może służyć do dynamicznego przydzielania wystarczającej ilości miejsca dla wszystkich wątków w zespole utworzonym w następnym regionie równoległym.

#### <a name="cross-references"></a>Odsyłacze

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a><a name="314-omp_get_thread_num-function"></a>3.1.4 funkcja omp_get_thread_num

Funkcja `omp_get_thread_num` zwraca numer wątku, w jego zespole, wątku wykonującego funkcję. Liczba wątku znajduje się `omp_get_num_threads()`między 0 i -1 włącznie. Wątek główny zespołu to wątek 0.

Format jest następujący:

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

Jeśli wywoływane z `omp_get_thread_num` regionu szeregowego, zwraca 0. Jeśli wywoływane z poziomu zagnieżdżonego regionu równoległego, który jest serializowany, ta funkcja zwraca 0.

#### <a name="cross-references"></a>Odsyłacze

- [omp_get_num_threads](#312-omp_get_num_threads-function) funkcja

### <a name="315-omp_get_num_procs-function"></a><a name="315-omp_get_num_procs-function"></a>3.1.5 funkcja omp_get_num_procs

Funkcja `omp_get_num_procs` zwraca liczbę procesorów, które są dostępne dla programu w czasie wywoływania funkcji. Format jest następujący:

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a><a name="316-omp_in_parallel-function"></a>3.1.6 funkcja omp_in_parallel

Funkcja `omp_in_parallel` zwraca wartość niezerową, jeśli jest wywoływana w dynamicznym zakresie równoległego regionu wykonywanego równolegle; w przeciwnym razie zwraca wartość 0. Format jest następujący:

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

Ta funkcja zwraca wartość niezerową, gdy wywoływane z poziomu regionu wykonywania równolegle, w tym zagnieżdżonych regionów, które są serializowane.

### <a name="317-omp_set_dynamic-function"></a><a name="317-omp_set_dynamic-function"></a>3.1.7 funkcja omp_set_dynamic

Funkcja `omp_set_dynamic` włącza lub wyłącza dynamiczne dostosowanie liczby wątków dostępnych do wykonywania regionów równoległych. Format jest następujący:

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Jeśli *dynamic_threads* ma wartość niezerową, liczba wątków, które są używane do wykonywania nadchodzących regionów równoległych może być automatycznie dostosowywana przez środowisko wykonawcze, aby jak najlepiej wykorzystać zasoby systemowe. W konsekwencji liczba wątków określonych przez użytkownika jest maksymalna liczba wątków. Liczba wątków w zespole wykonującym region równoległy pozostaje stała na czas trwania tego `omp_get_num_threads` regionu równoległego i jest raportowana przez funkcję.

Jeśli *dynamic_threads* ma wartość 0, dopasowanie dynamiczne jest wyłączone.

Ta funkcja ma efekty opisane powyżej, gdy wywoływane `omp_in_parallel` z części programu, gdzie funkcja zwraca zero. Jeśli jest wywoływana z części programu, `omp_in_parallel` w której funkcja zwraca wartość niezerową, zachowanie tej funkcji jest niezdefiniowane.

Wywołanie `omp_set_dynamic` ma pierwszeństwo `OMP_DYNAMIC` przed zmienną środowiskową.

Domyślnie dla dynamicznego dostosowania wątków jest zdefiniowana implementacja. W rezultacie kody użytkowników, które zależą od określonej liczby wątków do poprawnego wykonania należy jawnie wyłączyć wątki dynamiczne. Implementacje nie są wymagane, aby zapewnić możliwość dynamicznego dostosowywania liczby wątków, ale są one wymagane do zapewnienia interfejsu do obsługi przenośności na wszystkich platformach.

#### <a name="microsoft-specific"></a>specyficzne dla firmy Microsoft

Obecne wsparcie `omp_get_dynamic` i `omp_set_dynamic` jest następujące:

Parametr wejściowy `omp_set_dynamic` do nie wpływa na zasady wątków i nie zmienia liczby wątków. `omp_get_num_threads`zawsze zwraca numer zdefiniowany przez użytkownika, jeśli jest ustawiony, lub domyślny numer wątku. W bieżącej implementacji firmy Microsoft wyłącza wątki dynamiczne, `omp_set_dynamic(0)` dzięki czemu istniejący zestaw wątków może być ponownie użyczony dla następującego regionu równoległego. `omp_set_dynamic(1)`włącza wątki dynamiczne, odrzucając istniejący zestaw wątków i tworząc nowy zestaw dla nadchodzącego regionu równoległego. Liczba wątków w nowym zestawie jest taka sama jak stary zestaw i `omp_get_num_threads`jest oparta na wartości zwracanej . W związku z tym `omp_set_dynamic(0)` dla najlepszej wydajności, należy użyć ponownie istniejących wątków.

#### <a name="cross-references"></a>Odsyłacze

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a><a name="318-omp_get_dynamic-function"></a>3.1.8 funkcja omp_get_dynamic

Funkcja `omp_get_dynamic` zwraca wartość niezerową, jeśli włączono dynamiczne dostosowanie wątków i zwraca wartość 0 w przeciwnym razie. Format jest następujący:

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

Jeśli implementacja nie implementuje dynamicznej korekty liczby wątków, ta funkcja zawsze zwraca wartość 0. Aby uzyskać więcej informacji, zobacz [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Odsyłacze

- Aby uzyskać opis dynamicznej regulacji gwintu, zobacz [omp_set_dynamic](#317-omp_set_dynamic-function).

### <a name="319-omp_set_nested-function"></a><a name="319-omp_set_nested-function"></a>3.1.9 funkcja omp_set_nested

Funkcja `omp_set_nested` włącza lub wyłącza równoległości zagnieżdżone. Format jest następujący:

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

Jeśli *zagnieżdżone* ma wartość 0, równoległość zagnieżdżona jest wyłączona, co jest wartością domyślną, a zagnieżdżone równoległe regiony są serializowane i wykonywane przez bieżący wątek. W przeciwnym razie zagnieżdżony równoległości jest włączona i równoległych regionów, które są zagnieżdżone może wdrożyć dodatkowe wątki do tworzenia zespołów zagnieżdżonych.

Ta funkcja ma efekty opisane powyżej, gdy wywoływane `omp_in_parallel` z części programu, gdzie funkcja zwraca zero. Jeśli jest wywoływana z części programu, `omp_in_parallel` w której funkcja zwraca wartość niezerową, zachowanie tej funkcji jest niezdefiniowane.

To wywołanie ma `OMP_NESTED` pierwszeństwo przed zmienną środowiskową.

Gdy równoległość zagnieżdżona jest włączona, liczba wątków używanych do wykonywania zagnieżdżonych regionów równoległych jest zdefiniowana implementacji. W rezultacie implementacje zgodne ze standardem OpenMP mogą serializować zagnieżdżone regiony równoległe, nawet jeśli włączono równoległość zagnieżdżoną.

#### <a name="cross-references"></a>Odsyłacze

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a><a name="3110-omp_get_nested-function"></a>3.1.10 funkcja omp_get_nested

Funkcja `omp_get_nested` zwraca wartość niezerową, jeśli zagnieżdżony równoległość jest włączona i 0, jeśli jest wyłączona. Aby uzyskać więcej informacji na temat równoległości zagnieżdżonej, zobacz [omp_set_nested](#319-omp_set_nested-function). Format jest następujący:

```cpp
#include <omp.h>
int omp_get_nested(void);
```

Jeśli implementacja nie implementuje równoległości zagnieżdżonej, ta funkcja zawsze zwraca wartość 0.

## <a name="32-lock-functions"></a>3.2 Funkcje blokowania

Funkcje opisane w tej sekcji manipulują blokadami używanymi do synchronizacji.

W przypadku następujących funkcji zmienna `omp_lock_t`blokady musi mieć typ . Ta zmienna może być dostępna tylko za pośrednictwem tych funkcji. Wszystkie funkcje blokady wymagają argumentu, który ma wskaźnik do wpisywać. `omp_lock_t`

- Funkcja [omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) inicjuje prostą blokadę.
- Funkcja [omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) usuwa prostą blokadę.
- Funkcja [omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) czeka, aż dostępna jest prosta blokada.
- Funkcja [omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) zwalnia prosty zamek.
- Funkcja [omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) testuje prostą blokadę.

W przypadku następujących funkcji zmienna `omp_nest_lock_t`blokady musi mieć typ .  Ta zmienna może być dostępna tylko za pośrednictwem tych funkcji. Wszystkie funkcje blokady zagnieżdżonej wymagają argumentu, który ma wskaźnik do wpisywany. `omp_nest_lock_t`

- Funkcja [omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) inicjuje blokadę zagnieżdżoną.
- Funkcja [omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) usuwa blokadę zagnieżdżoną.
- Funkcja [omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) czeka, aż dostępna będzie blokada zagnieżdżania.
- Funkcja [omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) zwalnia blokadę zagnieżdżoną.
- Funkcja [omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) testuje blokadę zagnieżdżoną.

Funkcje blokady OpenMP uzyskują dostęp do zmiennej blokady w taki sposób, że zawsze odczytują i aktualizują najbardziej aktualną wartość zmiennej blokady. W związku z tym nie jest konieczne dla `flush` programu OpenMP do uwzględnienia jawnych dyrektyw, aby upewnić się, że wartość zmiennej blokady jest spójna między różnymi wątkami. (Może zajmą `flush` się, że dyrektywy będą zgodne z wartościami innych zmiennych).

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a><a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a>3.2.1 funkcje omp_init_lock i omp_init_nest_lock

Te funkcje zapewniają jedyny sposób inicjowania blokady. Każda funkcja inicjuje blokadę skojarzoną z *blokadą parametru* do użycia w nadchodzących wywołaniach. Format jest następujący:

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

Stan początkowy jest odblokowany (oznacza to, że żaden wątek nie jest właścicielem blokady). W przypadku blokady zagnieżdżonej początkowa liczba zagnieżdżeń wynosi zero. Jest niezgodne, aby wywołać jedną z tych procedur ze zmienną blokady, która została już zainicjowana.

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a><a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a>3.2.2 Funkcje omp_destroy_lock i omp_destroy_nest_lock

Te funkcje upewnij się, że wskazał na blokadę zmiennej *blokady* jest niezainicjalnia. Format jest następujący:

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

Jest niezgodne, aby wywołać jedną z tych procedur ze zmienną blokady, która jest niezainicjowana lub odblokowana.

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a><a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a>3.2.3 funkcje omp_set_lock i omp_set_nest_lock

Każda z tych funkcji blokuje wątek wykonujący funkcję, dopóki nie będzie dostępna określona blokada, a następnie ustawia blokadę. Prosta blokada jest dostępna, jeśli jest odblokowana. Blokada zagnieżdżona jest dostępna, jeśli jest odblokowana lub jest już własnością wątku wykonującego funkcję. Format jest następujący:

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

W przypadku blokady prostej `omp_set_lock` argument funkcji musi wskazywać zainicjowaną zmienną blokady. Własność blokady jest przyznawana wątku wykonującego funkcję.

W przypadku blokady zagnieżdżonej argument funkcji `omp_set_nest_lock` musi wskazywać zainicjowaną zmienną blokady. Liczba zagnieżdżenia jest zwiększana, a wątek jest przyznawany lub zachowuje własność blokady.

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a><a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a>3.2.4 funkcje omp_unset_lock i omp_unset_nest_lock

Funkcje te zapewniają środki zwalniania własności blokady. Format jest następujący:

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

Argument do każdej z tych funkcji musi wskazywać na zainicjowaną zmienną blokady należącą do wątku wykonującego funkcję. Zachowanie jest niezdefiniowane, jeśli wątek nie jest właścicielem tej blokady.

W przypadku blokady `omp_unset_lock` prostej funkcja zwalnia wątek wykonujący funkcję z własności blokady.

W przypadku blokady `omp_unset_nest_lock` zagnieżdżonej funkcja zmniejsza liczbę zagnieżdżeń i zwalnia wątek wykonujący funkcję z własności blokady, jeśli wynikowa liczba wynosi zero.

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a><a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a>3.2.5 funkcje omp_test_lock i omp_test_nest_lock

Te funkcje próbują ustawić blokadę, ale nie blokują wykonywania wątku. Format jest następujący:

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

Argument musi wskazywać na zainicjowaną zmienną blokady. Te funkcje próbują ustawić blokadę `omp_set_lock` w `omp_set_nest_lock`taki sam sposób jak i , z tą różnicą, że nie blokują wykonywania wątku.

W przypadku blokady `omp_test_lock` prostej funkcja zwraca wartość niezerową, jeśli blokada została pomyślnie ustawiona; w przeciwnym razie zwraca zero.

W przypadku blokady `omp_test_nest_lock` zagnieżdżonej funkcja zwraca nową liczbę zagnieżdżeń, jeśli blokada zostanie pomyślnie ustawiona; w przeciwnym razie zwraca zero.

## <a name="33-timing-routines"></a>3.3 Procedury pomiaru czasu

Funkcje opisane w tej sekcji obsługują przenośny zegar ścienny:

- Funkcja [omp_get_wtime](#331-omp_get_wtime-function) zwraca czas zegara ściennego.
- Funkcja [omp_get_wtick](#332-omp_get_wtick-function) zwraca sekundy między kolejnymi znacznikami zegara.

### <a name="331-omp_get_wtime-function"></a><a name="331-omp_get_wtime-function"></a>3.3.1 funkcja omp_get_wtime

Funkcja `omp_get_wtime` zwraca podwójną precyzję wartość zmiennoprzecinku równa czasu zegara ściany, który upłynął w sekundach, ponieważ niektóre "czas w przeszłości".  Rzeczywisty "czas w przeszłości" jest dowolny, ale gwarantuje, że nie zmieni się podczas wykonywania programu aplikacji. Format jest następujący:

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

Przewiduje się, że funkcja będzie używana do pomiaru czasu, który upłynął, jak pokazano w poniższym przykładzie:

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Zwracane czasy są "razy na wątek", przez co oznacza, że nie są one wymagane do globalnie spójne we wszystkich wątków uczestniczących w aplikacji.

### <a name="332-omp_get_wtick-function"></a><a name="332-omp_get_wtick-function"></a>3.3.2 funkcja omp_get_wtick

Funkcja `omp_get_wtick` zwraca podwójną precyzję wartość zmiennoprzecinku równa liczbie sekund między kolejnymi znacznikami zegara. Format jest następujący:

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
