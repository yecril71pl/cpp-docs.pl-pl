---
title: 'Wskazówki: tworzenie niestandardowego bloku komunikatów'
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: a29ed382d67b91443bd13e029af2a37c42ee834d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142827"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>Wskazówki: tworzenie niestandardowego bloku komunikatów

W tym dokumencie opisano sposób tworzenia niestandardowego typu bloku komunikatów, który porządkuje komunikaty przychodzące według priorytetu.

Chociaż wbudowane typy bloków komunikatów zapewniają szeroką gamę funkcji, można utworzyć własny typ bloku komunikatów i dostosować go do wymagań aplikacji. Aby uzyskać opis wbudowanych typów bloków komunikatów, które są dostarczane przez bibliotekę agentów asynchronicznych, zobacz [asynchroniczne bloki komunikatów](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu zapoznaj się z następującymi dokumentami:

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)

## <a name="top"></a>Poszczególne

Ten Instruktaż zawiera następujące sekcje:

- [Projektowanie niestandardowego bloku komunikatów](#design)

- [Definiowanie klasy priority_buffer](#class)

- [Kompletny przykład](#complete)

## <a name="design"></a>Projektowanie niestandardowego bloku komunikatów

Bloki komunikatów uczestniczą w wysyłaniu i otrzymywaniu komunikatów. Blok komunikatów, który wysyła wiadomości jest znany jako *blok źródłowy*. Blok komunikatów, który odbiera wiadomości jest znany jako *blok docelowy*. Blok komunikatów, który wysyła i odbiera wiadomości jest znany jako *blok propagacji*. Biblioteka agentów używa klasy abstrakcyjnej [concurrency:: ISource](../../parallel/concrt/reference/isource-class.md) do reprezentowania bloków źródłowych i abstrakcyjnej klasy [concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md) do reprezentowania bloków docelowych. Typy bloku komunikatów, które działają jako źródła pochodzą z `ISource`; typy bloku komunikatów, które działają jako obiekty docelowe, pochodzą od `ITarget`.

Chociaż można utworzyć typ bloku komunikatu bezpośrednio z `ISource` i `ITarget`, biblioteka agenci definiuje trzy klasy bazowe, które wykonują wiele funkcji wspólnych dla wszystkich typów bloku komunikatów, na przykład obsługę błędów i łączenie bloków komunikatów ze sobą w sposób bezpieczny dla współbieżności. Klasa [concurrency:: source_block](../../parallel/concrt/reference/source-block-class.md) dziedziczy po `ISource` i wysyła komunikaty do innych bloków. Klasa [concurrency:: target_block](../../parallel/concrt/reference/target-block-class.md) dziedziczy po `ITarget` i odbiera komunikaty z innych bloków. Klasa [concurrency::p ropagator_block](../../parallel/concrt/reference/propagator-block-class.md) dziedziczy po `ISource` i `ITarget` i wysyła komunikaty do innych bloków i odbiera komunikaty z innych bloków. Zalecamy używanie tych trzech klas bazowych do obsługi szczegółów infrastruktury, aby można było skupić się na zachowaniu bloku komunikatów.

Klasy `source_block`, `target_block`i `propagator_block` są szablonami, które są sparametryzowane na typie, który zarządza połączeniami lub łączami, między blokami źródłowymi i docelowymi oraz na typie, który zarządza sposobem przetwarzania komunikatów. Biblioteka agenci definiuje dwa typy, które wykonują zarządzanie linkami, [concurrency:: single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) i [concurrency:: multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md). Klasa `single_link_registry` umożliwia połączenie bloku komunikatów z jednym źródłem lub jednym obiektem docelowym. Klasa `multi_link_registry` umożliwia połączenie bloku komunikatów z wieloma źródłami lub wieloma obiektami docelowymi. Biblioteka agenci definiuje jedną klasę, która wykonuje zarządzanie komunikatami [concurrency:: ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md). Klasa `ordered_message_processor` umożliwia blokom komunikatów przetwarzanie komunikatów w kolejności, w jakiej je odbiera.

Aby lepiej zrozumieć sposób, w jaki bloki komunikatów odnoszą się do ich źródeł i elementów docelowych, weź pod uwagę Poniższy przykład. Ten przykład pokazuje deklarację klasy [concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) .

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

Klasa `transformer` pochodzi od `propagator_block`i dlatego działa jako blok źródłowy i jako blok docelowy. Akceptuje komunikaty typu `_Input` i wysyła komunikaty typu `_Output`. Klasa `transformer` określa `single_link_registry` jako Menedżera linków dla dowolnych bloków docelowych i `multi_link_registry` jako Menedżera linków dla wszystkich bloków źródłowych. W związku z tym obiekt `transformer` może mieć maksymalnie jeden element docelowy i nieograniczoną liczbę źródeł.

Klasa, która pochodzi od `source_block` musi implementować sześć metod: [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets), [accept_message](reference/source-block-class.md#accept_message), [reserve_message](reference/source-block-class.md#reserve_message), [consume_message](reference/source-block-class.md#consume_message), [release_message](reference/source-block-class.md#release_message)i [resume_propagation](reference/source-block-class.md#resume_propagation). Klasa, która pochodzi od `target_block` musi implementować metodę [propagate_message](reference/propagator-block-class.md#propagate_message) i opcjonalnie może zaimplementować metodę [send_message](reference/propagator-block-class.md#send_message) . Wyprowadzanie z `propagator_block` jest funkcjonalnie równoważne z pochodną obu `source_block` i `target_block`.

Metoda `propagate_to_any_targets` jest wywoływana przez środowisko uruchomieniowe w celu asynchronicznego lub synchronicznego przetwarzania wszelkich komunikatów przychodzących i propagowania wszelkich wychodzących komunikatów. Metoda `accept_message` jest wywoływana przez bloki docelowe w celu akceptowania komunikatów. Wiele typów bloku komunikatów, takich jak `unbounded_buffer`, wysyła wiadomości tylko do pierwszego obiektu docelowego, który go otrzyma. W związku z tym przenosi własność wiadomości do obiektu docelowego. Inne typy bloku komunikatów, takie jak [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md), oferują komunikaty do każdego z jego bloków docelowych. W związku z tym `overwrite_buffer` tworzy kopię wiadomości dla każdego z jej obiektów docelowych.

Metody `reserve_message`, `consume_message`, `release_message`i `resume_propagation` umożliwiają blokom komunikatów uczestniczenie w rezerwacji komunikatów. Bloki docelowe wywołują metodę `reserve_message`, gdy są oferowane przez nich komunikat i muszą zarezerwować komunikat do późniejszego użycia. Gdy blok docelowy rezerwuje komunikat, może wywołać metodę `consume_message`, aby użyć tej wiadomości lub metody `release_message` do anulowania rezerwacji. Podobnie jak w przypadku metody `accept_message` implementacja `consume_message` może przenieść własność wiadomości lub zwrócić kopię wiadomości. Gdy blok docelowy zużywa lub zwalnia zastrzeżony komunikat, środowisko uruchomieniowe wywołuje metodę `resume_propagation`. Zazwyczaj ta metoda kontynuuje propagację komunikatów, rozpoczynając od następnej wiadomości w kolejce.

Środowisko uruchomieniowe wywołuje metodę `propagate_message`, aby asynchronicznie przenieść komunikat z innego bloku do bieżącego. Metoda `send_message` przypomina `propagate_message`, z tą różnicą, że synchronicznie zamiast asynchronicznie wysyła komunikat do bloków docelowych. Domyślna implementacja `send_message` odrzuca wszystkie wiadomości przychodzące. Środowisko uruchomieniowe nie wywołuje żadnej z tych metod, jeśli komunikat nie przeszedł opcjonalnej funkcji filtru, która jest skojarzona z blokiem docelowym. Aby uzyskać więcej informacji na temat filtrów komunikatów, zobacz [asynchroniczne bloki komunikatów](../../parallel/concrt/asynchronous-message-blocks.md).

[[Top](#top)]

## <a name="class"></a>Definiowanie klasy priority_buffer

Klasa `priority_buffer` jest niestandardowym typem bloku komunikatów, który porządkuje wiadomości przychodzące najpierw według priorytetu, a następnie według kolejności, w której odbierane są komunikaty. Klasa `priority_buffer` jest podobna do klasy [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) , ponieważ zawiera kolejkę komunikatów, a także ponieważ działa zarówno jako źródło, jak i docelowy blok komunikatów i może mieć wiele źródeł i wiele obiektów docelowych. Niemniej jednak `unbounded_buffer` podstawowe propagowanie komunikatów tylko w kolejności, w której odbierają komunikaty ze źródeł.

Klasa `priority_buffer` odbiera komunikaty typu std::[krotka](../../standard-library/tuple-class.md) , która zawiera elementy `PriorityType` i `Type`. `PriorityType` odnosi się do typu, który posiada priorytet poszczególnych komunikatów; `Type` odnosi się do części danych wiadomości. Klasa `priority_buffer` wysyła komunikaty typu `Type`. Klasa `priority_buffer` zarządza także dwiema kolejkami komunikatów: obiektem [std::p riority_queue](../../standard-library/priority-queue-class.md) dla wiadomości przychodzących i obiektem std::[Queue](../../standard-library/queue-class.md) dla komunikatów wychodzących. Porządkowanie komunikatów według priorytetu jest przydatne, gdy obiekt `priority_buffer` odbiera wiele komunikatów jednocześnie lub odbiera wiele komunikatów przed odczytaniem jakichkolwiek komunikatów przez konsumentów.

Oprócz siedmiu metod, które Klasa, która dziedziczy z `propagator_block` musi implementować, Klasa `priority_buffer` również zastępuje metody `link_target_notification` i `send_message`. Klasa `priority_buffer` definiuje również dwie publiczne metody pomocnika, `enqueue` i `dequeue`oraz prywatną metodę pomocnika, `propagate_priority_order`.

Poniższa procedura opisuje sposób implementacji klasy `priority_buffer`.

#### <a name="to-define-the-priority_buffer-class"></a>Aby zdefiniować klasę priority_buffer

1. Utwórz plik C++ nagłówka i nadaj mu nazwę `priority_buffer.h`. Alternatywnie możesz użyć istniejącego pliku nagłówkowego, który jest częścią projektu.

1. W `priority_buffer.h`Dodaj następujący kod.

[!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. W obszarze nazw `std` Zdefiniuj specjalizacje [std:: less](../../standard-library/less-struct.md) i [std:: większe](../../standard-library/greater-struct.md) , które działają na współbieżności::[Message](../../parallel/concrt/reference/message-class.md) Objects.

[!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   Klasa `priority_buffer` przechowuje obiekty `message` w obiekcie `priority_queue`. Specjalizacje tego typu umożliwiają kolejkom priorytetów sortowanie komunikatów zgodnie z ich priorytetem. Priorytet jest pierwszym elementem obiektu `tuple`.

1. Zadeklaruj klasę `priority_buffer` w przestrzeni nazw `concurrencyex`.

[!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   Klasa `priority_buffer` pochodzi od `propagator_block`. W związku z tym może wysyłać i odbierać wiadomości. Klasa `priority_buffer` może mieć wiele obiektów docelowych, które odbierają komunikaty typu `Type`. Może również mieć wiele źródeł, które wysyłają komunikaty typu `tuple<PriorityType, Type>`.

1. W sekcji `private` klasy `priority_buffer` Dodaj następujące zmienne członkowskie.

[!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   Obiekt `priority_queue` zawiera komunikaty przychodzące; Obiekt `queue` zawiera komunikaty wychodzące. Obiekt `priority_buffer` może odbierać wiele komunikatów jednocześnie. Obiekt `critical_section` synchronizuje dostęp do kolejki komunikatów wejściowych.

1. W sekcji `private` Zdefiniuj Konstruktor kopiujący i operator przypisania. Zapobiega to możliwym przypisaniu obiektów `priority_queue`.

[!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. W sekcji `public` Zdefiniuj konstruktory, które są wspólne dla wielu typów bloku komunikatów. Zdefiniuj także destruktor.

[!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. W sekcji `public` Zdefiniuj metody `enqueue` i `dequeue`. Te metody pomocnika zapewniają alternatywny sposób wysyłania komunikatów do i odbierania komunikatów z obiektu `priority_buffer`.

[!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

9. W sekcji `protected` Zdefiniuj metodę `propagate_to_any_targets`.

[!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   Metoda `propagate_to_any_targets` przesyła komunikat, który znajduje się na wierzchu kolejki wejściowej do kolejki wyjściowej i propaguje wszystkie komunikaty w kolejce wyjściowej.

10. W sekcji `protected` Zdefiniuj metodę `accept_message`.

[!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   Gdy blok docelowy wywołuje metodę `accept_message`, Klasa `priority_buffer` przenosi własność wiadomości do pierwszego bloku docelowego, który go akceptuje. (Przypomina to zachowanie `unbounded_buffer`).

11. W sekcji `protected` Zdefiniuj metodę `reserve_message`.

[!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   Klasa `priority_buffer` pozwala blokowi docelowemu zarezerwować komunikat, gdy podany identyfikator wiadomości jest zgodny z identyfikatorem komunikatu znajdującego się na wierzchu kolejki. Innymi słowy, obiekt docelowy może zarezerwować komunikat, jeśli obiekt `priority_buffer` nie otrzymał jeszcze dodatkowej wiadomości i nie został jeszcze rozpropagowany w bieżącym.

12. W sekcji `protected` Zdefiniuj metodę `consume_message`.

[!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   Blok docelowy wywołuje `consume_message` w celu przeniesienia własności zastrzeżonej wiadomości.

13. W sekcji `protected` Zdefiniuj metodę `release_message`.

[!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   Blok docelowy wywołuje `release_message`, aby anulować jego rezerwację na wiadomość.

14. W sekcji `protected` Zdefiniuj metodę `resume_propagation`.

[!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   Wywołania środowiska uruchomieniowego `resume_propagation` po wykorzystaniu lub wydania zastrzeżonego komunikatu przez blok docelowy. Ta metoda propaguje wszystkie komunikaty znajdujące się w kolejce wyjściowej.

15. W sekcji `protected` Zdefiniuj metodę `link_target_notification`.

[!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   Zmienna członkowska `_M_pReservedFor` jest definiowana przez klasę bazową, `source_block`. Ta zmienna elementu członkowskiego wskazuje blok docelowy (jeśli istnieje), który zawiera rezerwację komunikatu znajdującego się na wierzchu kolejki wyjściowej. Wywołania środowiska uruchomieniowego `link_target_notification`, gdy nowy element docelowy jest połączony z obiektem `priority_buffer`. Ta metoda propaguje wszystkie komunikaty znajdujące się w kolejce wyjściowej, jeśli żaden element docelowy nie utrzymuje rezerwacji.

16. W sekcji `private` Zdefiniuj metodę `propagate_priority_order`.

[!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   Ta metoda propaguje wszystkie komunikaty z kolejki wyjściowej. Każdy komunikat w kolejce jest oferowany każdemu blokowi docelowemu do momentu, gdy jeden z bloków docelowych zaakceptuje komunikat. Klasa `priority_buffer` zachowuje kolejność komunikatów wychodzących. W związku z tym pierwszy komunikat w kolejce wyjściowej musi zostać zaakceptowany przez blok docelowy, zanim ta metoda oferuje inny komunikat do bloków docelowych.

17. W sekcji `protected` Zdefiniuj metodę `propagate_message`.

[!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   Metoda `propagate_message` umożliwia klasy `priority_buffer` działanie jako odbiorca wiadomości lub element docelowy. Ta metoda odbiera komunikat oferowany przez podany blok źródłowy i wstawia ten komunikat do kolejki priorytetowej. Metoda `propagate_message` następnie asynchronicznie wysyła wszystkie komunikaty wyjściowe do bloków docelowych.

   Środowisko uruchomieniowe wywołuje tę metodę podczas wywoływania funkcji [concurrency:: asend](reference/concurrency-namespace-functions.md#asend) lub gdy blok komunikatów jest podłączony do innych bloków komunikatów.

18. W sekcji `protected` Zdefiniuj metodę `send_message`.

[!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   Metoda `send_message` przypomina `propagate_message`. Jednak wysyła komunikaty wyjściowe synchronicznie, zamiast asynchronicznie.

   Środowisko uruchomieniowe wywołuje tę metodę podczas synchronicznej operacji wysyłania, na przykład podczas wywoływania funkcji [concurrency:: Send](reference/concurrency-namespace-functions.md#send) .

Klasa `priority_buffer` zawiera przeciążenia konstruktorów, które są typowe dla wielu typów bloku komunikatów. Niektóre przeciążenia konstruktorów pobierają [współbieżność:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) lub [concurrency:: schedulebinding](../../parallel/concrt/reference/schedulegroup-class.md) Objects, które umożliwiają bloku komunikatów zarządzanie przez określony harmonogram zadań. Inne przeciążenia konstruktorów przyjmują funkcję Filter. Funkcje filtrowania umożliwiają blokom komunikatów akceptowanie lub odrzucanie komunikatów na podstawie ładunku. Aby uzyskać więcej informacji na temat filtrów komunikatów, zobacz [asynchroniczne bloki komunikatów](../../parallel/concrt/asynchronous-message-blocks.md). Aby uzyskać więcej informacji na temat harmonogramów zadań, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Ponieważ Klasa `priority_buffer` porządkuje komunikaty według priorytetu, a następnie według kolejności, w której odbierane są komunikaty, ta klasa jest najbardziej przydatna, gdy odbiera komunikaty asynchronicznie, na przykład w przypadku wywołania funkcji [concurrency:: asend](reference/concurrency-namespace-functions.md#asend) lub gdy blok komunikatów jest podłączony do innych bloków komunikatów.

[[Top](#top)]

## <a name="complete"></a>Kompletny przykład

Poniższy przykład przedstawia pełną definicję klasy `priority_buffer`.

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

Poniższy przykład wykonuje jednocześnie wiele `asend` i [concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) operacji na obiekcie `priority_buffer`.

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe.

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

`priority_buffer` Class porządkuje wiadomości najpierw według priorytetu, a następnie według kolejności, w której odbierają komunikaty. W tym przykładzie komunikaty o większym priorytecie numerycznym są wstawiane do przodu kolejki.

[[Top](#top)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej definicję klasy `priority_buffer` w pliku o nazwie `priority_buffer.h` i programu testowego w pliku o nazwie `priority_buffer.cpp`, a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**CL. exe/EHsc priority_buffer. cpp**

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)
