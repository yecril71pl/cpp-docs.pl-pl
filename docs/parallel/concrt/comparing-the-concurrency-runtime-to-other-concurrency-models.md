---
title: "Porównywanie współbieżności środowiska wykonawczego z innymi modelami współbieżności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Concurrency Runtime, compared to other models
ms.assetid: d8b9a1f4-f15f-43c3-a5b4-c0991edf9c86
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e20523eb8a2c78cfa72b6c3084e9ca9f620a916c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comparing-the-concurrency-runtime-to-other-concurrency-models"></a>Porównywanie współbieżności środowiska wykonawczego z innymi modelami współbieżności
W tym dokumencie opisano różnice w funkcjach i modele programowania współbieżności środowiska wykonawczego i innych technologii. Zrozumienie, jak korzyści ze współbieżności środowiska wykonawczego Porównaj z zalet inne modele programowania, możesz wybrać technologia, która najlepiej spełnia wymagania aplikacji.  
  
 Jeśli obecnie używasz inny model programowania, takie jak pula wątków systemu Windows lub OpenMP, istnieją sytuacje, w których może być odpowiednie przeprowadzić migrację do współbieżności środowiska wykonawczego. Na przykład temat [Migrowanie z OpenMP do współbieżności środowiska wykonawczego](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md) w tym artykule opisano, kiedy może być odpowiednie do migracji z OpenMP do współbieżności środowiska wykonawczego. Jednak jeśli są zadowalające wydajność aplikacji i bieżącego obsługę debugowania, migracja nie jest wymagana.  
  
 Funkcje i korzyści współbieżności środowiska wykonawczego umożliwia uzupełnienie istniejących aplikacji, która używa innego modelu współbieżności. Współbieżność środowiska wykonawczego nie może zagwarantować równoważenia obciążenia, gdy wiele planiści zadań konkurują o tych samych zasobów obliczeniowych. Jednak w przypadku obciążeń nie pokrywają, efekt jest minimalny.  
  
##  <a name="top"></a>Sekcje  
  
-   [Porównywanie cenią sobie wcześniejsze planowanie do współpracy planowania](#models)  
  
-   [Porównywanie współbieżności środowiska wykonawczego systemu Windows API](#winapi)  
  
-   [Porównywanie współbieżności środowiska uruchomieniowego OpenMP](#openmp)  
  
##  <a name="models"></a>Porównywanie cenią sobie wcześniejsze planowanie do współpracy planowania  
 Model cenią sobie wcześniejsze i wspólnego planowania modeli są dwa podstawowe sposoby włączyć wielu zadań udostępnić zasoby obliczeniowe, na przykład, procesorów lub wątki sprzętu.  
  
### <a name="preemptive-and-cooperative-scheduling"></a>Planowanie cenią sobie wcześniejsze i współpracy  
 *Planowanie cenią sobie wcześniejsze* jest działanie okrężne, oparte na priorytetach mechanizm, który umożliwia każdego zadania wyłącznego dostępu do zasobów obliczeniowych w danym czasie, a następnie zmienia się na inne zadanie. Planowanie cenią sobie wcześniejsze jest typowe w przypadku wielozadaniowości systemy operacyjne, takie jak Windows*. Planowanie współpracy* jest mechanizm, który umożliwia każdego zadania wyłącznego dostępu do zasobów obliczeniowych, zakończenie zadania lub zadania daje jego dostępu do zasobu. Współbieżność środowiska wykonawczego używa współpracy planowania wraz z cenią sobie wcześniejsze Harmonogram systemu operacyjnego do osiągnięcia maksymalnego użycia przetwarzania zasobów.  
  
### <a name="differences-between-preemptive-and-cooperative-schedulers"></a>Różnice między planiści cenią sobie wcześniejsze i współpracy  
 Planiści cenią sobie wcześniejsze starać się zapewniają wiele wątków równy dostęp do zasobów, aby upewnić się, że wątek, co sprawia, że postęp obliczeniowych. Na komputerach, które mają wiele zasobów obliczeniowych zapewnienie odpowiedniej dostępu staje się mniej problematyczne; jednak zapewnienia jego efektywne wykorzystanie zasobów staje się bardziej kłopotliwy.  
  
 Harmonogram cenią sobie wcześniejsze trybu jądra wymaga kod aplikacji, zależą od systemu operacyjnego, aby decyzji w procesie planowania. Z drugiej strony harmonogramu współpracy trybu użytkownika umożliwia kod aplikacji, aby jego własnej decyzji w procesie planowania. Ponieważ wspólnych planowania umożliwia wiele decyzji planowania ma zostać wykonane przez aplikację, zmniejsza znacznie obciążenie, które jest skojarzone z synchronizacji w trybie jądra. Wspólne harmonogramu zwykle różni decyzji w procesie planowania jądra systemu operacyjnego, jeśli nie ma żadnych innych prac, można zaplanować. Wspólne harmonogramu również różni do harmonogramu systemu operacyjnego, gdy brak operacji blokowania, które są przekazywane do jądra, ale operacja nie jest przekazywane do harmonogramu trybu użytkownika.  
  
### <a name="cooperative-scheduling-and-efficiency"></a>Planowanie współpracy i wydajności  
 Do harmonogramu cenią sobie wcześniejsze wszystkie pracy, który ma na tym samym poziomie priorytetu są takie same. Harmonogram cenią sobie wcześniejsze zwykle planuje wątków w kolejności ich utworzenia. Ponadto cenią sobie wcześniejsze harmonogram zapewnia każdego wątku przedział czasu w sposób okrężnego na podstawie priorytetu wątku. Ten mechanizm zapewnia sprawiedliwe przydzielanie zasobów (wątku, co sprawia, że postęp), jednak jest dostarczany w niektórych koszt wydajności. Na przykład wiele algorytmów obliczeń intensywnie nie wymagają sprawiedliwe przydzielanie zasobów. Zamiast tego należy pamiętać, że powiązane zadania zakończone w najmniej całkowity czas. Planowanie współpracy umożliwia bardziej efektywne harmonogramu pracy aplikacji. Rozważmy na przykład aplikacja, która ma wiele wątków. Harmonogram wątków, które nie udostępniają zasoby równoczesne uruchamianie może zmniejszyć synchronizacji i zwiększając wydajność. Inny sposób efektywne planowanie zadań jest uruchomienie potoki zadań (gdzie każde zadanie działa na dane wyjściowe poprzedniego) na tym samym procesorze tak, aby w danych wejściowych na każdym z etapów potoku jest już załadowany do pamięci podręcznej.  
  
### <a name="using-preemptive-and-cooperative-scheduling-together"></a>Przy użyciu cenią sobie wcześniejsze i wspólnych planowania razem  
 Planowanie współpracy nie pomogą rozwiązać wszystkie problemy dotyczące planowania. Na przykład zadań, które nie zwracają dość do wykonywania innych zadań można używać wszystkich dostępnych zasobów obliczeniowych i uniemożliwić czyni postępy innych zadań. Współbieżność środowiska wykonawczego korzysta z zalet współpracy planowania wydajności uzupełnienie gwarancje sprawiedliwe przydzielanie zasobów cenią sobie wcześniejsze planowanie. Domyślnie współbieżności środowiska wykonawczego zawiera wspólne harmonogramu, który używa algorytmu kradzież pracy umożliwiająca efektywną dystrybucję pracy między zasobów obliczeniowych. Jednak harmonogramu współbieżność środowiska wykonawczego zależy również cenią sobie wcześniejsze Harmonogram systemu operacyjnego do dość dystrybucji zasobów między aplikacjami. Planiści niestandardowi i harmonogram zasad można również utworzyć w aplikacji do tworzenia precyzyjną kontrolę nad wykonanie wątku.  
  
 [[Górnej](#top)]  
  
##  <a name="winapi"></a>Porównywanie współbieżności środowiska wykonawczego systemu Windows API  
 Microsoft Windows interfejsu programowania aplikacji, która jest zwykle nazywany interfejsu API systemu Windows (i znanego wcześniej jako Win32), zapewnia model programowania umożliwiający współbieżność w aplikacji. Współbieżność środowiska wykonawczego opiera się na interfejs API systemu Windows, aby zapewnić dodatkowe modele programowania, które nie są dostępne w system operacyjny.  
  
 Współbieżność środowiska wykonawczego oparty na modelu wątku interfejsu API systemu Windows do wykonywania pracy równoległych. Używa również zarządzanie pamięcią interfejsu API systemu Windows i mechanizmów magazynu lokalnego wątku. W systemie Windows 7 i Windows Server 2008 R2 obsługę interfejsu API systemu Windows używa wątków schedulable użytkowników i komputerów, które mają ponad 64 wątków sprzętu. Współbieżność środowiska wykonawczego rozszerza modelu interfejsu API systemu Windows, zapewniając harmonogramu zadań współpracy i algorytmu kradzież pracy do optymalnego wykorzystania zasobów komputerowych i włączając wielu wystąpień jednoczesnych harmonogramu.  
   
### <a name="programming-languages"></a>Języki programowania  
 Interfejs API systemu Windows korzysta język programowania C, aby prezentować modelu programowania. Współbieżność środowiska wykonawczego udostępnia interfejs programowania C++, który korzysta z najnowszych funkcji w języku C++. Na przykład funkcje lambda mechanizm zwięzły, bezpieczne definiowania równoległych pracy funkcji. Aby uzyskać więcej informacji o najnowszych funkcjach języka C++, które używa współbieżności środowiska wykonawczego, zobacz [omówienie](../../parallel/concrt/asynchronous-message-blocks.md).  
  
### <a name="threads-and-thread-pools"></a>Wątki i pule wątków  
 Mechanizm centralnej współbieżność w interfejsie API systemu Windows jest wątku. Zazwyczaj używają [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) funkcji, aby utworzyć wątków. Mimo że wątki są stosunkowo łatwa do utworzenia i użycia, system operacyjny przydziela znaczną ilość czasu i innych zasobów do zarządzania nimi. Ponadto mimo, że każdy wątek jest gwarantowana do odbierania w czasie wykonywania innych wątków na tym samym poziomie priorytetu, skojarzony narzut wymaga utworzenia wystarczająco dużą zadania. Mniejszy lub bardziej szczegółowych zadań obciążenie, który jest skojarzony z współbieżności można przeważają korzyści uruchomionych zadań równolegle.  
  
 Pule wątków jest jednym ze sposobów kosztów zarządzania wątku. Pule wątków niestandardowych i zapewnianej przez interfejs API systemu Windows, włączyć zarówno małych elementów roboczych na wydajne działanie równoległe implementacji puli wątków. Pula wątków systemu Windows zachowuje elementów pracy w kolejce FIFO (FIFO) pierwszy w. Każdy element pracy jest uruchamiany w kolejności, w którym został dodany do puli.  
  
 Współbieżność środowiska wykonawczego implementuje algorytmu kradzież pracy rozszerzenie FIFO planowania mechanizmu. Algorytm przenosi zadania, które nie zostały jeszcze uruchomione wątki uruchomione poza elementów roboczych. Mimo że algorytm kradzież pracy umożliwiają równoważenie obciążeń, może również spowodować na zmianę kolejności elementów roboczych. Ten proces ponownego zamawiania może spowodować elementu pracy można uruchomić w innym porządku niż przesłanego. Jest to przydatne w przypadku algorytmów cykliczne przypadku lepiej szansy, że dane są udostępniane spośród zadań nowszej niż wśród tych starszych. Pobieranie nowych elementów ma być uruchomiony oznacza mniej Chybienia pamięci podręcznej i prawdopodobnie mniejszej liczby błędów stron.  
  
 Z punktu widzenia systemu operacyjnego kradzież pracy jest nieuczciwej. Jednak w przypadku aplikacji implementuje algorytm lub zadanie ma być wykonywane równolegle, sprawiedliwe przydzielanie zasobów między zadania podrzędne nie zawsze znaczenia. Ma znaczenia, co jest, jak szybko ogólną zadanie kończy się. Inne algorytmy FIFO jest odpowiednie strategii planowania.  
  
### <a name="behavior-on-various-operating-systems"></a>Zachowanie w różnych systemach operacyjnych  
 W systemie Windows XP i Windows Vista aplikacji, które korzystają ze współbieżności środowiska wykonawczego zachowują się podobnie, z wyjątkiem tego, że zwiększona wydajność sterty w systemie Windows Vista.  
  
 W systemie Windows 7 i Windows Server 2008 R2 dalsze system operacyjny obsługuje współbieżności i skalowalność. Te systemy operacyjne obsługują na przykład komputerów, które mają ponad 64 wątków sprzętu. Istniejących aplikacji, która używa interfejsu API systemu Windows muszą zostać zmodyfikowane, aby móc korzystać z nowych funkcji. Jednak aplikacji korzystającej ze współbieżności środowiska wykonawczego automatycznie korzysta z tych funkcji i nie wymagają modyfikacji.  
  
 [Base.user mode_scheduling](http://msdn.microsoft.com/library/windows/desktop/dd627187)  
  
 [[Górnej](#top)]  
  
##  <a name="openmp"></a>Porównywanie współbieżności środowiska uruchomieniowego OpenMP  
 Współbieżność środowiska wykonawczego umożliwia różne modele programowania. Te modele mogą nakładać się lub uzupełniają modeli z innych bibliotek. Ta sekcja porównuje współbieżności środowiska wykonawczego z [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp).  
  
 Model programowania OpenMP jest definiowana za pomocą standardem otwartym i ma dobrze zdefiniowanego powiązania z języków programowania Fortran i C/C++. OpenMP w wersji 2.0 i 2.5 dobrze nadają się do algorytmów równoległych iteracyjne; oznacza to ich wykonywanie równoległe iteracji przez tablicę danych. OpenMP jest najbardziej efektywne, gdy stopień równoległości jest wstępnie określane i zgodny z dostępnych zasobów w systemie. OpenMP model jest szczególnie przydatne dopasowania dla przetwarzanie o wysokiej wydajności, które bardzo dużych obliczeniową problemów są dystrybuowane między zasobami przetwarzania dla pojedynczego komputera. W tym scenariuszu środowisko sprzętowe jest znany i deweloper może spodziewać wyłącznego dostępu do zasobów obliczeniowych, gdy jest wykonywana przez algorytm.  
  
 Jednak inne, mniej ograniczone środowisk komputerowych nie może być dobrym dopasowania dla OpenMP. Na przykład trudniejsze do zaimplementowania przy użyciu OpenMP są cykliczne problemów (takich jak algorytm quicksort lub wyszukiwanie drzewa danych). Współbieżność środowiska wykonawczego uzupełnia możliwości OpenMP zapewniając [Biblioteka równoległych wzorców](../../parallel/concrt/parallel-patterns-library-ppl.md) (PLL) i [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md). W odróżnieniu od OpenMP współbieżności środowiska wykonawczego zapewnia dynamiczne harmonogramu, który dostosowuje się do dostępnych zasobów i dostosowuje stopień równoległości po zmianie obciążeń.  
  
 Można rozszerzyć wiele funkcji współbieżność środowiska wykonawczego. Można także połączyć istniejących funkcji, aby utworzyć nowe. Ponieważ OpenMP opiera się na dyrektywy kompilatora, nie może zostać rozszerzony w prosty sposób.  
  
 Aby uzyskać więcej informacji na temat porównuje współbieżność środowiska wykonawczego OpenMP i jak przeprowadzić migrację istniejącego kodu OpenMP do współbieżności środowiska wykonawczego, zobacz [Migrowanie z OpenMP do współbieżności środowiska wykonawczego](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md).  
  
 [[Górnej](#top)]  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność środowiska wykonawczego](../../parallel/concrt/concurrency-runtime.md)     
 [Omówienie](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Biblioteka równoległych wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)   
 [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)
