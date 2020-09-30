---
title: Migrowanie z OpenMP do współbieżności środowiska wykonawczego
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
ms.openlocfilehash: 081d0ae8b312d827a0af98dd45c62f7563e81677
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507758"
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>Migrowanie z OpenMP do współbieżności środowiska wykonawczego

Środowisko uruchomieniowe współbieżności włącza różne modele programowania. Modele te mogą nakładać się lub uzupełniać modele innych bibliotek. Dokumenty w tej sekcji porównują [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp) z środowisko uruchomieniowe współbieżności i zawierają przykłady dotyczące sposobu migrowania istniejącego kodu OpenMP w celu korzystania z środowisko uruchomieniowe współbieżności.

Model programowania OpenMP jest definiowany przez otwarty standard i ma dobrze zdefiniowane powiązania z językami programowania Pascal i C/C++. Wersje OpenMP 2,0 i 2,5, które są obsługiwane przez kompilator języka Microsoft C++, są dobrze dostosowane do równoległych algorytmów, które są iteracyjne; oznacza to, że wykonują iterację równoległą w odniesieniu do tablicy danych. OpenMP 3,0 obsługuje zadania nieiteracyjne oprócz iteracyjnych zadań.

OpenMP jest najbardziej wydajny, gdy stopień równoległości jest wstępnie określony i jest zgodny z dostępnymi zasobami w systemie. Model OpenMP to szczególnie dobre dopasowanie w przypadku obliczeń o wysokiej wydajności, w przypadku których duże problemy obliczeniowe są dystrybuowane między zasobami przetwarzania jednego komputera. W tym scenariuszu środowisko sprzętowe jest ogólnie stałe i deweloper może oczekiwać, że ma wyłączny dostęp do wszystkich zasobów obliczeniowych, gdy algorytm jest wykonywany.

Jednak mniej ograniczone środowiska obliczeniowe mogą nie być dobrym odpowiednikiem OpenMP. Na przykład problemy cykliczne (takie jak algorytm sortowania lub wyszukiwanie drzewa danych) są trudniejsze do zaimplementowania przy użyciu OpenMP 2,0 i 2,5. Środowisko uruchomieniowe współbieżności uzupełnia możliwości technologii OpenMP przez udostępnienie [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) i [biblioteki równoległych wzorców](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). Biblioteka agentów asynchronicznych obsługuje bardziej precyzyjną równoległość zadań; PPL obsługuje bardziej szczegółowe zadania równoległe. Środowisko uruchomieniowe współbieżności zapewnia infrastrukturę, która jest wymagana do równoległego wykonywania operacji, aby można było skupić się na logice aplikacji. Ponieważ jednak środowisko uruchomieniowe współbieżności włącza różne modele programowania, jego obciążenie związane z planowaniem może być większe niż w przypadku innych bibliotek współbieżności, takich jak OpenMP. W związku z tym zaleca się przetestowanie wydajności przyrostowo podczas konwertowania istniejącego kodu OpenMP na korzystanie z środowisko uruchomieniowe współbieżności.

## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Kiedy należy przeprowadzić migrację z OpenMP do środowisko uruchomieniowe współbieżności

Może być korzystne przeprowadzenie migracji istniejącego kodu OpenMP, aby użyć środowisko uruchomieniowe współbieżności w następujących przypadkach.

|Padkach|Zalety środowisko uruchomieniowe współbieżności|
|-----------|-------------------------------------------|
|Wymagana jest rozszerzalna platforma programistyczna współbieżności.|Wiele funkcji w środowisko uruchomieniowe współbieżności można rozszerzyć. Możesz również połączyć istniejące funkcje, aby utworzyć nowe. Ponieważ OpenMP opiera się na dyrektywach kompilatora, nie można go łatwo rozszerzyć.|
|Twoja aplikacja może korzystać z blokowania w zakresie współpracy.|Gdy zadanie jest blokowane, ponieważ wymaga zasobu, który nie jest jeszcze dostępny, środowisko uruchomieniowe współbieżności mogą wykonywać inne zadania, podczas gdy pierwsze zadanie czeka na zasób.|
|Aplikacja będzie korzystać z dynamicznego równoważenia obciążenia.|Środowisko uruchomieniowe współbieżności używa algorytmu planowania, który dostosowuje przydział zasobów obliczeniowych w miarę zmiany obciążeń. W środowisku OpenMP, gdy harmonogram przydziela zasoby obliczeniowe do regionu równoległego, te alokacje zasobów są rozwiązane w całym obliczeniu.|
|Wymagana jest obsługa wyjątków.|PPL umożliwia przechwytywanie wyjątków zarówno wewnątrz, jak i poza równoległym regionem lub pętlą. W OpenMP należy obsłużyć wyjątek wewnątrz równoległego regionu lub pętli.|
|Wymagany jest mechanizm anulowania.|PPL umożliwia aplikacjom anulowanie poszczególnych zadań i równoległych drzew pracy. OpenMP wymaga, aby aplikacja mogła zaimplementować swój własny mechanizm anulowania.|
|Wymagany jest kod równoległy, aby zakończyć w innym kontekście, z którego został uruchomiony.|Środowisko uruchomieniowe współbieżności pozwala uruchomić zadanie w jednym kontekście, a następnie zaczekać lub anulować to zadanie w innym kontekście. W OpenMP wszystkie prace równoległe muszą zakończyć się w kontekście, z którego się zaczyna.|
|Wymagana jest ulepszona obsługa debugowania.|Program Visual Studio udostępnia **stosy równoległe** i okna **zadań równoległych** , dzięki czemu można łatwiej debugować aplikacje wielowątkowe.<br /><br /> Aby uzyskać więcej informacji na temat obsługi debugowania dla środowisko uruchomieniowe współbieżności, zobacz [Korzystanie z okna zadania](/visualstudio/debugger/using-the-tasks-window), [Korzystanie z okna stosów równoległych](/visualstudio/debugger/using-the-parallel-stacks-window)i [Przewodnik: debugowanie aplikacji równoległej](/visualstudio/debugger/walkthrough-debugging-a-parallel-application).|

## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Gdy nie należy migrować z OpenMP do środowisko uruchomieniowe współbieżności

Poniższe przypadki opisują, kiedy może nie być konieczne Migrowanie istniejącego kodu OpenMP w celu użycia środowisko uruchomieniowe współbieżności.

|Padkach|Objaśnienie|
|-----------|-----------------|
|Twoja aplikacja spełnia już Twoje wymagania.|Jeśli spełniasz wymagania dotyczące wydajności aplikacji i bieżącej obsługi debugowania, migracja może nie być odpowiednia.|
|Ciała pętli równoległej wykonują niewiele pracy.|Narzuty harmonogramu zadań środowisko uruchomieniowe współbieżności mogą nie przezwyciężyć korzyści płynących z wykonywania pętli cyklicznej, szczególnie gdy treść pętli jest stosunkowo mała.|
|Aplikacja jest zapisywana w C.|Ponieważ środowisko uruchomieniowe współbieżności używa wielu funkcji języka C++, może to nie być odpowiednie, gdy nie można napisać kodu, który umożliwia aplikacji C pełne korzystanie z niej.|

## <a name="related-topics"></a>Tematy pokrewne

[Instrukcje: konwertowanie pętli równoległej OpenMP na używanie środowisko uruchomieniowe współbieżności](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)

Porada podstawowa pętla, która używa algorytmu OpenMP [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) and [for](../openmp/reference/openmp-directives.md#for-openmp) , pokazuje, jak przekonwertować go na środowisko uruchomieniowe współbieżności algorytm [współbieżności::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) .

[Instrukcje: konwertowanie pętli OpenMP używającej anulowania do używania środowisko uruchomieniowe współbieżności](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)<br/>
W przypadku pętli "OpenMP [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) ", która nie wymaga wszystkich iteracji do uruchomienia, pokazuje, jak przekonwertować ją w celu użycia mechanizmu anulowania środowisko uruchomieniowe współbieżności.

[Instrukcje: konwertowanie pętli OpenMP używającej obsługi wyjątków do korzystania z środowisko uruchomieniowe współbieżności](../../parallel/concrt/convert-an-openmp-loop-that-uses-exception-handling.md)<br/>
W przypadku pętli "OpenMP [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) ", która wykonuje obsługę wyjątków, pokazuje, jak przekonwertować ją w celu użycia mechanizmu obsługi wyjątków środowisko uruchomieniowe współbieżności.

[Instrukcje: konwertowanie pętli OpenMP używającej zmiennej redukcji do korzystania z środowisko uruchomieniowe współbieżności](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)<br/>
W przypadku pętli "OpenMP [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) " wykorzystującej klauzulę [redukcji](../openmp/reference/openmp-clauses.md#reduction) pokazano, jak przekonwertować ją w celu użycia środowisko uruchomieniowe współbieżności.

## <a name="see-also"></a>Zobacz też

[Współbieżność środowiska wykonawczego](../../parallel/concrt/concurrency-runtime.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)<br/>
[Biblioteka równoległych wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)
