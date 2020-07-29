---
title: 'Wskazówki: tworzenie niestandardowego bloku komunikatów'
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: f95eaf7e1da41bd473ab15d12330d0177b98ccdf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219498"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>Wskazówki: tworzenie niestandardowego bloku komunikatów

W tym dokumencie opisano sposób tworzenia niestandardowego typu bloku komunikatów, który porządkuje komunikaty przychodzące według priorytetu.

Chociaż wbudowane typy bloków komunikatów zapewniają szeroką gamę funkcji, można utworzyć własny typ bloku komunikatów i dostosować go do wymagań aplikacji. Aby uzyskać opis wbudowanych typów bloków komunikatów, które są dostarczane przez bibliotekę agentów asynchronicznych, zobacz [asynchroniczne bloki komunikatów](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu zapoznaj się z następującymi dokumentami:

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)

## <a name="sections"></a><a name="top"></a>Poszczególne

Ten Instruktaż zawiera następujące sekcje:

- [Projektowanie niestandardowego bloku komunikatów](#design)

- [Definiowanie klasy priority_buffer](#class)

- [Kompletny przykład](#complete)

## <a name="designing-a-custom-message-block"></a><a name="design"></a>Projektowanie niestandardowego bloku komunikatów

Bloki komunikatów uczestniczą w wysyłaniu i otrzymywaniu komunikatów. Blok komunikatów, który wysyła wiadomości jest znany jako *blok źródłowy*. Blok komunikatów, który odbiera wiadomości jest znany jako *blok docelowy*. Blok komunikatów, który wysyła i odbiera wiadomości jest znany jako *blok propagacji*. Biblioteka agentów używa klasy abstrakcyjnej [concurrency:: ISource](../../parallel/concrt/reference/isource-class.md) do reprezentowania bloków źródłowych i abstrakcyjnej klasy [concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md) do reprezentowania bloków docelowych. Typy bloku komunikatów, które działają jako źródła pochodzą z `ISource` ; typy bloku komunikatów, które działają jako elementy docelowe pochodne `ITarget` .

Chociaż można utworzyć typ bloku wiadomości bezpośrednio z `ISource` i `ITarget` , biblioteka agenci definiuje trzy klasy bazowe, które wykonują wiele funkcji wspólnych dla wszystkich typów bloku komunikatów, na przykład obsługa błędów i łączenie bloków komunikatów ze sobą w sposób bezpieczny dla współbieżności. Klasa [concurrency:: source_block](../../parallel/concrt/reference/source-block-class.md) dziedziczy z `ISource` i wysyła komunikaty do innych bloków. Klasa [concurrency:: target_block](../../parallel/concrt/reference/target-block-class.md) dziedziczy z `ITarget` i odbiera komunikaty z innych bloków. Klasa [concurrency::p ropagator_block](../../parallel/concrt/reference/propagator-block-class.md) dziedziczy z `ISource` i `ITarget` i wysyła komunikaty do innych bloków i odbiera komunikaty z innych bloków. Zalecamy używanie tych trzech klas bazowych do obsługi szczegółów infrastruktury, aby można było skupić się na zachowaniu bloku komunikatów.

`source_block`Klasy, `target_block` i `propagator_block` są szablonami, które są sparametryzowane na typie, który zarządza połączeniami lub łączami, między blokami źródłowymi i docelowymi oraz na typie, który zarządza sposobem przetwarzania komunikatów. Biblioteka agenci definiuje dwa typy, które wykonują zarządzanie linkami, [concurrency:: single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) i [concurrency:: multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md). `single_link_registry`Klasa umożliwia połączenie bloku komunikatów z jednym źródłem lub jednym obiektem docelowym. `multi_link_registry`Klasa umożliwia połączenie bloku komunikatów z wieloma źródłami lub wieloma obiektami docelowymi. Biblioteka agenci definiuje jedną klasę, która wykonuje zarządzanie komunikatami [concurrency:: ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md). `ordered_message_processor`Klasa umożliwia blokom komunikatów przetwarzanie komunikatów w kolejności, w jakiej je odbiera.

Aby lepiej zrozumieć sposób, w jaki bloki komunikatów odnoszą się do ich źródeł i elementów docelowych, weź pod uwagę Poniższy przykład. Ten przykład pokazuje deklarację klasy [concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) .

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

`transformer`Klasa pochodzi od `propagator_block` i w związku z tym działa jako blok źródłowy i jako blok docelowy. Akceptuje komunikaty typu `_Input` i wysyła komunikaty typu `_Output` . `transformer`Klasa określa `single_link_registry` jako Menedżera linków dla dowolnych bloków docelowych oraz `multi_link_registry` jako Menedżera linków dla bloków źródłowych. W związku z tym `transformer` obiekt może mieć maksymalnie jeden obiekt docelowy i nieograniczoną liczbę źródeł.

Klasa, która pochodzi z `source_block` musi zaimplementować sześć metod: [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets), [accept_message](reference/source-block-class.md#accept_message), [reserve_message](reference/source-block-class.md#reserve_message), [consume_message](reference/source-block-class.md#consume_message), [release_message](reference/source-block-class.md#release_message)i [resume_propagation](reference/source-block-class.md#resume_propagation). Klasa, która dziedziczy z `target_block` musi implementować metodę [propagate_message](reference/propagator-block-class.md#propagate_message) i opcjonalnie może zaimplementować metodę [send_message](reference/propagator-block-class.md#send_message) . Wyprowadzanie z `propagator_block` jest funkcjonalnie równoważne z pochodną obu `source_block` i `target_block` .

`propagate_to_any_targets`Metoda jest wywoływana przez środowisko uruchomieniowe w celu asynchronicznego lub synchronicznego przetwarzania wszelkich komunikatów przychodzących i propagowania wszelkich wychodzących komunikatów. `accept_message`Metoda jest wywoływana przez bloki docelowe w celu akceptowania komunikatów. Wiele typów bloku komunikatów, takich jak `unbounded_buffer` , wysyła komunikaty tylko do pierwszego obiektu docelowego, który otrzyma go. W związku z tym przenosi własność wiadomości do obiektu docelowego. Inne typy bloku komunikatów, takie jak [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md), oferują komunikaty do każdego z jego bloków docelowych. W związku z tym program `overwrite_buffer` tworzy kopię wiadomości dla każdego z jej obiektów docelowych.

`reserve_message`Metody, `consume_message` , `release_message` i `resume_propagation` umożliwiają blokom komunikatów uczestniczenie w rezerwacji komunikatów. Bloki docelowe wywołują `reserve_message` metodę, gdy są oferowane przez nich komunikat i muszą zarezerwować komunikat do późniejszego użycia. Gdy blok docelowy rezerwuje komunikat, może wywołać `consume_message` metodę, aby użyć tego komunikatu, lub metodę, `release_message` Aby anulować rezerwację. Podobnie jak w przypadku `accept_message` metody, implementacja programu `consume_message` może przenieść własność wiadomości lub zwrócić kopię wiadomości. Gdy blok docelowy zużywa lub zwalnia zastrzeżony komunikat, środowisko uruchomieniowe wywołuje `resume_propagation` metodę. Zazwyczaj ta metoda kontynuuje propagację komunikatów, rozpoczynając od następnej wiadomości w kolejce.

Środowisko uruchomieniowe wywołuje `propagate_message` metodę, aby asynchronicznie przenieść komunikat z innego bloku do bieżącego. `send_message`Metoda przypomina `propagate_message` , z tą różnicą, że synchronicznie zamiast asynchronicznie wysyła komunikat do bloków docelowych. Domyślna implementacja programu `send_message` odrzuca wszystkie wiadomości przychodzące. Środowisko uruchomieniowe nie wywołuje żadnej z tych metod, jeśli komunikat nie przeszedł opcjonalnej funkcji filtru, która jest skojarzona z blokiem docelowym. Aby uzyskać więcej informacji na temat filtrów komunikatów, zobacz [asynchroniczne bloki komunikatów](../../parallel/concrt/asynchronous-message-blocks.md).

[[Top](#top)]

## <a name="defining-the-priority_buffer-class"></a><a name="class"></a>Definiowanie klasy priority_buffer

`priority_buffer`Klasa jest niestandardowym typem bloku komunikatów, który porządkuje wiadomości przychodzące najpierw według priorytetu, a następnie według kolejności, w której odbierane są komunikaty. `priority_buffer`Klasa jest podobna do klasy [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) , ponieważ zawiera kolejkę komunikatów, a także ponieważ działa zarówno jako źródło, jak i docelowy blok komunikatów i może mieć wiele źródeł i wiele obiektów docelowych. Jednak podstawowe `unbounded_buffer` propagowanie komunikatów dotyczy tylko kolejności, w której odbierają komunikaty ze źródeł.

`priority_buffer`Klasa odbiera komunikaty typu std::[krotka](../../standard-library/tuple-class.md) , która zawiera `PriorityType` `Type` elementy i. `PriorityType`odnosi się do typu, który posiada priorytet poszczególnych komunikatów; `Type`odwołuje się do części danych wiadomości. `priority_buffer`Klasa wysyła komunikaty typu `Type` . `priority_buffer`Klasa zarządza również dwiema kolejkami komunikatów: obiektu [std::p riority_queue](../../standard-library/priority-queue-class.md) dla wiadomości przychodzących i obiektu std::[Queue](../../standard-library/queue-class.md) dla komunikatów wychodzących. Porządkowanie komunikatów według priorytetu jest przydatne, gdy `priority_buffer` obiekt odbiera wiele komunikatów jednocześnie lub odbiera wiele komunikatów przed odczytaniem jakichkolwiek komunikatów przez odbiorców.

Oprócz siedmiu metod, których Klasa dziedziczy z `propagator_block` musi implementować, `priority_buffer` Klasa również zastępuje `link_target_notification` `send_message` metody i. `priority_buffer`Klasa definiuje również dwie publiczne metody pomocnika, `enqueue` i `dequeue` i prywatną metodę pomocnika `propagate_priority_order` .

Poniższa procedura opisuje sposób implementacji `priority_buffer` klasy.

#### <a name="to-define-the-priority_buffer-class"></a>Aby zdefiniować klasę priority_buffer

1. Utwórz plik nagłówka C++ i nadaj mu nazwę `priority_buffer.h` . Alternatywnie możesz użyć istniejącego pliku nagłówkowego, który jest częścią projektu.

1. W programie `priority_buffer.h` Dodaj następujący kod.

    [!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. W `std` obszarze nazw Zdefiniuj specjalizacje [std:: less](../../standard-library/less-struct.md) i [std:: większe](../../standard-library/greater-struct.md) , które działają na współbieżności::[Message](../../parallel/concrt/reference/message-class.md) Objects.

    [!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   `priority_buffer`Klasa przechowuje `message` obiekty w `priority_queue` obiekcie. Specjalizacje tego typu umożliwiają kolejkom priorytetów sortowanie komunikatów zgodnie z ich priorytetem. Priorytet jest pierwszym elementem `tuple` obiektu.

1. W `concurrencyex` przestrzeni nazw Zadeklaruj `priority_buffer` klasę.

    [!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   `priority_buffer`Klasa pochodzi od `propagator_block` . W związku z tym może wysyłać i odbierać wiadomości. `priority_buffer`Klasa może mieć wiele obiektów docelowych, które odbierają komunikaty typu `Type` . Może również mieć wiele źródeł, które wysyłają komunikaty typu `tuple<PriorityType, Type>` .

1. W **`private`** sekcji `priority_buffer` klasy Dodaj następujące zmienne członkowskie.

    [!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   `priority_queue`Obiekt przechowuje komunikaty przychodzące; `queue` obiekt zawiera komunikaty wychodzące. `priority_buffer`Obiekt może odbierać wiele komunikatów jednocześnie; `critical_section` obiekt synchronizuje dostęp do kolejki komunikatów wejściowych.

1. W **`private`** sekcji Zdefiniuj Konstruktor kopiujący i operator przypisania. Uniemożliwia to `priority_queue` przypisanie obiektów.

    [!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. W **`public`** sekcji Zdefiniuj konstruktory, które są wspólne dla wielu typów bloku komunikatów. Zdefiniuj także destruktor.

    [!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. W **`public`** sekcji Zdefiniuj metody `enqueue` i `dequeue` . Te metody pomocnika zapewniają alternatywny sposób wysyłania komunikatów do i odbierania komunikatów z `priority_buffer` obiektu.

    [!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

1. W **`protected`** sekcji Zdefiniuj `propagate_to_any_targets` metodę.

    [!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   `propagate_to_any_targets`Metoda przenosi komunikat, który znajduje się na początku kolejki wejściowej, do kolejki wyjściowej i propaguje wszystkie komunikaty w kolejce wyjściowej.

1. W **`protected`** sekcji Zdefiniuj `accept_message` metodę.

    [!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   Gdy blok docelowy wywołuje `accept_message` metodę, `priority_buffer` Klasa przenosi własność wiadomości do pierwszego bloku docelowego, który go akceptuje. (Przypomina to zachowanie `unbounded_buffer` .)

1. W **`protected`** sekcji Zdefiniuj `reserve_message` metodę.

    [!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   `priority_buffer`Klasa pozwala blokowi docelowemu zarezerwować komunikat, gdy podany identyfikator wiadomości jest zgodny z identyfikatorem komunikatu znajdującego się na wierzchu kolejki. Innymi słowy, obiekt docelowy może zarezerwować wiadomość, jeśli `priority_buffer` obiekt nie otrzymał jeszcze dodatkowej wiadomości i nie został jeszcze rozpropagowany w bieżącym.

1. W **`protected`** sekcji Zdefiniuj `consume_message` metodę.

    [!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   Blok docelowy wywołuje `consume_message` przekazanie własności zastrzeżonej wiadomości.

1. W **`protected`** sekcji Zdefiniuj `release_message` metodę.

    [!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   Blok docelowy wywołuje, `release_message` Aby anulować jego rezerwację na wiadomość.

1. W **`protected`** sekcji Zdefiniuj `resume_propagation` metodę.

    [!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   Wywołania środowiska uruchomieniowego `resume_propagation` po bloku docelowym zużywają lub zwalniają zastrzeżony komunikat. Ta metoda propaguje wszystkie komunikaty znajdujące się w kolejce wyjściowej.

1. W **`protected`** sekcji Zdefiniuj `link_target_notification` metodę.

    [!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   `_M_pReservedFor`Zmienna członkowska jest definiowana przez klasę bazową `source_block` . Ta zmienna elementu członkowskiego wskazuje blok docelowy (jeśli istnieje), który zawiera rezerwację komunikatu znajdującego się na wierzchu kolejki wyjściowej. Wywołania środowiska uruchomieniowego, `link_target_notification` gdy nowy element docelowy jest połączony z `priority_buffer` obiektem. Ta metoda propaguje wszystkie komunikaty znajdujące się w kolejce wyjściowej, jeśli żaden element docelowy nie utrzymuje rezerwacji.

1. W **`private`** sekcji Zdefiniuj `propagate_priority_order` metodę.

    [!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   Ta metoda propaguje wszystkie komunikaty z kolejki wyjściowej. Każdy komunikat w kolejce jest oferowany każdemu blokowi docelowemu do momentu, gdy jeden z bloków docelowych zaakceptuje komunikat. `priority_buffer`Klasa zachowuje kolejność komunikatów wychodzących. W związku z tym pierwszy komunikat w kolejce wyjściowej musi zostać zaakceptowany przez blok docelowy, zanim ta metoda oferuje inny komunikat do bloków docelowych.

1. W **`protected`** sekcji Zdefiniuj `propagate_message` metodę.

    [!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   `propagate_message`Metoda umożliwia `priority_buffer` klasie działanie jako odbiorca wiadomości lub element docelowy. Ta metoda odbiera komunikat oferowany przez podany blok źródłowy i wstawia ten komunikat do kolejki priorytetowej. `propagate_message`Następnie metoda asynchronicznie wysyła wszystkie komunikaty wyjściowe do bloków docelowych.

   Środowisko uruchomieniowe wywołuje tę metodę podczas wywoływania funkcji [concurrency:: asend](reference/concurrency-namespace-functions.md#asend) lub gdy blok komunikatów jest podłączony do innych bloków komunikatów.

1. W **`protected`** sekcji Zdefiniuj `send_message` metodę.

    [!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   `send_message`Metoda jest podobna `propagate_message` . Jednak wysyła komunikaty wyjściowe synchronicznie, zamiast asynchronicznie.

   Środowisko uruchomieniowe wywołuje tę metodę podczas synchronicznej operacji wysyłania, na przykład podczas wywoływania funkcji [concurrency:: Send](reference/concurrency-namespace-functions.md#send) .

`priority_buffer`Klasa zawiera przeciążenia konstruktorów, które są typowe w wielu typach bloku komunikatów. Niektóre przeciążenia konstruktorów pobierają [współbieżność:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) lub [concurrency:: schedulebinding](../../parallel/concrt/reference/schedulegroup-class.md) Objects, które umożliwiają bloku komunikatów zarządzanie przez określony harmonogram zadań. Inne przeciążenia konstruktorów przyjmują funkcję Filter. Funkcje filtrowania umożliwiają blokom komunikatów akceptowanie lub odrzucanie komunikatów na podstawie ładunku. Aby uzyskać więcej informacji na temat filtrów komunikatów, zobacz [asynchroniczne bloki komunikatów](../../parallel/concrt/asynchronous-message-blocks.md). Aby uzyskać więcej informacji na temat harmonogramów zadań, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Ponieważ `priority_buffer` Klasa porządkuje komunikaty według priorytetu, a następnie według kolejności, w której odbierane są komunikaty, ta klasa jest najbardziej przydatna, gdy odbiera komunikaty asynchronicznie, na przykład w przypadku wywołania funkcji [concurrency:: asend](reference/concurrency-namespace-functions.md#asend) lub gdy blok komunikatów jest podłączony do innych bloków komunikatów.

[[Top](#top)]

## <a name="the-complete-example"></a><a name="complete"></a>Kompletny przykład

Poniższy przykład przedstawia pełną definicję `priority_buffer` klasy.

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

Poniższy przykład wykonuje jednocześnie wiele `asend` operacji i [współbieżność:: Receive](reference/concurrency-namespace-functions.md#receive) na `priority_buffer` obiekcie.

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe.

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

`priority_buffer`Klasa porządkuje wiadomości najpierw według priorytetu, a następnie według kolejności, w której odbierają komunikaty. W tym przykładzie komunikaty o większym priorytecie numerycznym są wstawiane do przodu kolejki.

[[Top](#top)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej definicję `priority_buffer` klasy w pliku o nazwie `priority_buffer.h` i programu testowego w pliku o nazwie, `priority_buffer.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**cl.exe/EHsc priority_buffer. cpp**

## <a name="see-also"></a>Zobacz także

[Instruktaże środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)
