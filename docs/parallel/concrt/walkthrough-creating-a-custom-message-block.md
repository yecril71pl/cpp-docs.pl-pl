---
title: 'Przewodnik: Tworzenie niestandardowego bloku komunikatów'
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: e7dfc5d78d2281d77b9ce882b302c4d7db776d3b
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64856985"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>Przewodnik: Tworzenie niestandardowego bloku komunikatów

Ten dokument zawiera opis sposobu tworzenia komunikatów niestandardowy typ bloku, które porządkuje przychodzące wiadomości według priorytetu.

Chociaż wbudowane typy bloku komunikatu zapewniają szeroki zakres funkcji, możesz utworzyć swój własny typ bloku komunikatu i dostosować go do wymagań aplikacji. Aby uzyskać opis typów bloku wbudowanych wiadomości dostarczanych przez bibliotekę asynchronicznych agentów, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu, przeczytaj następujące dokumenty:

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)

##  <a name="top"></a> Sekcje

Ten przewodnik zawiera następujące sekcje:

- [Projektowanie bloku komunikatów niestandardowych](#design)

- [Definiowanie obiektu bufor_priorytetowy klasy](#class)

- [Kompletny przykład](#complete)

##  <a name="design"></a> Projektowanie bloku komunikatów niestandardowych

Bloki komunikatów uczestniczą w Akcie wysyłania i odbierania komunikatów. Blok komunikatów, który wysyła wiadomości jest znany jako *blok źródłowy*. Blok komunikatów, który odbiera wiadomości jest znany jako *blok docelowy*. Blok komunikatów, który wysyła i odbiera wiadomości jest znany jako *blok propagatora*. Klasa abstrakcyjna używa biblioteki agentów [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) do reprezentowania bloków źródła i klasa abstrakcyjna [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) do reprezentowania bloków docelowych. Typy bloków wiadomości które działają jako wywodzą się z `ISource`; typy bloków wiadomości które działają jako obiekty docelowe wywodzą się z `ITarget`.

Chociaż można uzyskać typ bloku wiadomości bezpośrednio z `ISource` i `ITarget`, biblioteka agentów definiuje trzy klasy bazowe, które wykonują wiele funkcji, które są wspólne dla wszystkich typów bloku komunikatu, na przykład obsługa błędów i łączenie bloków wiadomości razem w sposób bezpieczny dla współbieżności. [Concurrency::source_block](../../parallel/concrt/reference/source-block-class.md) klasa pochodzi od `ISource` i wysyła wiadomości do innych bloków. [Concurrency::target_block](../../parallel/concrt/reference/target-block-class.md) klasa pochodzi od `ITarget` i odbiera komunikaty z innych bloków. [Concurrency::propagator_block](../../parallel/concrt/reference/propagator-block-class.md) klasa pochodzi od `ISource` i `ITarget` i wysyła wiadomości do innych bloków i odbiera komunikaty z innych bloków. Zalecamy użycie tych trzech klas bazowych do obsługi infrastruktury szczegółowej, dzięki czemu można skupić się na zachowaniu bloku komunikatu.

`source_block`, `target_block`, I `propagator_block` klasy są szablonami, które są parametryzowane na typ, który zarządza połączeniami lub linkami, między źródłowym i docelowym bloki i typ, który zarządza, jak wiadomości są przetwarzane. Biblioteka agentów definiuje dwa typy, które wykonują łącza zarządzania [concurrency::single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) i [concurrency::multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md). `single_link_registry` Klasa umożliwia blokowi komunikatu połączenie z jednym źródłem i jednym elementem docelowym. `multi_link_registry` Klasa umożliwia blokowi komunikatu połączenie z wieloma źródłami lub wieloma elementami docelowymi. Biblioteka agentów definiuje jedna klasa, która wykonuje zarządzania wiadomość [concurrency::ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md). `ordered_message_processor` Klasy umożliwiają blokadom przetwarzanie wiadomości w kolejności, w której otrzymuje je.

Aby lepiej zrozumieć, jak bloki komunikatów odnoszą się do ich źródła i obiektów docelowych, rozważmy następujący przykład. W tym przykładzie przedstawiono deklarację [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) klasy.

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

`transformer` Klasa pochodzi od `propagator_block`, a zatem działa jako blok źródłowy i blok docelowy. Akceptuje ona wiadomości typu `_Input` i wysyła komunikaty typu `_Output`. `transformer` Klasa określa `single_link_registry` jako Menedżera połączeń dla wszelkich bloków docelowych i `multi_link_registry` jako Menedżera połączeń dla bloków dowolnego źródła. W związku z tym `transformer` obiektu może zawierać maksymalnie jeden obiekt docelowy i nieograniczoną liczbę źródeł.

Klasa, która pochodzi od klasy `source_block` musi zaimplementować sześć metod: [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets), [accept_message](reference/source-block-class.md#accept_message), [reserve_message](reference/source-block-class.md#reserve_message), [ consume_message](reference/source-block-class.md#consume_message), [release_message](reference/source-block-class.md#release_message), i [resume_propagation](reference/source-block-class.md#resume_propagation). Klasa, która pochodzi od klasy `target_block` musi implementować [propagate_message](reference/propagator-block-class.md#propagate_message) — metoda i może opcjonalnie zaimplementować [send_message](reference/propagator-block-class.md#send_message) metody. Wyprowadzanie z `propagator_block` jest funkcjonalnie równoważna pochodzeniu z obu `source_block` i `target_block`.

`propagate_to_any_targets` Metoda jest wywoływana w czasie wykonywania to asynchronicznego lub synchronicznego przetwarzania wszelkich komunikatów przychodzących i propagowania wszystkich wiadomości wychodzących. `accept_message` Metoda jest wywoływana przez bloki miejsce docelowego, aby akceptować wiadomości. Wiele typów bloku komunikatu, takich jak `unbounded_buffer`, wysyła wiadomości tylko do pierwszego obiektu docelowego, który mógłby ją otrzymać. W związku z tym przenosi własność wiadomości do obiektu docelowego. Typy innych bloków komunikatów, takie jak [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md), oferują wiadomości do każdego z bloków jego miejsca docelowego. W związku z tym `overwrite_buffer` tworzy kopię wiadomości dla każdego z jego elementów docelowych.

`reserve_message`, `consume_message`, `release_message`, I `resume_propagation` metody umożliwiają blokom komunikatów wzięcia udziału w wiadomości rezerwacji. Miejsce docelowe blokuje połączenia `reserve_message` metody, gdy ich zaoferować komunikat lub zarezerwować komunikat do późniejszego użytku. Po zarezerwowaniu wiadomości przez blok docelowy, może wywołać `consume_message` metodę, aby zużyć tę wiadomość lub `release_message` metodę, aby anulować rezerwację. Podobnie jak w przypadku `accept_message` metody, implementacja `consume_message` można przenieść prawo własności wiadomości lub zwrócić kopię wiadomości. Po bloku docelowym zużywa lub zwalnia zarezerwowaną wiadomość, środowisko wykonawcze wywołuje `resume_propagation` metody. Zazwyczaj ta metoda nadal propaguje wiadomość, począwszy od następnej wiadomości w kolejce.

Środowisko uruchomieniowe wywołuje `propagate_message` metody asynchronicznej przenosi wiadomości z innego bloku do bieżącego. `send_message` Metoda przypomina `propagate_message`, z tą różnicą, że synchronicznie, zamiast asynchronicznie, wysyła komunikat do bloków docelowych. Domyślna implementacja klasy `send_message` odrzuca wszystkie wiadomości przychodzące. Środowisko wykonawcze nie wymaga żadnej z tych metod, jeśli wiadomość nie przejdzie funkcji opcjonalnych filtru skojarzonego z blokiem docelowym. Aby uzyskać więcej informacji na temat filtrów komunikatów, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md).

[[Górnej](#top)]

##  <a name="class"></a> Definiowanie obiektu bufor_priorytetowy klasy

`priority_buffer` Klasa jest niestandardowym typem bloku wiadomości, która porządkuje wiadomości przychodzące najpierw według priorytetu, a następnie według kolejności, w jakiej komunikaty są odbierane. `priority_buffer` Klasa przypomina [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) klasy, ponieważ posiada kolejkę wiadomości, a także ponieważ działa jako źródło i miejsce docelowe bloku komunikatów i może mieć wiele źródeł i wiele obiekty docelowe. Jednak `unbounded_buffer` opiera propagację tylko na kolejności, w której otrzymuje wiadomości od jej źródeł wiadomości.

`priority_buffer` Klasa otrzymuje komunikaty typu std::[krotki](../../standard-library/tuple-class.md) zawierających `PriorityType` i `Type` elementów. `PriorityType` odwołuje się do typu, który posiada priorytet każdej wiadomości; `Type` odnosi się do części danych wiadomości. `priority_buffer` Klasy wysyła komunikaty typu `Type`. `priority_buffer` Klasa zarządza także dwoma kolejkami wiadomości: [std::priority_queue](../../standard-library/priority-queue-class.md) obiektu dla wiadomości przychodzących i std::[kolejki](../../standard-library/queue-class.md) obiektu dla wiadomości wychodzących. Porządkowanie wiadomości według priorytetu jest przydatne, gdy `priority_buffer` obiekt otrzymuje wiele wiadomości jednocześnie lub kiedy otrzymuje wiele wiadomości zanim jakiekolwiek komunikaty są odczytywane przez konsumentów.

Oprócz siedmiu metod, klasa, która pochodzi od `propagator_block` musi implementować `priority_buffer` również klasy zastąpienia `link_target_notification` i `send_message` metody. `priority_buffer` Klasa definiuje również dwie metody pomocnika publicznego `enqueue` i `dequeue`oraz metody pomocnika prywatnego, `propagate_priority_order`.

Poniższa procedura opisuje sposób implementacji `priority_buffer` klasy.

#### <a name="to-define-the-prioritybuffer-class"></a>Aby zdefiniować klasę priority_buffer

1. Utwórz plik nagłówka C++ i nadaj mu nazwę `priority_buffer.h`. Alternatywnie można użyć istniejącego pliku nagłówka, który jest częścią projektu.

1. W `priority_buffer.h`, Dodaj następujący kod.

[!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. W `std` przestrzeni nazw, zdefiniuj specjalizacje [std::less](../../standard-library/less-struct.md) i [std::greater](../../standard-library/greater-struct.md) które działają na współbieżność::[komunikat](../../parallel/concrt/reference/message-class.md) obiektów.

[!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   `priority_buffer` Klasa przechowuje `message` obiekty w `priority_queue` obiektu. Specjalizacje tego typu włączają kolejkę priorytetów posortowanych wiadomości według ich priorytetu. Priorytet jest pierwszym elementem `tuple` obiektu.

1. W `concurrencyex` przestrzeni nazw, Zadeklaruj `priority_buffer` klasy.

[!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   `priority_buffer` Klasa pochodzi od `propagator_block`. W związku z tym jego mogą wysyłać i odbierać komunikaty. `priority_buffer` Klasa może mieć wiele elementów docelowych, które odbierają komunikaty typu `Type`. Może też mieć wiele źródeł, które wysyłają wiadomości typu `tuple<PriorityType, Type>`.

1. W `private` części `priority_buffer` klasy, Dodaj następujące zmienne Członkowskie.

[!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   `priority_queue` Obiekt zawiera wiadomości przychodzące; `queue` obiekt zawiera wiadomości wychodzące. A `priority_buffer` obiektu może odbierać wiele wiadomości równocześnie; `critical_section` obiektu synchronizuje dostęp do kolejki komunikatów wejściowych.

1. W `private` sekcji, zdefiniować Konstruktor kopiujący i operator przypisania. Zapobiega to `priority_queue` przypisaniu obiektów.

[!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. W `public` sekcji, zdefiniuj konstruktory, które są wspólne dla wielu typów bloku komunikatu. Również określa destruktor.

[!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. W `public` sekcji, definiować metody `enqueue` i `dequeue`. Te metody pomocnika zapewniają alternatywny sposób wysyłania wiadomości do i odbierania komunikatów z `priority_buffer` obiektu.

[!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

9. W `protected` sekcji, zdefiniuj `propagate_to_any_targets` metody.

[!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   `propagate_to_any_targets` Metoda przesyła wiadomości, który znajduje się na wierzchu kolejki wejściowej do kolejki wyjściowej i propaguje wszystkie wiadomości z kolejki wyjściowej.

10. W `protected` sekcji, zdefiniuj `accept_message` metody.

[!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   Kiedy blick docelowy wywołuje `accept_message` metody `priority_buffer` klasa przenosi własności wiadomości do pierwszego bloku docelowego, która go akceptuje. (Przypomina to zachowanie `unbounded_buffer`.)

11. W `protected` sekcji, zdefiniuj `reserve_message` metody.

[!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   `priority_buffer` Klasy zezwala, aby blok docelowy zarezerwował komunikat, gdy dostarczony identyfikator wiadomości pasuje do identyfikatora komunikat, który znajduje się na wierzchu kolejki. Innymi słowy, obiekt docelowy może zarezerwować wiadomość, jeśli `priority_buffer` obiektu nie otrzymał jeszcze dodatkowej wiadomości i nie ma jeszcze rozpropagowane się bieżący.

12. W `protected` sekcji, zdefiniuj `consume_message` metody.

[!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   Blok docelowy wywołuje `consume_message` można przenieść własności wiadomości zastrzeżonej.

13. W `protected` sekcji, zdefiniuj `release_message` metody.

[!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   Blok docelowy wywołuje `release_message` Aby anulować swoje zastrzeżenia do wiadomości.

14. W `protected` sekcji, zdefiniuj `resume_propagation` metody.

[!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   Środowisko uruchomieniowe wywołuje `resume_propagation` po bloku docelowym zużywa lub zwalnia zarezerwowaną wiadomość. Ta metoda propaguje wszelkie wiadomości z kolejki wyjściowej.

15. W `protected` sekcji, zdefiniuj `link_target_notification` metody.

[!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   `_M_pReservedFor` Zmienna członka jest zdefiniowany przez klasę bazową `source_block`. Ta zmienna członka wskazuje blok docelowy, jeśli taki posiada rezerwację wiadomość, która znajduje się na wierzchu kolejki wyjściowej. Środowisko uruchomieniowe wywołuje `link_target_notification` kiedy nowy obiekt docelowy jest połączony z `priority_buffer` obiektu. Ta metoda rozdaje komunikaty, które znajdują się w kolejce wyjścia, jeśli żadne miejsce docelowe nie posiada rezerwacji.

16. W `private` sekcji, zdefiniuj `propagate_priority_order` metody.

[!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   Ta metoda propaguje wszystkie wiadomości z kolejki wyjściowej. Każda wiadomość w kolejce jest oferowana do każdego bloku docelowego aż jeden z bloków docelowych zaakceptuje wiadomość. `priority_buffer` Klasa zachowuje kolejności wiadomości wychodzących. Dlatego pierwszy komunikat w kolejce wyjściowej musi zostać zaakceptowana przez blok docelowy, zanim ta metoda da inne wiadomości do bloków docelowych.

17. W `protected` sekcji, zdefiniuj `propagate_message` metody.

[!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   `propagate_message` Metoda umożliwia `priority_buffer` klasie działania jako odbiorcom wiadomości lub celom. Ta metoda odbiera komunikat, który jest oferowany przez zapewniony blok źródłowy i wstawia tę wiadomość w kolejce priorytetu. `propagate_message` Metoda następnie asynchronicznie wysyła wszystkie wyjściowe komunikaty do bloków docelowych.

   Środowisko wykonawcze wywołuje tę metodę podczas wywoływania [concurrency::asend](reference/concurrency-namespace-functions.md#asend) funkcji lub gdy blok komunikatów jest podłączony do innych bloków komunikatów.

18. W `protected` sekcji, zdefiniuj `send_message` metody.

[!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   `send_message` Metoda przypomina `propagate_message`. Jednak wysyła wiadomości danych wyjściowych synchronicznie zamiast asynchronicznie.

   Środowisko wykonawcze wywołuje tę metodę podczas synchronicznej operacji, takich jak podczas wywoływania [concurrency::send](reference/concurrency-namespace-functions.md#send) funkcji.

`priority_buffer` Klasa zawiera konstruktora przeciążeń, które jest typowy w wielu typów bloku komunikatu. Niektóre konstruktory przeciążeń przybierają [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) lub [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) obiektów, które umożliwiają blok komunikatów, które mają być zarządzane przez harmonogram zadań szczególnych. Inne konstruktory przeładowania mają funkcję filtru. Funkcje filtrowania umożliwiają blokom wiadomości akceptowanie lub odrzucanie wiadomość na podstawie ładunku. Aby uzyskać więcej informacji na temat filtrów komunikatów, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md). Aby uzyskać więcej informacji dotyczących harmonogramów zadań, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Ponieważ `priority_buffer` klasy zszereguje wiadomości według priorytetu, a następnie według kolejności, w jakiej komunikaty są odbierane, klasa ta jest najbardziej użyteczna po odebraniu wiadomości asynchronicznie, na przykład gdy wywołujesz [concurrency::asend](reference/concurrency-namespace-functions.md#asend)funkcji lub gdy blok komunikatów jest podłączony do innych bloków komunikatów.

[[Górnej](#top)]

##  <a name="complete"></a> Kompletny przykład

Poniższy przykład pokazuje kompletną definicję `priority_buffer` klasy.

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

Poniższy przykład wykonuje jednocześnie wiele `asend` i [concurrency::receive](reference/concurrency-namespace-functions.md#receive) operacji na `priority_buffer` obiektu.

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe.

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

`priority_buffer` Klasy zszereguje najpierw wiadomości, według priorytetu, a następnie według kolejności, w której otrzymuje wiadomości. W tym przykładzie wiadomości o większym priorytecie liczbowym są wstawiane do przodu kolejki.

[[Górnej](#top)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub Wklej definicję `priority_buffer` klasy w pliku o nazwie `priority_buffer.h` a program badań w pliku o nazwie `priority_buffer.cpp` , a następnie uruchom następujące polecenie w programie Visual Studio Okno wiersza polecenia.

**Cl.exe/ehsc priority_buffer.cpp**

## <a name="see-also"></a>Zobacz także

[Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)
