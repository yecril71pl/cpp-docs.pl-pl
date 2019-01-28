---
title: 1. Wprowadzenie
ms.date: 01/16/2019
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
ms.openlocfilehash: 8c735408bdf9f9a13693bd0ad25df185bb1db42a
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087278"
---
# <a name="1-introduction"></a>1. Wprowadzenie

W tym dokumencie określa zbiór dyrektywy kompilatora, funkcje i zmienne środowiskowe, używanych do określania równoległości pamięci współużytkowanej w ramach programów C i C++. Funkcje opisane w niniejszym dokumencie jest nazywane zbiorczo *interfejsu programu aplikacji (API) OpenMP C/C++*. Celem tej specyfikacji jest zapewnienie modelu programowania równoległego umożliwia program będzie działał w ramach architektury pamięci współużytkowanej pochodzących od różnych dostawców. Kompilatory od wielu dostawców obsługuje OpenMP API języka C/C++. Więcej informacji na temat OpenMP, w tym *interfejs aplikacji OpenMP Fortran*, można znaleźć w następującej witrynie sieci web:

[https://www.openmp.org](https://www.openmp.org)

Dyrektywy, funkcje i zmienne środowiskowe zdefiniowane w tym dokumencie umożliwiają tworzenie i zarządzanie nimi programów do równoległego przetwarzania, a jednocześnie przenośność. Dyrektywy rozszerzenie C i C++ sekwencyjnego modelu programowania za pomocą jednego programu, który tworzy wiele danych (zawiera system SPMD), konstrukcje podziału pracy i konstrukcje synchronizacji. Obsługują one również udostępnianie i prywatyzacji danych. Kompilatory, które obsługują OpenMP C i C++ API obejmują opcji wiersza polecenia kompilatora, który aktywuje i umożliwia interpretacji wszystkich OpenMP, dyrektywy kompilatora.

## <a name="11-scope"></a>1.1 Zakres

Ta specyfikacja obejmuje tylko użytkownik skierowany przetwarzania równoległego, którym jawne zdefiniowanie działania, jakie kompilatora i środowiska wykonawczego systemu Rozwijaj równolegle uruchomić program. Implementacje OpenMP C i C++ nie są wymagane do wyszukania zależności, konfliktów, zakleszczenia, wyścigu lub innych problemów, które powoduje wykonanie programu niepoprawne. Ponosisz odpowiedzialność za zapewnienie poprawnie wykonuje aplikacji przy użyciu konstrukcje OpenMP C i C++ interfejsu API. Generowane przez kompilator automatyczne przetwarzanie równoległe i dyrektywy kompilatora ułatwiają przetwarzania równoległego na takie nie są objęte pomocą techniczną w tym dokumencie.

## <a name="12-definition-of-terms"></a>1.2 definicje terminów

W tym dokumencie są używane następujące terminy:

- ograniczenie

  Punkt synchronizacji, które muszą być dostarczone przez wszystkie wątki w zespole.  Każdy wątek czeka, aż wszystkie wątki w zespole pojawić się w tym momencie. Brak jawnych bariery identyfikowane za pomocą dyrektywy i niejawne bariery utworzone przez implementację.

- Konstrukcja

  Konstrukcja znajduje się zdanie. Składa się z dyrektywą, następuje strukturalnego bloku. Niektóre dyrektywy nie są częścią konstrukcji. (Zobacz *openmp — dyrektywa* w [dodatek C](c-openmp-c-and-cpp-grammar.md)).

- — Dyrektywa

  C lub C++ `#pragma` następuje `omp` identyfikator, inny tekst i nowy wiersz. Dyrektywa określa zachowanie programu.

- zakres dynamiczny

  Wszystkie instrukcje w *zakresie leksykalnym*, a także każdej instrukcji wewnątrz funkcji, który jest wykonywany w wyniku wykonania instrukcji w zakresie leksykalnym. Zakres dynamiczny jest również nazywany *region*.

- zakres leksykalne

  Instrukcje leksykalnie przechowywanych w ramach *strukturalnego bloku*.

- główny wątek

  Wątek, który utworzy zespół po *równoległego regionu* wprowadzeniu.

- równoległego regionu

  Instrukcje powiązać konstrukcja równoległa OpenMP, które mogą być wykonywane przez wiele wątków.

- private

  Prywatna zmienna nazwy bloku pamięci, który jest unikatowy w wątku, dzięki czemu odwołania. Istnieje kilka sposobów, aby określić, czy zmienna jest prywatna: definicje w ramach równoległego regionu `threadprivate` dyrektywy, `private`, `firstprivate`, `lastprivate`, lub `reduction` klauzulę lub użyj zmiennej jako `for`pętli Zmienna sterująca w `for` pętli, natychmiast po `for` lub `parallel for` dyrektywy.

- region

  Zakres dynamiczny.

- region szeregowej

  Instrukcje wykonywane tylko przez *głównym wątku* poza dynamiczny zakres dowolnego *równoległego regionu*.

- Serializacji

  Wykonywanie równoległe konstrukcji za pomocą:

  - zespół wątków składający się z tylko jednego wątku (czyli głównego wątku dla tego konstrukcja równoległa),

  - Serial kolejność wykonywania instrukcji w bloku strukturalne (takie same kolejność tak, jakby bloku nie były częścią konstrukcja równoległa), a

  - nie wpływa na wartość zwrócona przez obiekt `omp_in_parallel()` (oprócz efekty dowolnego zagnieżdżone konstrukcje równoległe).

- udostępnione

  Udostępnionej zmiennej nazwy jeden blok pamięci masowej. Wszystkie wątki w zespole, uzyskujących dostęp do tej zmiennej również dostęp do tego jednego bloku pamięci.

- Blok strukturalny

  Blok strukturalny jest instrukcją (pojedyncze lub złożone) zawierający pojedynczy wpis i pojedynczego wyjścia. W przypadku skok do lub z instrukcji tej instrukcji jest strukturalnego bloku. (Ta reguła zawiera wywołanie `longjmp`(3C) lub użycia `throw`, mimo że wywołanie `exit` jest dozwolona.) Jeśli jej wykonanie zawsze zaczyna się od otwarcia `{` i zawsze kończy się zamykającym `}`, instrukcję złożonego jest strukturalnego bloku. Instrukcja wyrażeń, wybór instrukcji, instrukcji iteracji lub `try` blok jest blok strukturalny uzyskane odpowiedniej instrukcji złożonej, umieszczając go w `{` i `}` będzie strukturalnego bloku. Nie ma strukturalnego bloku, instrukcja skoku, instrukcja labeled lub instrukcji deklaracji.

- Zespół

  Jeden lub więcej wątków, współpracujących podczas wykonywania konstrukcji.

- wątek

  Jednostki wykonywania mający serial przepływ sterowania, zestaw zmiennych prywatnych i dostęp do udostępnionego zmiennych.

- zmienna

  Identyfikator, opcjonalnie kwalifikowana przez nazwy przestrzeni nazw nazwy obiektu.

## <a name="13-execution-model"></a>1.3 model wykonania

OpenMP używa modelu przyłączaniem do rozwidlenia wykonywanie równoległe. Mimo że ten model rozwidlenia sprzężenia mogą być przydatne w przypadku rozwiązywania różnych problemów, jest to przeznaczony dla dużych aplikacji opartych na tablicy. OpenMP jest przeznaczona do obsługi programów, które są wykonywane prawidłowo, zarówno jako programów do równoległego przetwarzania (biblioteki obsługi wielu wątków i wykonywanie pełnej OpenMP). Jest również dla programów, które są wykonywane prawidłowo jako kolejne programy (dyrektywy ignorowane i proste biblioteki klas zastępczych OpenMP). Jednak jest możliwe i możliwość tworzenia program, który nie działają prawidłowo, gdy są wykonywane sekwencyjnie. Ponadto różny stopień równoległości może spowodować różnych wyników liczbowych ze względu na zmiany w skojarzeniu operacji numerycznych. Na przykład zmniejszenie o dodanie serial mogą mieć różnych wzorców skojarzenia dodanie niż równoległych redukcji. Te różne skojarzenia mogą ulec zmianie wyniki dodawania zmiennoprzecinkowych.

Program napisany za pomocą interfejsu API języka C/C++ OpenMP rozpoczyna wykonywanie jako pojedynczy wątek wykonywania o nazwie *głównym wątku*. Główny wątek wykonuje w regionie serial, dopóki nie zostanie osiągnięty pierwszy konstrukcja równoległa. W interfejsie API języka C/C++ OpenMP `parallel` dyrektywa stanowi konstrukcja równoległa. Po napotkaniu konstrukcja równoległa głównego wątku utworzy zespół wątków, i wzorcem staje się głównej zespołu. Każdy wątek w zespół wykonuje instrukcje dynamiczne zakresu równoległego regionu, z wyjątkiem konstrukcje podziału pracy. Wszystkie wątki w zespole musi wystąpić konstrukcje podziału pracy w tej samej kolejności i co najmniej jeden z wątków, wykonuje instrukcje w ramach skojarzone ze strukturalnego bloku. Możesz też dorozumianych na końcu konstrukcji podziału pracy, bez `nowait` klauzula jest wykonywana przez wszystkie wątki w zespole.

Jeśli wątek modyfikuje obiektów udostępnionych, dotyczy nie tylko własnego środowiska wykonawczego, a także porównanie tych innych wątków w programie. Modyfikacja jest gwarantowane jest pełny, z punktu widzenia inny wątek w następnym punkcie sekwencji (zgodnie z definicją w języku podstawowej), tylko wtedy, gdy obiekt został zadeklarowany jako volatile. W przeciwnym razie zmiany może być kompletny po pierwszych modyfikowanie wątku. Zobacz inne wątki, a następnie (lub jednocześnie) `flush` dyrektywę, który określa obiekt (jawnie lub niejawenie). Gdy `flush` dyrektyw, które są też dorozumianych przez inne dyrektywy OpenMP nie gwarantuje poprawną porządkowanie efekty uboczne, odpowiada za programisty podać dodatkowe, jawna `flush` dyrektywy.

Po zakończeniu konstrukcja równoległa w niejawne barierę synchronizować wątków w zespole, a tylko główny wątek kontynuuje wykonywanie. W jednym programie można określić dowolną liczbę równoległych konstrukcji. Co w efekcie program może rozwidlenie i połączyć wiele razy w czasie wykonywania.

OpenMP C/C++ API umożliwia programistom użyć dyrektyw w funkcje wywołane z wnętrza równoległe konstrukcje. Dyrektyw, które nie pojawiają się w zakresie leksykalnym konstrukcja równoległa, ale może znajdować się w zakresie dynamicznych są nazywane *oddzielone* dyrektywy. Za pomocą dyrektywy oddzielone równolegle z tylko minimalne zmiany dotyczące sekwencyjny program programistów można uruchomić główne części programu. Dzięki tej funkcji można kodu równoległe konstrukcje w górnym poziomy drzewa wywołań programu i użyj dyrektywy, aby kontrolować wykonywanie we wszystkich wywoływanych funkcji.

Funkcje, które zapisu do tego samego pliku może spowodować w danych wyjściowych, w którym dane zapisane przez inne wątki pojawia się w kolejności niedeterministyczne danych wyjściowych niezsynchronizowane wywołania do C i C++. Podobnie niezsynchronizowane wywołania do funkcji, które odczytują z tego samego pliku wejściowego może odczytać dane w kolejności jednoznaczne wyniki. Niezsynchronizowane użycia operacji We/Wy, tak, aby każdy wątek uzyskuje dostęp do innego pliku, jest taki sam jak wykonanie szeregowe funkcji we/wy.

## <a name="14-compliance"></a>1.4 Zgodność

Implementacja OpenMP API języka C/C++ jest *CLS OpenMP* jeśli ją rozpoznaje i zachowuje semantykę wszystkie elementy tej specyfikacji, tak jak w rozdziałach 1, 2, 3, 4, i związanych z dodatek C. dodatki A, B, D, E i f. informacje o wyłącznie do celów i nie są częścią specyfikacji. Implementacji, które zawierają tylko podzestaw interfejsu API nie są zgodne z OpenMP.

OpenMP C i C++ interfejsu API jest rozszerzeniem języka podstawowego, która jest obsługiwana przez implementację. Jeśli język podstawowy nie obsługuje konstrukcją języka pierwszej klasy lub rozszerzenie, które pojawia się w tym dokumencie, implementacja OpenMP nie jest wymagane do jego obsługi.

Wszystkie standardowe funkcje biblioteki C i C++ i funkcji wbudowanych (oznacza to, że funkcje których kompilator zna określonych) musi być metodą o bezpiecznych wątkach. Niezsynchronizowane korzystania z funkcji metodą o bezpiecznych wątkach, przez inne wątki w ramach równoległego regionu nie generuje niezdefiniowane zachowanie. Jednak to zachowanie nie może być taki sam jak region szeregowe. (Funkcja generowania liczb losowych jest przykładem).

OpenMP C/C++ API Określa, że określone zachowanie jest *zdefiniowanych w implementacji.* Odpowiadające implementacja OpenMP jest wymagany do definiowania i zarządzania dokumentami jego zachowanie w takich przypadkach. Aby uzyskać listę zachowania zdefiniowane w implementacji, zobacz [dodatku E](e-implementation-defined-behaviors-in-openmp-c-cpp.md).

## <a name="15-normative-references"></a>1.5 odwołania normatywne

- 9899:1999 ISO/IEC *informacji o technologii — języki programowania - C*. Tej specyfikacji OpenMP API odwołuje się do 9899:1999 ISO/IEC jako C99.

- 9899:1990 ISO/IEC *informacji o technologii — języki programowania - C*. Tej specyfikacji OpenMP API odwołuje się do 9899:1990 ISO/IEC jako C90.

- 14882:1998 ISO/IEC *informacji o technologii — języki programowania - C++*. Tej specyfikacji OpenMP API odwołuje się do 14882:1998 ISO/IEC co kod C++.

W przypadku, gdy tej specyfikacji OpenMP API odwołuje się do języka C, odniesienia do języka podstawowego, jest obsługiwana przez implementację.

## <a name="16-organization"></a>1.6 Organizacja

- [Funkcje biblioteki czasu wykonywania](3-run-time-library-functions.md)
- [Zmienne środowiskowe](4-environment-variables.md)
- [Zachowania zdefiniowane w implementacji programie OpenMP C/C++](e-implementation-defined-behaviors-in-openmp-c-cpp.md)
- [Nowe funkcje w programie OpenMP C/C++ w wersji 2.0](f-new-features-and-clarifications-in-version-2-0.md)
