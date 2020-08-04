---
title: 1. Wprowadzenie
ms.date: 01/16/2019
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
ms.openlocfilehash: e2857565f7838ae45ff88ea53ba714e1418116ff
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2020
ms.locfileid: "87521177"
---
# <a name="1-introduction"></a>1. Wprowadzenie

Ten dokument określa kolekcję dyrektyw kompilatora, funkcji biblioteki i zmiennych środowiskowych, których można użyć do określenia równoległości pamięci współdzielonej w programach C i C++. Funkcje opisane w tym dokumencie są zbiorczo nazywane *interfejsem programu aplikacji OpenMP C/C++*. Celem tej specyfikacji jest zapewnienie modelu programowania równoległego, który umożliwia przenośny program w ramach architektury pamięci współdzielonej od różnych dostawców. Kompilatory od wielu dostawców obsługują interfejs API OpenMP C/C++. Więcej informacji na temat OpenMP, w tym *interfejsu programu aplikacji OpenMP Pascal*, można znaleźć w następującej witrynie sieci Web:

[https://www.openmp.org](https://www.openmp.org)

Dyrektywy, funkcje biblioteki i zmienne środowiskowe zdefiniowane w tym dokumencie umożliwiają tworzenie równoległych programów i zarządzanie nimi, umożliwiając przenośność. Dyrektywy rozszerzającą model programowania sekwencyjnego C i C++ za pomocą jednego programu, konstrukcji wielu danych (SPMD), konstrukcji udostępniania pracy i konstrukcji synchronizacji. Obsługują one także udostępnianie i prywatyzacji danych. Kompilatory obsługujące interfejs API OpenMP i C++ zawierają opcję wiersza polecenia do kompilatora, który aktywuje i umożliwia interpretację wszystkich dyrektyw kompilatora OpenMP.

## <a name="11-scope"></a>1.1 Zakres

Ta specyfikacja obejmuje tylko przetwarzanie równoległe ukierunkowane na użytkownika, w którym można jawnie definiować akcje wykonywane przez kompilator i system czasu wykonywania programu równolegle. Implementacje OpenMP C i C++ nie są wymagane, aby sprawdzać zależności, konflikty, zakleszczenia, sytuacje wyścigu lub inne problemy powodujące nieprawidłowe wykonywanie programu. Użytkownik jest odpowiedzialny za zapewnienie, że aplikacja używająca interfejsów API OpenMP i C++ działa prawidłowo. Automatyczne wygenerowane przez kompilator przetwarzanie równoległe i dyrektywy do kompilatora, aby pomóc temu przetwarzanie równoległe nie zostały omówione w tym dokumencie.

## <a name="12-definition-of-terms"></a>1,2 Definicja warunków

W tym dokumencie są używane następujące terminy:

- ograniczenie

  Punkt synchronizacji, do którego muszą dotrzeć wszystkie wątki w zespole.  Każdy wątek czeka, aż wszystkie wątki w zespole dotarły do tego momentu. Istnieją jawne bariery identyfikowane przez dyrektywy i niejawne przeszkody utworzone przez implementację.

- Konstruuj

  Konstrukcja jest instrukcją. Składa się z dyrektywy, a po niej blok strukturalny. Niektóre dyrektywy nie są częścią konstrukcji. (Patrz *dyrektywa OpenMP* w [dodatku C](c-openmp-c-and-cpp-grammar.md)).

- dyrektywę

  Kod C lub C++ `#pragma` , po którym następuje `omp` Identyfikator, inny tekst i nowy wiersz. Dyrektywa określa zachowanie programu.

- zakres dynamiczny

  Wszystkie instrukcje w *zakresie leksykalnym*oraz jakakolwiek instrukcja wewnątrz funkcji, która jest wykonywana w wyniku wykonywania instrukcji w zakresie leksykalnym. Dynamiczny zakres jest również nazywany *regionem*.

- zakres leksykalny

  Instrukcje leksykalne w obrębie *bloku strukturalnego*.

- wątek główny

  Wątek, który tworzy zespół, gdy zostanie wprowadzony *region równoległy* .

- Region równoległy

  Instrukcje, które wiążą się z równoległą konstrukcją OpenMP i mogą być wykonywane przez wiele wątków.

- private

  Zmienna prywatna nazywa blok magazynu, który jest unikatowy dla wątku tworzącego odwołanie. Istnieje kilka sposobów, aby określić, że zmienna jest prywatna: Definicja w ramach równoległego regionu, `threadprivate` dyrektywy,, `private` lub, lub `firstprivate` `lastprivate` `reduction` użycie zmiennej jako **`for`** zmiennej sterującej pętli **`for`** bezpośrednio po `for` `parallel for` dyrektywie lub.

- region

  Dynamiczny zakres.

- Region szeregowy

  Instrukcje wykonywane tylko przez *wątek główny* poza dynamicznym zakresem dowolnego *równoległego regionu*.

- potrzeby

  Aby wykonać konstrukcję równoległą przy użyciu:

  - Zespół wątków składający się z tylko jednego wątku (który jest głównym wątkiem dla tej konstrukcji równoległej),

  - kolejność szeregowa wykonywania dla instrukcji w bloku strukturalnym (taka sama kolejność jak w przypadku, gdy blok nie był częścią konstrukcji równoległej), i

  - nie wpływa na wartość zwracaną przez `omp_in_parallel()` (oprócz efektów zagnieżdżonych konstrukcji równoległych).

- udostępnione

  Zmienna współdzielona nazywa pojedynczym blokiem magazynu. Wszystkie wątki w zespole, które uzyskują dostęp do tej zmiennej, również uzyskują dostęp do tego pojedynczego bloku magazynu.

- blok strukturalny

  Blok strukturalny jest instrukcją (pojedynczą lub złożoną), która ma pojedynczy wpis i pojedyncze wyjście. W przypadku przechodzenia do lub z instrukcji, ta instrukcja jest blokiem strukturalnym. (Ta reguła zawiera wywołanie do `longjmp` (3C) lub użycie `throw` , chociaż wywołanie `exit` jest dozwolone.) Jeśli jego wykonanie zawsze rozpoczyna się na otwarciu `{` i zawsze kończą się przy zamykaniu `}` , instrukcja złożona jest blokiem strukturalnym. Instrukcja Expression, instrukcja SELECT, instrukcja iteracji lub **`try`** blok to blok strukturalny, Jeśli odpowiednia złożona instrukcja uzyskana przez zawrzeć ją w `{` i będzie `}` blokiem strukturalnym. Instrukcja skoku, instrukcja oznaczona etykietą lub instrukcja deklaracji nie jest blokiem strukturalnym.

- zespół

  Co najmniej jeden wątek współdziała podczas wykonywania konstrukcji.

- wątek

  Jednostka wykonywania ma przepływ szeregowy sterowania, zestaw zmiennych prywatnych i dostęp do zmiennych udostępnionych.

- zmienna

  Identyfikator, opcjonalnie kwalifikowana nazwami przestrzeni nazw, która nazywa obiekt.

## <a name="13-execution-model"></a>model wykonywania 1,3

OpenMP używa modelu przyłączania do rozwidlenia. Chociaż ten model łączenia rozwidlenia może być przydatny do rozwiązywania różnych problemów, jest dostosowany do dużych aplikacji opartych na tablicy. OpenMP jest przeznaczony do obsługi programów, które działają poprawnie zarówno jako programy równoległe (wiele wątków wykonywania, jak i pełną bibliotekę obsługi OpenMP). Jest on również przeznaczony dla programów, które są wykonywane prawidłowo jako programy sekwencyjne (dyrektywy ignorowane i prosta biblioteka pociągania OpenMP). Jednak jest możliwe, że opracowuje program, który nie działa prawidłowo w przypadku wykonywania sekwencyjnie. Ponadto różne stopnie równoległości mogą powodować różne wyniki liczbowe ze względu na zmiany skojarzenia operacji numerycznych. Na przykład redukcja numeru seryjnego może mieć inny wzorzec dla skojarzeń dodatkowych niż w przypadku obniżenia wartości równoległej. Te różne skojarzenia mogą zmieniać wyniki dodawania zmiennoprzecinkowego.

Program zapisany przy użyciu interfejsu API OpenMP/C++ rozpoczyna wykonywanie jako pojedynczy wątek wykonywania nazywany *wątkiem głównym*. Wątek główny jest wykonywany w regionie szeregowym do momentu napotkania pierwszej równoległej konstrukcji. W interfejsie API OpenMP C/C++ `parallel` dyrektywa stanowi konstrukcję równoległą. Gdy napotkana jest konstrukcja równoległa, wątek główny tworzy zespół wątków, a główny stał się wzorcem zespołu. Każdy wątek w zespole wykonuje instrukcje w dynamicznym zakresie regionu równoległego, z wyjątkiem konstrukcji udostępniania pracy. Wszystkie wątki w zespole muszą napotkać konstrukcje podziału pracy w tej samej kolejności, a co najmniej jeden z wątków wykonuje instrukcje w ramach skojarzonego bloku strukturalnego. Bariera implikowana na końcu konstrukcji udostępniania pracy bez `nowait` klauzuli jest wykonywana przez wszystkie wątki w zespole.

Jeśli wątek modyfikuje obiekt współużytkowany, dotyczy nie tylko własnego środowiska wykonawczego, ale również do innych wątków w programie. Zmiana zostanie zagwarantowana, z punktu widzenia innego wątku, w następnym punkcie sekwencji (zgodnie z definicją w języku podstawowym) tylko wtedy, gdy obiekt jest zadeklarowany jako nietrwały. W przeciwnym razie modyfikacja zostanie zagwarantowana po pierwszym wątku modyfikowania. Pozostałe wątki następnie (lub współbieżnie) widzą `flush` dyrektywy, która określa obiekt (niejawnie lub jawnie). Gdy `flush` dyrektywy, które są implikowane przez inne dyrektywy OpenMP, nie gwarantują prawidłowej kolejności efektów ubocznych, to programista jest odpowiedzialny za dostarczanie dodatkowych, jawnych `flush` dyrektyw.

Po zakończeniu konstruowania równoległego wątki w zespole są synchronizowane z niejawną barierą i tylko wątek główny kontynuuje wykonywanie. Dowolna liczba równoległych konstrukcji może być określona w pojedynczym programie. W efekcie program może rozwidlenia i sprzęgać wiele razy podczas wykonywania.

Interfejs API OpenMP C/C++ umożliwia programistom używanie dyrektyw w funkcjach wywoływanych z wewnątrz konstrukcji równoległych. Dyrektywy, które nie pojawiają się w zakresie leksykalnym konstrukcji równoległej, ale mogą znajdować się w zakresie dynamicznym są nazywane dyrektywami *oddzielonymi* . W przypadku dyrektyw oddzielonych programiści mogą wykonywać w sposób równoległy główne części programu, z uwzględnieniem tylko minimalnych zmian w programie sekwencyjnym. Korzystając z tej funkcji, można kodu konstrukcje równoległe na najwyższym poziomie drzewa wywołań programu i stosować dyrektywy do sterowania wykonywaniem w którejkolwiek z wywołanych funkcji.

Niezsynchronizowane wywołania funkcji wyjściowych C i C++, które zapisują w tym samym pliku, mogą spowodować wyjście, w którym dane zapisane przez różne wątki pojawiają się w kolejności niedeterministycznej. Podobnie niezsynchronizowane wywołania funkcji wejściowych odczytywanych z tego samego pliku mogą odczytywać dane w kolejności niedeterministycznej. Niezsynchronizowane użycie operacji we/wy, w taki sposób, że każdy wątek uzyskuje dostęp do innego pliku, daje takie same wyniki jak wykonywanie szeregu funkcji we/wy.

## <a name="14-compliance"></a>1.4 Zgodność

Implementacja interfejsu API OpenMP C/C++ jest *zgodna ze standardem OpenMP* , jeśli rozpoznaje i zachowuje semantykę wszystkich elementów tej specyfikacji, jak określono w rozdziale 1, 2, 3, 4 i dodatek C. Dodatki a, B, D, E i F są wyłącznie do celów informacyjnych i nie są częścią specyfikacji. Implementacje, które zawierają tylko podzestaw interfejsu API, nie są zgodne ze standardem OpenMP.

Interfejs API OpenMP C i C++ jest rozszerzeniem języka podstawowego, który jest obsługiwany przez implementację. Jeśli język podstawowy nie obsługuje konstrukcji językowej lub rozszerzenia, które pojawia się w tym dokumencie, implementacja OpenMP nie jest wymagana do jej obsługi.

Wszystkie standardowe funkcje biblioteki C i C++ oraz wbudowane funkcje (czyli funkcje, które kompilator ma określoną wiedzę) muszą być bezpieczne wątkowo. Niezsynchronizowane użycie funkcji bezpiecznych dla wątków przez różne wątki w regionie równoległym nie powoduje utworzenia niezdefiniowanego zachowania. Zachowanie może jednak nie być takie samo jak w przypadku regionu szeregowego. (Przykładowa funkcja generowania liczb losowych).

Interfejs API OpenMP C/C++ określa, że określone zachowanie jest *zdefiniowane w implementacji.* Zgodność z implementacją OpenMP jest wymagana do zdefiniowania i udokumentowania zachowania w takich przypadkach. Aby zapoznać się z listą zachowań zdefiniowanych w implementacji, zobacz [dodatek E](e-implementation-defined-behaviors-in-openmp-c-cpp.md).

## <a name="15-normative-references"></a>1,5 Odwołania normatywne

- ISO/IEC 9899:1999, *technologia informacyjna — Języki programowania-C*. Ta specyfikacja interfejsu API OpenMP odnosi się do ISO/IEC 9899:1999 jako C99.

- ISO/IEC 9899:1990, *technologia informacyjna — Języki programowania-C*. Ta specyfikacja interfejsu API OpenMP odnosi się do ISO/IEC 9899:1990 jako C90.

- ISO/IEC 14882:1998, *technologia informacyjna — Języki programowania — C++*. Ta specyfikacja interfejsu API OpenMP odnosi się do ISO/IEC 14882:1998 jako C++.

Jeśli ta Specyfikacja interfejsu API OpenMP odwołuje się do języka C, odwołanie jest tworzone do podstawowego w języku obsługiwanym przez implementację.

## <a name="16-organization"></a>1.6 Organizacja

- [Funkcje bibliotek środowiska uruchomieniowego](3-run-time-library-functions.md)
- [Zmienne środowiskowe](4-environment-variables.md)
- [Zachowania zdefiniowane w implementacji w programie OpenMP C/C++](e-implementation-defined-behaviors-in-openmp-c-cpp.md)
- [Nowe funkcje w programie OpenMP C/C++ w wersji 2,0](f-new-features-and-clarifications-in-version-2-0.md)
