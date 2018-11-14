---
title: 1.2 Definicje terminów
ms.date: 11/04/2016
ms.assetid: fcaa8eb8-bbbf-4a24-ad0e-e299c442db79
ms.openlocfilehash: cd8bcc47a7fc9d1d0683c220ccd5ef1edac2b4e9
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326033"
---
# <a name="12-definition-of-terms"></a>1.2 Definicje terminów

W tym dokumencie są używane następujące terminy:

- ograniczenie

   Punkt synchronizacji, który musi być dostępny przez wszystkie wątki w zespole.  Każdy wątek czeka, aż wszystkie wątki w zespole pojawić się w tym momencie. Brak jawnych bariery identyfikowane za pomocą dyrektywy i niejawne bariery utworzone przez implementację.

- Konstrukcja

   Konstrukcja znajduje się zdanie. Składa się z dyrektywą i kolejne strukturalnego bloku. Należy pamiętać, że niektóre dyrektywy nie są częścią konstrukcji. (Zobacz *openmp — dyrektywa* w [dodatku C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)).

- — Dyrektywa

   C lub C++ **#pragma** następuje **omp** identyfikator, inny tekst i nowy wiersz. Dyrektywa określa zachowanie programu.

- zakres dynamiczny

   Wszystkie instrukcje w *zakresie leksykalnym*, a także każdej instrukcji wewnątrz funkcji, który jest wykonywany w wyniku wykonania instrukcji w zakresie leksykalnym. Zakres dynamiczny jest również nazywany *region*.

- zakres leksykalne

   Instrukcje leksykalnie zawartych w *strukturalnego bloku*.

- główny wątek

   Wątek, który utworzy zespół po *równoległego regionu* wprowadzeniu.

- równoległego regionu

   Instrukcje powiązać konstrukcja równoległa OpenMP, które mogą być wykonywane przez wiele wątków.

- private

   Prywatna zmienna nazwy bloku pamięci, który jest unikatowy w wątku, dzięki czemu odwołania. Należy pamiętać, że istnieje kilka sposobów, aby określić, czy zmienna jest prywatna: definicje w ramach równoległego regionu **threadprivate** dyrektywy, **prywatnej**, **firstprivate**, **lastprivate**, lub **redukcji** klauzulę lub użyj zmiennej jako **dla**zmienna sterująca pętli w **dla** pętli natychmiast po **dla** lub **równoległe w** dyrektywy.

- region

   Zakres dynamiczny.

- region szeregowej

   Instrukcje wykonywane tylko przez *głównym wątku* poza dynamiczny zakres dowolnego *równoległego regionu*.

- Serializacji

   Wykonywanie równoległe konstrukcji z zespołem wątków składający się z tylko jednego wątku (czyli głównego wątku dla tego konstrukcja równoległa), serial kolejności wykonywania instrukcji w bloku strukturalnego (taka sama kolejność tak, jakby nie były bloku część równoległe konstrukcji) i nie wpływa na wartość zwrócona przez obiekt **omp_in_parallel()** (oprócz efekty dowolnego zagnieżdżone konstrukcje równoległe).

- udostępnione

   Udostępnionej zmiennej nazwy jeden blok pamięci masowej. Wszystkie wątki w zespole, uzyskujących dostęp do tej zmiennej, będą miały dostęp tego jednego bloku pamięci.

- Blok strukturalny

   Blok strukturalny jest instrukcją (pojedyncze lub złożone) zawierający pojedynczy wpis i pojedynczego wyjścia. Oświadczenia jest blok strukturalny w przypadku skok do lub z którymi instrukcja (w tym wywołaniu **longjmp**(3 C) lub korzystanie z **throw**, ale wywołanie **wyjść** jest dozwolona). Instrukcja złożona jest strukturalnego bloku, jeśli jego zawsze zaczyna się od otwarcia **{** i zawsze kończy się zamykającym **}**. Instrukcja wyrażeń, wybór instrukcji, instrukcji iteracji lub **spróbuj** blok jest blok strukturalny uzyskane odpowiedniej instrukcji złożonej, umieszczając go w **{** i **}**  będzie strukturalnego bloku. Instrukcja skoku, instrukcja labeled lub instrukcji deklaracji nie jest strukturalnego bloku.

- Zespół

   Jeden lub więcej wątków, współpracujących podczas wykonywania konstrukcji.

- wątek

   Jednostki wykonywania mający serial przepływ sterowania, zestaw zmiennych prywatnych i dostęp do udostępnionego zmiennych.

- zmienna

   Identyfikator, opcjonalnie kwalifikowana przez nazwy przestrzeni nazw nazwy obiektu.
