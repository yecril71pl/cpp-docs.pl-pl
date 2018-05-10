---
title: Migrowanie z OpenMP do współbieżności środowiska wykonawczego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16e10287526e6b815ba56183a8e3d590102507aa
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>Migrowanie z OpenMP do współbieżności środowiska wykonawczego
Współbieżność środowiska wykonawczego umożliwia różne modele programowania. Te modele mogą nakładać się lub uzupełniają modeli z innych bibliotek. Dokumenty w tej sekcji porównaj [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp) do współbieżności środowiska wykonawczego i zawierają przykłady dotyczące migracji istniejącego kodu OpenMP do współbieżności środowiska wykonawczego.  
  
 Model programowania OpenMP jest definiowana za pomocą standardem otwartym i ma dobrze zdefiniowanego powiązania z języków programowania Fortran i C/C++. OpenMP w wersji 2.0 i 2.5, które są obsługiwane przez kompilatora Visual C++, są odpowiednie dla algorytmów równoległych iteracyjne; oznacza to ich wykonywanie równoległe iteracji przez tablicę danych. OpenMP 3.0 obsługuje-iteracyjne zadania i zadania iteracji.  
  
 OpenMP jest najbardziej efektywne, gdy stopień równoległości jest wstępnie określane i zgodny z dostępnych zasobów w systemie. OpenMP model jest szczególnie przydatne dopasowania dla przetwarzanie o wysokiej wydajności, których bardzo dużych problemów obliczeniowa są rozmieszczane przetwarzania zasobów z jednego komputera. W tym scenariuszu środowisko sprzętu zazwyczaj jest stała i deweloper może spodziewać ma wyłączny dostęp do wszystkich zasobów obliczeniowych, gdy wykonywane jest algorytm.  
  
 Jednak mniej ograniczone środowisk komputerowych nie może być dobrym dopasowania dla OpenMP. Na przykład trudniejsze do zaimplementowania przy użyciu OpenMP 2.0 i 2.5 są cykliczne problemów (takich jak algorytm quicksort lub wyszukiwanie drzewa danych). Współbieżność środowiska wykonawczego uzupełnia możliwości OpenMP zapewniając [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) i [Biblioteka równoległych wzorców](../../parallel/concrt/parallel-patterns-library-ppl.md) (PLL). Biblioteki agentów asynchronicznych obsługuje równoległość zadań coarse-grained; PPL obsługuje więcej szczegółowych zadań równoległych. Współbieżność środowiska wykonawczego udostępnia infrastrukturę, która jest wymagana do wykonywania operacji równolegle, dzięki czemu można skupić się na logiki aplikacji. Jednak ponieważ współbieżności środowiska wykonawczego umożliwia różne modele programowania, jego planowania obciążenie może być większa niż innych bibliotek współbieżności, takich jak OpenMP. Dlatego zaleca się, że należy przetestować wydajność przyrostowo podczas konwertowania z istniejącego kodu OpenMP do współbieżności środowiska wykonawczego.  
  
## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Podczas migracji z OpenMP do współbieżności środowiska wykonawczego  
 Może być korzystne w przypadku migracji z istniejącego kodu OpenMP do współbieżności środowiska wykonawczego w następujących przypadkach.  
  
|Przypadków|Zalety współbieżności środowiska wykonawczego|  
|-----------|-------------------------------------------|  
|Wymagane jest, czyli rozszerzalne środowisko programowania współbieżnych.|Można rozszerzyć wiele funkcji współbieżność środowiska wykonawczego. Można także połączyć istniejących funkcji, aby utworzyć nowe. Ponieważ OpenMP opiera się na dyrektywy kompilatora, nie można łatwo rozszerzyć.|  
|Aplikacja będzie korzystać z blokuje współpracy.|Gdy zadanie blokuje, ponieważ wymaga ona z zasobem, który nie jest jeszcze dostępna, współbieżności środowiska wykonawczego można wykonywać inne zadania podczas pierwszego zadania oczekiwania przez zasób.|  
|Aplikacja będzie korzystać z dynamicznego równoważenia obciążenia.|Współbieżność środowiska wykonawczego używa algorytmu planowania, które można dostosować przydziału zasobów obliczeniowych, jak zmienić obciążeń. W OpenMP gdy harmonogram przydziela zasoby obliczeniowe do równoległego regionu tych alokacji zasobów są ustalone w całym obliczenia.|  
|Wymagana jest obsługa obsługi wyjątków.|PPL umożliwia przechwytywanie wyjątków wewnątrz i poza równoległego regionu lub pętli. W OpenMP musi obsługiwać wyjątek w ramach równoległego regionu lub pętli.|  
|Wymagane jest mechanizm anulowania.|PPL umożliwia aplikacjom anulować zarówno poszczególne zadania i równoległych drzewa pracy. OpenMP wymaga, aby zaimplementować mechanizm anulowania aplikacja.|  
|Równoległego kodu na zakończenie w kontekście innej, z którego uruchamiany jest wymagana.|Współbieżność środowiska wykonawczego pozwala uruchomić zadanie w kontekście jednej i poczekaj lub anulowanie tego zadania w innym kontekście. W OpenMP wszystkie wykonywane równolegle musi zakończyć się w kontekście, w którym rozpoczyna się.|  
|Wymagane jest rozszerzoną obsługę debugowania.|Program Visual Studio udostępnia **stosów równoległych** i **zadań równoległych** systemu windows, dzięki czemu można łatwiej Debuguj wielowątkowe aplikacje.<br /><br /> Aby uzyskać więcej informacji o debugowaniu Obsługa współbieżności środowiska wykonawczego, zobacz [korzystanie z okna zadań](/visualstudio/debugger/using-the-tasks-window), [za pomocą okna stosów równoległych](/visualstudio/debugger/using-the-parallel-stacks-window), i [wskazówki: debugowanie równoległego Aplikacja](/visualstudio/debugger/walkthrough-debugging-a-parallel-application).|  
  
## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Kiedy nie można migrować z OpenMP do współbieżności środowiska wykonawczego  
 Gdy opisano, gdy nie można zastosować do migracji istniejącego kodu OpenMP do współbieżności środowiska wykonawczego.  
  
|Przypadków|Wyjaśnienie|  
|-----------|-----------------|  
|Aplikacja już odpowiadać wymaganiom.|Jeśli są zadowalające wydajność aplikacji i bieżącego obsługę debugowania, migracji może nie być odpowiednie.|  
|Twoje treści pętli równoległego wykonywania małego wysiłku.|Obciążenie współbieżność środowiska wykonawczego harmonogram zadań nie może rozwiązać zalet wykonywania pętli równolegle, szczególnie w przypadku względnie niewielkich treści pętli.|  
|Aplikacja została napisana C.|Ponieważ współbieżności środowiska wykonawczego korzysta z wielu funkcji języka C++, może nie być odpowiednie, gdy nie można zapisać kodu, który umożliwia aplikacji C w pełni wykorzystać go.|  
  
## <a name="related-topics"></a>Tematy pokrewne  
 [Instrukcje: konwertowanie paraleli OpenMP dla pętli do korzystania ze środowiska uruchomieniowego współbieżności](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)  

 Podane podstawowe pętli, które używa OpenMP [równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) i [dla](../../parallel/openmp/reference/for-openmp.md) dyrektywy, pokazuje, jak przekonwertować go do korzystania ze współbieżności środowiska wykonawczego [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm.  

  
 [Instrukcje: konwertowanie pętli OpenMP stosującej anulowanie do korzystania ze środowiska uruchomieniowego współbieżności](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)  
 Podane OpenMP [równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[dla](../../parallel/openmp/reference/for-openmp.md) pętli, które nie wymaga wszystkich iteracji, aby uruchomić, pokazuje, jak przekonwertować go do korzystania ze współbieżności środowiska wykonawczego mechanizmu anulowania.  
  
 [Instrukcje: konwertowanie pętli OpenMP używającej obsługi wyjątków do korzystania ze środowiska uruchomieniowego współbieżności](../../parallel/concrt/convert-an-openmp-loop-that uses-exception-handling.md)  
 Podane OpenMP [równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[dla](../../parallel/openmp/reference/for-openmp.md) pętli, które wykonuje obsługi wyjątków, pokazuje, jak przekonwertować go pod kątem użycia mechanizmu obsługi wyjątków współbieżności środowiska wykonawczego.  
  
 [Instrukcje: konwertowanie pętli OpenMP używającej zmiennej redukcji do korzystania ze środowiska uruchomieniowego współbieżności](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)  
 Podane OpenMP [równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[dla](../../parallel/openmp/reference/for-openmp.md) pętli, które używa [redukcji](../../parallel/openmp/reference/reduction.md) klauzuli pokazano, jak przekonwertować go do korzystania ze współbieżności środowiska wykonawczego.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność środowiska wykonawczego](../../parallel/concrt/concurrency-runtime.md)   
 [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)   
 [Biblioteka równoległych wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)

