---
title: Porównywanie współbieżności środowiska wykonawczego z innymi modelami współbieżności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Concurrency Runtime, compared to other models
ms.assetid: d8b9a1f4-f15f-43c3-a5b4-c0991edf9c86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c0647b05f0f9dce7c3f9b9b1b79668646dbb874
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423360"
---
# <a name="comparing-the-concurrency-runtime-to-other-concurrency-models"></a>Porównywanie współbieżności środowiska wykonawczego z innymi modelami współbieżności

W tym dokumencie opisano różnice między funkcjami i modeli programowania, środowisku uruchomieniowym współbieżności: też inne technologie pomocne. Zrozumienie, jak korzyści ze współbieżności środowiska wykonawczego wypadają w porównaniu do korzystania z innych modeli programowania, można wybrać technologia, która najlepiej spełnia wymagania aplikacji.

Jeśli obecnie korzystasz z innego modelu programowania, takich jak Windows puli wątków ani OpenMP, istnieją sytuacje, gdzie może być odpowiednie do migracji do środowiska uruchomieniowego współbieżności. Na przykład temat [Migrowanie z OpenMP do współbieżności środowiska wykonawczego](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md) opisuje, kiedy może być odpowiednie do migracji z OpenMP do współbieżności środowiska wykonawczego. Jednakże jeżeli jesteś zadowolony z wydajnością aplikacji i bieżącej obsługi debugowania, migracja nie jest wymagana.

Funkcje i korzyści produktywności środowiska uruchomieniowego współbieżności służy jako uzupełnienie istniejących aplikacji korzystającej z innym modelem współbieżności. Środowisko uruchomieniowe współbieżności nie może zagwarantować równoważenia obciążenia, gdy wiele harmonogramów zadań konkurują o tych samych zasobów obliczeniowych. Jednak w przypadku obciążeń nie nakładają się, w tym celu jest minimalny.

##  <a name="top"></a> Sekcje

- [Porównywanie Preemptive harmonogramów planowania współpracy](#models)

- [Porównywanie współbieżności środowiska wykonawczego z Windows API](#winapi)

- [Porównywanie współbieżności środowiska wykonawczego z OpenMP](#openmp)

##  <a name="models"></a> Porównywanie Preemptive harmonogramów planowania współpracy

Preemptive modelu i cooperative planowania modeli są dwa podstawowe sposoby włączyć wielu zadań udostępnić zasoby obliczeniowe, na przykład procesory lub wątków sprzętu.

### <a name="preemptive-and-cooperative-scheduling"></a>Planowanie preemptive i współpracy

*Planowanie preemptive* jest działanie okrężne, oparte na priorytetach mechanizm, który umożliwia każdego zadania wyłącznego dostępu do zasobów obliczeniowych dla danego okresu, a następnie zmienia się na inne zadanie. Planowanie preemptive jest często używany w systemach operacyjnych wielozadaniowości, takich jak Windows *. Planowanie współpracy* to mechanizm, który zapewnia co zadanie wyłącznego dostępu do zasobów obliczeniowych, przed zakończeniem zadania lub zadania daje jego dostęp do zasobu. Środowisko uruchomieniowe współbieżności używa współpracy planowania wraz z preemptive Harmonogram systemu operacyjnego do osiągnięcia maksymalnego użycia przetwarzania zasobów.

### <a name="differences-between-preemptive-and-cooperative-schedulers"></a>Różnice między lotów Preemptive i współpracy

Preemptive lotów stara się zapewnić wielu wątków taki sam dostęp do zasobów, aby upewnić się, że każdy wątek sprawia, że postęp obliczeniowych. Na komputerach, które mają wiele zasobów obliczeniowych zapewniając uczciwego dostępu staje się mniej problematyczne; jednak zapewnienie efektywnego wykorzystania zasobów staje się bardziej problematyczne.

Harmonogram trybu jądra preemptive wymaga kod aplikacji, zależą od systemu operacyjnego do podejmowania decyzji dotyczących planowania. Z drugiej strony harmonogramu współpracy trybu użytkownika umożliwia kod aplikacji, aby jego własnej decyzji planowania. Ponieważ współpracy planowania umożliwia dotyczące planowania decyzji podejmowanych przez aplikację, zmniejsza to znacznie obciążenie, który jest skojarzony z synchronizacji w trybie jądra. Wspólne usługi scheduler zwykle odracza decyzji planowania do jądra systemu operacyjnego, gdy ma ona nie innych zadań do zaplanowania. Wspólne usługi scheduler również odracza do harmonogramu systemu operacyjnego, gdy operacja blokowania, który jest przekazywany do jądra, ale operacja nie jest przekazywane do harmonogramu trybu użytkownika.

### <a name="cooperative-scheduling-and-efficiency"></a>Planowanie współpracy i wydajność

Do harmonogramu preemptive cała praca, który ma ten sam poziom priorytetu są takie same. Preemptive scheduler planuje zazwyczaj wątki w kolejności, w którym są tworzone. Ponadto preemptive harmonogram zapewnia każdy wątek przedziału czasu w sposób okrężny, na podstawie priorytetu wątku. Chociaż ten mechanizm zapewnia sprawiedliwe (każdy wątek sprawia, że postęp), znajduje się na pewien koszt wydajności. Na przykład wiele algorytmów najintensywniejszej obliczeniowo nie wymagają sprawiedliwe. Zamiast tego należy pamiętać, że powiązane zadania zakończone w co najmniej całkowity czas. Planowanie współpracy umożliwia aplikacji wydajniej harmonogramu pracy. Na przykład rozważmy aplikację, która ma wiele wątków. Harmonogram wątków, które nie udostępniają zasoby, aby uruchamiać jednocześnie można zmniejszyć koszty synchronizacji i zwiększając wydajność. Innym sposobem efektywne planowanie zadań jest uruchomienie potoków zadań (gdzie każde zadanie podrzędne działa na dane wyjściowe poprzedniego) na tym samym procesorze tak, aby każdy z etapów potoku danych wejściowych jest już załadowana do pamięci podręcznej.

### <a name="using-preemptive-and-cooperative-scheduling-together"></a>Za pomocą Preemptive i współpracy ze sobą planowania

Planowanie współpracy nie rozwiązuje wszystkich problemów z planowaniem. Na przykład zadań, które nie dość dają wyniku do innych zadań można używać wszystkich dostępnych zasobów obliczeniowych i uniemożliwić innym zadaniom postępy. Środowisko uruchomieniowe współbieżności używa korzyści wydajność planowania współpracy jako uzupełnienie gwarancje sprawiedliwe preemptive planowania. Domyślnie środowisko uruchomieniowe współbieżności udostępnia wspólne harmonogram, który używa algorytmu kradzież pracy umożliwiająca efektywną dystrybucję między zasobami obliczeniowymi. Jednak harmonogram współbieżność środowiska wykonawczego korzysta również preemptive Harmonogram systemu operacyjnego do dość dystrybucji zasobów między aplikacjami. Można również utworzyć niestandardowe harmonogramów i zasad harmonogramu w swoich aplikacjach, aby wygenerować precyzyjną kontrolę nad wykonywaniem wątków.

[[Górnej](#top)]

##  <a name="winapi"></a> Porównywanie współbieżności środowiska wykonawczego z Windows API

Program Microsoft Windows interfejsu programowania aplikacji, która jest zwykle określane jako interfejsu API programu Windows (znana wcześniej jako Win32), zapewnia model programowania, który umożliwia współbieżności w swoich aplikacjach. Środowisko uruchomieniowe współbieżności opiera się na interfejs API Windows, aby zapewnić dodatkowe modele programowania, które nie są dostępne od zasadniczego systemu operacyjnego.

Środowisko uruchomieniowe współbieżności opiera się na modelu wątku interfejsu Windows API do wykonania pracy równoległej. Używa również interfejsu Windows API zarządzanie pamięcią i mechanizmy magazynu wątków lokalnych. Windows 7 i Windows Server 2008 R2 używa obsługi interfejsu API Windows wątków ustalonych w harmonogramie użytkownika — i komputerów, które mają więcej niż 64 wątków sprzętu. Środowisko uruchomieniowe współbieżności rozszerza modelu interfejsu API Windows, zapewniając harmonogramu zadań w zakresie współpracy i algorytmu kradzież pracy w celu optymalnego wykorzystania zasobów obliczeniowych i włączając wielu wystąpień harmonogramu jednoczesnych.

### <a name="programming-languages"></a>Języki programowania

Interfejs API Windows używa języka programowania C w celu udostępnienia modelu programowania. Środowisko uruchomieniowe współbieżności udostępnia interfejs programowania C++, która korzysta z najnowszych funkcji w języku C++. Na przykład funkcje lambda mechanizm zwięzły, bezpieczny do definiowania funkcji równoległej pracy. Aby uzyskać więcej informacji na temat najnowszych funkcji języka C++, których używa w środowisku uruchomieniowym współbieżności: zobacz [Przegląd](../../parallel/concrt/asynchronous-message-blocks.md).

### <a name="threads-and-thread-pools"></a>Wątki i pul wątków

Mechanizm centralnej współbieżności w interfejsie API Windows jest wątku. Zazwyczaj używa się [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) funkcja służąca do tworzenia wątków. Mimo że wątki są stosunkowo łatwa do tworzenia i używania, system operacyjny przydziela znaczną ilość czasu i innych zasobów, aby zarządzać nimi. Ponadto mimo że każdy wątek jest gwarantowane do odbierania w czasie wykonywania innego wątku, w tym samym poziomie priorytetu, skojarzonego obciążenie wymaga utworzenia zadania wystarczająco duży. Mniejsze lub bardziej szczegółowych zadań obciążenie, który jest skojarzony ze współbieżnością można przeważają korzyści równoległego uruchamiania zadań.

Pule wątków to jedyny sposób zmniejszenia kosztów zarządzania wątku. Pule wątków niestandardowych i implementacja puli wątków, dostarczonej przez interfejs API Windows włączyć zarówno małych elementów roboczych do wydajnego uruchamiania w sposób równoległy. Puli wątków Windows przechowuje elementy robocze w kolejce FIFO (FIFO) pierwszego w. Każdy element roboczy jest uruchomiona w kolejności, w którym został dodany do puli.

Środowisko uruchomieniowe współbieżności implementuje algorytm kradzież pracy w celu rozszerzenia FIFO mechanizm planowania. Algorytm przenosi zadania, które nie zostały rozpoczęte wątki uruchomione z elementami roboczymi. Mimo, że algorytm kradzież Praca mogą równoważyć procesy obciążeń, może być przyczyną na zmianę kolejności elementów roboczych. Ten proces ponownego zamawiania może spowodować elementu roboczego, można uruchomić w innym porządku niż jego zostało przesłane. Jest to przydatne w przypadku algorytmów cykliczne, których lepszym szansy na to, że dane są współużytkowane przez nowszą zadań niż wśród tych starszych. Wprowadzenie nowych elementów do uruchomienia jako pierwsza oznacza mniejszą liczbę Chybienia pamięci podręcznej i prawdopodobnie mniejszą liczbę błędów stron.

Z punktu widzenia systemu operacyjnego nieuczciwej jest kradzież pracy. Jednak w przypadku aplikacji implementuje algorytm lub zadanie do uruchomienia w sposób równoległy, sprawiedliwe spośród zadań podrzędnych nie zawsze znaczenia. Co jest istotne jest, jak szybko zakończeniem całego zadania. Dla innych algorytmów FIFO jest odpowiednią strategię planowania.

### <a name="behavior-on-various-operating-systems"></a>Zachowanie w różnych systemach operacyjnych

Windows XP i Windows Vista aplikacje, które używają środowiska uruchomieniowego współbieżności działają w podobny sposób, z tą różnicą, że sterty jest wydajność w Windows Vista.

Windows 7 i Windows Server 2008 R2 systemu operacyjnego obsługuje współbieżność i skalowalności. Na przykład te systemy operacyjne obsługują komputerów, które mają więcej niż 64 wątków sprzętu. Istniejącą aplikację, która korzysta z interfejsu API Windows muszą zostać zmodyfikowane, aby móc korzystać z tych nowych funkcji. Jednak aplikacja, która automatycznie używa środowiska uruchomieniowego współbieżności używa tych funkcji i nie wymagają modyfikacji.

[Base.user mode_scheduling](https://msdn.microsoft.com/library/windows/desktop/dd627187)

[[Górnej](#top)]

##  <a name="openmp"></a> Porównywanie współbieżności środowiska wykonawczego z OpenMP

Środowisko uruchomieniowe współbieżności umożliwia różne modele programowania. Te modele mogą nakładać się na lub uzupełniają modele innych bibliotek. W tej sekcji porównuje środowiska uruchomieniowego współbieżności z [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp).

Model programowania OpenMP jest definiowany przez otwarty standard i dobrze zdefiniowanych powiązań dla języków programowania Fortran i języka C/C++. OpenMP w wersji 2.0 i 2.5 są odpowiednie dla algorytmów równoległych, które są iteracyjne; oznacza to ich wykonywanie równoległe iteracji przez tablicę danych. OpenMP jest najbardziej efektywne, gdy stopień równoległości jest wstępnie określane i dopasowuje dostępnych zasobów w systemie. OpenMP model jest szczególnie dobre dopasowanie do obliczeń o wysokiej wydajności, bardzo duże rozwiązywania problemów obliczeniowych są dystrybuowane między zasobami przetwarzania dla pojedynczego komputera. W tym scenariuszu środowisko sprzętowe jest znany i deweloper może spodziewać ma wyłącznego dostępu do zasobów obliczeniowych, gdy jest wykonywana przez algorytm.

Jednak inne, mniej ograniczone środowiska obliczeniowe może nie być dobre dopasowanie dla OpenMP. Na przykład problemy rekursywnego (na przykład algorytm szybkiego sortowania lub wyszukiwania drzewo danych) są trudniejsze do zaimplementowania za pomocą OpenMP. Środowisko uruchomieniowe współbieżności uzupełnia możliwości OpenMP, zapewniając [biblioteki wzorców równoległych](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) i [bibliotekę asynchronicznych agentów](../../parallel/concrt/asynchronous-agents-library.md). W odróżnieniu od OpenMP środowisko uruchomieniowe współbieżności zapewnia dynamicznego harmonogram, który dostosowuje się do dostępnych zasobów i dostosowuje stopień równoległości, jak zmienić obciążeń.

Wiele funkcji w środowisku uruchomieniowym współbieżności: można rozszerzyć. Można także połączyć istniejące funkcje do tworzenia nowych. Ponieważ OpenMP opiera się na dyrektywy kompilatora, nie można rozszerzyć w prosty sposób.

Aby uzyskać więcej informacji o tym, jak porównuje współbieżność środowiska wykonawczego, OpenMP i jak przeprowadzić migrację istniejącego kodu OpenMP do współbieżności środowiska wykonawczego, zobacz [Migrowanie z OpenMP do współbieżności środowiska wykonawczego](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md).

[[Górnej](#top)]

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)<br/>
[Omówienie](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)
