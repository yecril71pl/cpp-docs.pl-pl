---
title: Porównywanie współbieżności środowiska wykonawczego z innymi modelami współbieżności
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, compared to other models
ms.assetid: d8b9a1f4-f15f-43c3-a5b4-c0991edf9c86
ms.openlocfilehash: 5bc6691f6d0b166bb3084091ee6af70474937568
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422256"
---
# <a name="comparing-the-concurrency-runtime-to-other-concurrency-models"></a>Porównywanie współbieżności środowiska wykonawczego z innymi modelami współbieżności

W tym dokumencie opisano różnice między funkcjami i modelami programowania środowisko uruchomieniowe współbieżności i innymi technologiami. Zrozumienie, jak korzyści z środowisko uruchomieniowe współbieżności porównać z korzyściami z innych modeli programowania, można wybrać technologię, która najlepiej spełnia wymagania aplikacji.

Jeśli obecnie używasz innego modelu programowania, takiego jak Pula wątków systemu Windows lub OpenMP, istnieją sytuacje, w których może być odpowiednie do migracji do środowisko uruchomieniowe współbieżności. Na przykład temat [Migrowanie z OpenMP do środowisko uruchomieniowe współbieżności opisuje,](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md) kiedy może być odpowiednie do migracji z openmp do środowisko uruchomieniowe współbieżności. Jednak w przypadku spełnienia wymagań dotyczących wydajności aplikacji i bieżącej obsługi debugowania migracja nie jest wymagana.

Korzystając z funkcji i korzyści związanych z produktywnością środowisko uruchomieniowe współbieżności, można uzupełnić istniejącą aplikację, która korzysta z innego modelu współbieżności. Środowisko uruchomieniowe współbieżności nie może zagwarantować równoważenia obciążenia, gdy wiele harmonogramów zadań jest konkurujących dla tych samych zasobów obliczeniowych. Jeśli jednak obciążenia nie nakładają się na siebie, ten efekt jest minimalny.

## <a name="top"></a>Poszczególne

- [Porównywanie planowania z przeznaczeniem do wspólnego planowania](#models)

- [Porównywanie środowisko uruchomieniowe współbieżności z interfejsem API systemu Windows](#winapi)

- [Porównywanie środowisko uruchomieniowe współbieżności ze OpenMP](#openmp)

## <a name="models"></a>Porównywanie planowania z przeznaczeniem do wspólnego planowania

Model zastępujący i wspólne modele planowania są dwa typowe sposoby na umożliwienie wielu zadań współdzielenia zasobów obliczeniowych, na przykład procesorów lub wątków sprzętowych.

### <a name="preemptive-and-cooperative-scheduling"></a>Planowanie zastępujące i wspólne

*Planowanie zastępujące* to mechanizm okrężny, oparty na priorytetach, który zapewnia każdemu użytkownikowi wyłączny dostęp do zasobu obliczeniowego w danym okresie, a następnie przełącza się do innego zadania. Planowanie zastępujące jest wspólne w przypadku wielozadańowych systemów operacyjnych, takich jak Windows. *Planowanie wspólne* jest mechanizmem, który zapewnia każdemu użytkownikowi wyłączny dostęp do zasobów obliczeniowych do momentu zakończenia zadania lub do momentu uzyskania przez zadanie dostępu do zasobu. Środowisko uruchomieniowe współbieżności korzysta z planowania wspólnego wraz z zaplanowanym harmonogramem systemu operacyjnego w celu osiągnięcia maksymalnego użycia zasobów przetwarzania.

### <a name="differences-between-preemptive-and-cooperative-schedulers"></a>Różnice między programami zastępujące i spółdzielnie

Zastępujący harmonogramy starają się dać wielu wątkom równy dostęp do zasobów obliczeniowych, aby upewnić się, że każdy wątek wykonuje postęp. Na komputerach, które mają wiele zasobów obliczeniowych, zapewnienie sprawiedliwego dostępu jest mniej problematyczne. jednak zapewnienie efektywnego wykorzystania zasobów jest bardziej problematyczne.

Zastępujący harmonogram trybu jądra wymaga, aby kod aplikacji korzystał z systemu operacyjnego w celu podejmowania decyzji dotyczących planowania. Z kolei współpraca w trybie użytkownika umożliwia wykonywanie własnych decyzji dotyczących planowania przez kod aplikacji. Ze względu na to, że planowanie w ramach współpracy umożliwia wykonywanie wielu decyzji dotyczących planowania przez aplikację, zmniejsza to wiele nakładów związanych z synchronizacją w trybie jądra. Harmonogram współpracy zwykle uwzględnia decyzje związane z planowaniem jądra systemu operacyjnego, gdy nie ma żadnych innych zadań do zaplanowania. W przypadku operacji blokującej, która jest przekazywana do jądra, w ramach usługi Scheduler zostanie również przekazany do harmonogramu systemu operacyjnego, ale ta operacja nie jest przekazywana do harmonogramu trybu użytkownika.

### <a name="cooperative-scheduling-and-efficiency"></a>Wspólne planowanie i wydajność

W przypadku harmonogramu zastępują wszystkie prace o tym samym poziomie priorytetu są równe. Harmonogram zastępujący przeważnie planuje wątki w kolejności, w której zostały utworzone. Ponadto harmonogram zastępujący przypisuje każdy wątek a czas w sposób okrężny, na podstawie priorytetu wątku. Mimo że ten mechanizm zapewnia godziwość (każdy wątek postępuje postęp), jest to koszt wydajności. Na przykład wiele algorytmów intensywnie korzystających z obliczeń nie wymaga godziwości. Zamiast tego ważne jest, aby powiązane zadania kończyły się w minimalnym czasie. Wspólne planowanie pozwala aplikacji na efektywniejsze planowanie pracy. Rozważmy na przykład aplikację, która ma wiele wątków. Planowanie wątków, które nie udostępniają zasobów do uruchamiania współbieżnie, może zmniejszyć obciążenie synchronizacji i zwiększyć wydajność. Innym wydajnym sposobem planowania zadań jest uruchamianie potoków zadań (gdzie każde zadanie działa na danych wyjściowych poprzedniego) na tym samym procesorze, tak aby dane wejściowe poszczególnych etapów potoku zostały już załadowane do pamięci podręcznej pamięci.

### <a name="using-preemptive-and-cooperative-scheduling-together"></a>Używanie planowania z przeznaczeniem i współdziałaniem wspólnie

W ramach planowania wspólnego nie są rozwiązywane wszystkie problemy związane z planowaniem. Na przykład zadania, które nie są dość związane z innymi zadaniami, mogą zużywać wszystkie dostępne zasoby obliczeniowe i uniemożliwiać wykonywanie innych zadań. Środowisko uruchomieniowe współbieżności korzysta z zalet w zakresie wydajności w ramach planowania współdziałania, aby uzupełnić gwarancje związane z planowaniem zastępujące. Domyślnie środowisko uruchomieniowe współbieżności zapewnia wspólny harmonogram, który korzysta z algorytmu kradzieży pracy w celu efektywnego dystrybuowania pracy między zasobami obliczeniowymi. Jednak usługa środowisko uruchomieniowe współbieżności Scheduler opiera się również na założeniu harmonogramu systemu operacyjnego w celu stosunkowo spójnej dystrybucji zasobów między aplikacjami. Możesz również utworzyć niestandardowe harmonogramy i zasady harmonogramu w aplikacjach, aby utworzyć szczegółową kontrolę nad wykonywaniem wątków.

[[Top](#top)]

## <a name="winapi"></a>Porównywanie środowisko uruchomieniowe współbieżności z interfejsem API systemu Windows

Interfejs programowania aplikacji systemu Microsoft Windows, który jest zwykle określany jako interfejs API systemu Windows (i dawniej znany jako Win32), zapewnia model programowania, który umożliwia współbieżność aplikacji. Środowisko uruchomieniowe współbieżności kompiluje się w interfejsie API systemu Windows w celu zapewnienia dodatkowych modeli programistycznych, które nie są dostępne w podstawowym systemie operacyjnym.

Środowisko uruchomieniowe współbieżności kompiluje w modelu wątku interfejsu API systemu Windows w celu wykonania równoległej pracy. Używa również mechanizmów zarządzania pamięcią interfejsu API systemu Windows i lokalnego magazynu wątków. W systemach Windows 7 i Windows Server 2008 R2 korzysta z obsługi interfejsu API systemu Windows dla wątków i komputerów, które mają więcej niż 64 wątków sprzętowych. Środowisko uruchomieniowe współbieżności rozszerza model interfejsu API systemu Windows, dostarczając wspólny harmonogram zadań i algorytm kradzieży pracy, aby zmaksymalizować wykorzystanie zasobów obliczeniowych i włączyć wiele równoczesnych wystąpień usługi Scheduler.

### <a name="programming-languages"></a>Języki programowania

Interfejs API systemu Windows używa języka programowania C, aby uwidocznić model programowania. Środowisko uruchomieniowe współbieżności udostępnia interfejs C++ programowania, który korzysta z najnowszych funkcji w C++ języku. Na przykład funkcje lambda zapewniają zwięzły, bezpieczny dla typu mechanizm do definiowania równoległych funkcji roboczych. Aby uzyskać więcej informacji na temat C++ najnowszych funkcji używanych przez środowisko uruchomieniowe współbieżności, zobacz [Omówienie](../../parallel/concrt/asynchronous-message-blocks.md).

### <a name="threads-and-thread-pools"></a>Wątki i pule wątków

Centralny mechanizm współbieżności w interfejsie API systemu Windows jest wątkiem. Zwykle [Funkcja myFunction służy do tworzenia](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) wątków. Chociaż wątki są stosunkowo łatwe do utworzenia i używania, system operacyjny przydziela znaczną ilość czasu i inne zasoby do zarządzania nimi. Ponadto, chociaż każdy wątek ma mieć taki sam czas wykonywania jak każdy inny wątek na tym samym poziomie priorytetu, skojarzone obciążenie wymaga utworzenia wystarczająco dużych zadań. W przypadku mniejszych lub bardziej szczegółowych zadań narzuty skojarzone z współbieżnością mogą wznieść korzyści wynikające z równoczesnego uruchamiania zadań.

Pule wątków są jednym ze sposobów zmniejszenia kosztów zarządzania wątkami. Pule wątków niestandardowych i implementacja puli wątków zapewniane przez interfejs API systemu Windows umożliwiają wydajną pracę w małych elementach roboczych. Pula wątków systemu Windows przechowuje elementy robocze w kolejce First-In, First-Out (FIFO). Każdy element roboczy jest uruchamiany w kolejności, w której został dodany do puli.

Środowisko uruchomieniowe współbieżności implementuje algorytm kradzieży pracy w celu poszerzenia mechanizmu planowania FIFO. Algorytm przenosi zadania, które nie zostały jeszcze uruchomione w wątkach, które są uruchamiane z elementów roboczych. Chociaż algorytm kradzieży pracy można zrównoważyć obciążenia, może to spowodować zmianę kolejności elementów roboczych. Ten proces zmiany kolejności może spowodować, że element roboczy zostanie uruchomiony w innej kolejności niż przesłany. Jest to przydatne w przypadku algorytmów cyklicznych, gdy istnieje lepsza szansa, że dane są współużytkowane przez nowsze zadania niż w starszych. Wprowadzenie nowych elementów do uruchomienia oznacza mniejszą liczbę chybień w pamięci podręcznej i prawdopodobnie mniejszą liczbę błędów stron.

Z punktu widzenia systemu operacyjnego kradzieży pracy jest niesłuszne. Jednak w przypadku zastosowania przez aplikację algorytmu lub zadania w sposób równoległy, sprawiedliwa wartość w podzadaniach podrzędnych nie zawsze ma znaczenia. Co ma na celu szybkie zakończenie całego zadania. W przypadku innych algorytmów moduł FIFO jest odpowiednią strategią planowania.

### <a name="behavior-on-various-operating-systems"></a>Zachowanie w różnych systemach operacyjnych

W systemach Windows XP i Windows Vista aplikacje używające środowisko uruchomieniowe współbieżności zachowują się podobnie, z tą różnicą, że wydajność sterty została ulepszona w systemie Windows Vista.

W systemach Windows 7 i Windows Server 2008 R2 system operacyjny obsługuje współbieżność i skalowalność. Na przykład te systemy operacyjne obsługują komputery, które mają ponad 64 wątków sprzętowych. Istniejąca aplikacja, która korzysta z interfejsu API systemu Windows, musi zostać zmodyfikowana, aby można było korzystać z tych nowych funkcji. Jednak aplikacja, która używa środowisko uruchomieniowe współbieżności automatycznie korzysta z tych funkcji i nie wymaga modyfikacji.

[Base. User-mode_scheduling](/windows/win32/procthread/user-mode-scheduling)

[[Top](#top)]

## <a name="openmp"></a>Porównywanie środowisko uruchomieniowe współbieżności ze OpenMP

Środowisko uruchomieniowe współbieżności włącza różne modele programowania. Modele te mogą nakładać się lub uzupełniać modele innych bibliotek. W tej sekcji porównano środowisko uruchomieniowe współbieżności ze [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp).

Model programowania OpenMP jest definiowany przez otwarty standard i ma dobrze zdefiniowane powiązania z Pascal i językiem programowania C/C++ c++. Wersje OpenMP 2,0 i 2,5 są odpowiednie dla równoległych algorytmów, które są iteracyjne; oznacza to, że wykonują iterację równoległą w odniesieniu do tablicy danych. OpenMP jest najbardziej wydajny, gdy stopień równoległości jest wstępnie określony i jest zgodny z dostępnymi zasobami w systemie. Model OpenMP to szczególnie dobre dopasowanie w przypadku obliczeń o wysokiej wydajności, w przypadku których duże problemy obliczeniowe są dystrybuowane między zasobami przetwarzania jednego komputera. W tym scenariuszu środowisko sprzętowe jest znane, a deweloper może oczekiwać, że ma wyłączny dostęp do zasobów obliczeniowych, gdy algorytm jest wykonywany.

Jednak inne, mniej ograniczone środowiska obliczeniowe mogą nie być dobrym odpowiednikiem OpenMP. Na przykład problemy cykliczne (takie jak algorytm sortowania lub wyszukiwanie drzewa danych) są trudniejsze do zaimplementowania przy użyciu OpenMP. Środowisko uruchomieniowe współbieżności uzupełnia możliwości technologii OpenMP przez udostępnienie [biblioteki równoległych wzorców](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) i [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md). W przeciwieństwie do OpenMP, środowisko uruchomieniowe współbieżności zapewnia dynamiczny harmonogram, który dostosowuje się do dostępnych zasobów i dostosowuje stopień równoległości w miarę zmiany obciążeń.

Wiele funkcji w środowisko uruchomieniowe współbieżności można rozszerzyć. Możesz również połączyć istniejące funkcje, aby utworzyć nowe. Ponieważ OpenMP opiera się na dyrektywach kompilatora, nie można go łatwo rozszerzyć.

Aby uzyskać więcej informacji na temat porównuje środowisko uruchomieniowe współbieżności ze OpenMP i jak przeprowadzić migrację istniejącego kodu OpenMP do korzystania z środowisko uruchomieniowe współbieżności, zobacz [Migrowanie z OpenMP do środowisko uruchomieniowe współbieżności](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md).

[[Top](#top)]

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)<br/>
[Omówienie](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)
