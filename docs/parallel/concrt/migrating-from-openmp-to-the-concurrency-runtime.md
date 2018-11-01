---
title: Migrowanie z OpenMP do współbieżności środowiska wykonawczego
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
ms.openlocfilehash: 4b70aa57a6485fefe0dbb678e72ba127502c89e3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481929"
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>Migrowanie z OpenMP do współbieżności środowiska wykonawczego

Środowisko uruchomieniowe współbieżności umożliwia różne modele programowania. Te modele mogą nakładać się na lub uzupełniają modele innych bibliotek. Dokumenty w tej sekcji porównania [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp) do współbieżności środowiska wykonawczego i zawierają przykłady dotyczące migracji istniejącego kodu OpenMP do współbieżności środowiska wykonawczego.

Model programowania OpenMP jest definiowany przez otwarty standard i dobrze zdefiniowanych powiązań dla języków programowania Fortran i języka C/C++. OpenMP w wersji 2.0 i 2.5, które są obsługiwane przez kompilator języka Visual C++, są one odpowiednie dla algorytmów równoległych, które są iteracyjne; oznacza to ich wykonywanie równoległe iteracji przez tablicę danych. OpenMP 3.0 obsługuje-iteracyjne zadania i zadania iteracyjne.

OpenMP jest najbardziej efektywne, gdy stopień równoległości jest wstępnie określane i dopasowuje dostępnych zasobów w systemie. OpenMP model jest szczególnie dobre dopasowanie do obliczeń o wysokiej wydajności, bardzo duże rozwiązywania problemów obliczeniowych są dystrybuowane między przetwarzania zasobów z jednego komputera. W tym scenariuszu środowisko sprzętu zazwyczaj jest stała i deweloper może spodziewać ma wyłącznego dostępu do wszystkich zasobów obliczeniowych, podczas wykonywania algorytmu.

Jednak mniej ograniczone środowiska obliczeniowe może nie być dobre dopasowanie dla OpenMP. Na przykład rekursywny problemy (np. algorytm szybkiego sortowania lub wyszukiwania drzewo danych) są trudniejsze do zaimplementowania za pomocą OpenMP 2.0 i 2.5. Środowisko uruchomieniowe współbieżności uzupełnia możliwości OpenMP, zapewniając [bibliotekę asynchronicznych agentów](../../parallel/concrt/asynchronous-agents-library.md) i [biblioteki wzorców równoległych](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). Bibliotekę asynchronicznych agentów obsługuje równoległości gruboziarnistych zadań; PPL obsługuje więcej szczegółowych zadań równoległych. Środowisko uruchomieniowe współbieżności stanowi infrastrukturę, która jest wymagana do wykonywania operacji w sposób równoległy, dzięki czemu możesz skupić się na logice aplikacji. Jednak ponieważ środowisko uruchomieniowe współbieżności umożliwia różne modele programowania, jego planowaniem obciążenie może być większa niż inne biblioteki współbieżności, takich jak OpenMP. Dlatego zaleca się, należy przetestować wydajność przyrostowo gdy konwertujesz istniejący kod OpenMP do korzystania ze współbieżności środowiska wykonawczego.

## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Kiedy Migrowanie z OpenMP do współbieżności środowiska wykonawczego

Może być korzystne, aby przeprowadzić migrację istniejącego kodu OpenMP do współbieżności środowiska wykonawczego w następujących przypadkach.

|Przypadków|Zalety środowiska uruchomieniowego współbieżności|
|-----------|-------------------------------------------|
|Wymagane jest rozszerzalny platformy programowania współbieżnego.|Wiele funkcji w środowisku uruchomieniowym współbieżności: można rozszerzyć. Można także połączyć istniejące funkcje do tworzenia nowych. Ponieważ OpenMP opiera się na dyrektywy kompilatora, nie można łatwo rozszerzyć.|
|Aplikacja używającym blokowanie współpracy.|Gdy zadanie blokuje, ponieważ wymaga to zasób, który nie jest jeszcze dostępny, środowisku uruchomieniowym współbieżności: można wykonywać inne zadania, gdy pierwsze zadanie czeka na zasób.|
|Aplikacja może korzystać z dynamicznego równoważenia obciążenia.|Środowisko uruchomieniowe współbieżności używa planowania algorytmu, który dostosowuje alokacji zasobów obliczeniowych, jak zmienić obciążeń. W OpenMP gdy harmonogram przydziela zasoby obliczeniowe do równoległego regionu alokacje tych zasobów są ustalone w całym obliczeń.|
|Potrzebujesz pomocy technicznej do obsługi wyjątków.|PPL pozwala przechwytywać wyjątki i spoza równoległego regionu lub pętli. W OpenMP musi obsługiwać wyjątek w ramach równoległego regionu lub pętli.|
|Wymagane jest mechanizmie anulowania.|PPL umożliwia aplikacjom anulowanie zarówno pojedynczych zadań, jak i równoległych drzew pracy. OpenMP — wymaga od aplikacji, aby zaimplementować własny mechanizm anulowania.|
|Wymagane jest równoległy kod, aby zakończyć w innym kontekście, z którego został uruchomiony.|Środowisko uruchomieniowe współbieżności pozwala uruchomić zadanie w jednym kontekście, a następnie czekać lub anulować zadania w innym kontekście. W OpenMP wszystkie równoległą musi zakończyć się w kontekście, z którego został uruchomiony.|
|Ulepszona obsługa debugowania jest wymagana.|Program Visual Studio udostępnia **stosów równoległych** i **zadań równoległych** systemu windows, dzięki czemu można łatwiej debugowanie aplikacji wielowątkowych.<br /><br /> Aby uzyskać więcej informacji o debugowaniu Obsługa środowiska uruchomieniowego współbieżności, zobacz [korzystanie z okna zadań](/visualstudio/debugger/using-the-tasks-window), [przy użyciu Parallel Stacks Window](/visualstudio/debugger/using-the-parallel-stacks-window), i [wskazówki: debugowanie równoległego Aplikacja](/visualstudio/debugger/walkthrough-debugging-a-parallel-application).|

## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Kiedy nie należy Migrowanie z OpenMP do współbieżności środowiska wykonawczego

Gdy opisano, gdy nie mogą nie być odpowiednie przeprowadzić migrację istniejącego kodu OpenMP do współbieżności środowiska wykonawczego.

|Przypadków|Wyjaśnienie|
|-----------|-----------------|
|Twoja aplikacja już spełnia Twoje wymagania.|Jeśli jesteś zadowolony z wydajnością aplikacji i bieżącej obsługi debugowania, migracji mogą nie być odpowiednie.|
|Twoje treści pętli równoległej wykonać małego wysiłku.|Koszty związane z harmonogramu zadań w środowisku uruchomieniowym współbieżności: nie może być Pokonaj zalety wykonywania pętli w sposób równoległy, szczególnie w przypadku, gdy ciało pętli jest stosunkowo niewielka.|
|Aplikacja jest zapisywany w C.|Ponieważ środowisko uruchomieniowe współbieżności używa wielu funkcji języka C++, może nie być odpowiedni podczas nie można napisać kod, który umożliwia aplikacji C w pełni wykorzystać ją.|

## <a name="related-topics"></a>Tematy pokrewne

[Instrukcje: konwertowanie paraleli OpenMP dla pętli do korzystania ze środowiska uruchomieniowego współbieżności](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)

Biorąc pod uwagę podstawowe pętli, która korzysta z OpenMP [równoległe](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) i [dla](../../parallel/openmp/reference/for-openmp.md) dyrektyw, opisano sposób konwertowania go do korzystania ze współbieżności środowiska wykonawczego [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm.

[Instrukcje: konwertowanie pętli OpenMP stosującej anulowanie do korzystania ze środowiska uruchomieniowego współbieżności](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)<br/>
Biorąc pod uwagę OpenMP [równoległe](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[dla](../../parallel/openmp/reference/for-openmp.md) pętli, które nie wymagają wszystkich iteracji, aby uruchomić, opisano sposób konwertowania go do korzystania ze współbieżności środowiska wykonawczego mechanizmie anulowania.

[Instrukcje: konwertowanie pętli OpenMP używającej obsługi wyjątków do korzystania ze środowiska uruchomieniowego współbieżności](../../parallel/concrt/convert-an-openmp-loop-that uses-exception-handling.md)<br/>
Biorąc pod uwagę OpenMP [równoległe](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[dla](../../parallel/openmp/reference/for-openmp.md) pętli, która wykonuje obsługę wyjątków, opisano sposób konwertowania go do korzystania ze mechanizm obsługi wyjątków współbieżność środowiska wykonawczego.

[Instrukcje: konwertowanie pętli OpenMP używającej zmiennej redukcji do korzystania ze środowiska uruchomieniowego współbieżności](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)<br/>
Biorąc pod uwagę OpenMP [równoległe](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[dla](../../parallel/openmp/reference/for-openmp.md) pętli, która używa [redukcji](../../parallel/openmp/reference/reduction.md) klauzuli opisano sposób konwertowania go do korzystania ze współbieżności środowiska wykonawczego.

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)<br/>
[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)

