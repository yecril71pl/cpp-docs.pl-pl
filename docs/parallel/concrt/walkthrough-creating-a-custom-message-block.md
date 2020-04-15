---
title: 'Wskazówki: tworzenie niestandardowego bloku komunikatów'
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: 3386994dce68812cf3ed0852a24d8910cb903acf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368556"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>Wskazówki: tworzenie niestandardowego bloku komunikatów

W tym dokumencie opisano sposób tworzenia niestandardowego typu bloku wiadomości, który zamawia przychodzące wiadomości według priorytetu.

Mimo że wbudowane typy bloków komunikatów zapewniają szeroki zakres funkcji, można utworzyć własny typ bloku wiadomości i dostosować go do wymagań aplikacji. Aby uzyskać opis wbudowanych typów bloków komunikatów dostarczanych przez bibliotekę agentów asynchronicznych, zobacz [Asynchroniczne bloki komunikatów](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego przewodnika przeczytaj następujące dokumenty:

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkcje przekazywania wiadomości](../../parallel/concrt/message-passing-functions.md)

## <a name="sections"></a><a name="top"></a>Sekcje

Ten instruktaż zawiera następujące sekcje:

- [Projektowanie niestandardowego bloku wiadomości](#design)

- [Definiowanie klasy priority_buffer](#class)

- [Kompletny przykład](#complete)

## <a name="designing-a-custom-message-block"></a><a name="design"></a>Projektowanie niestandardowego bloku wiadomości

Bloki wiadomości uczestniczą w akcie wysyłania i odbierania wiadomości. Blok komunikatów, który wysyła wiadomości jest znany jako *blok źródłowy*. Blok komunikatów odbierany przez wiadomości jest nazywany *blokiem docelowym*. Blok komunikatów, który wysyła i odbiera wiadomości jest znany jako *blok propagatora*. Biblioteka agentów używa [współbieżności klasy abstrakcyjnej::ISource](../../parallel/concrt/reference/isource-class.md) do reprezentowania bloków źródłowych i współbieżności klasy abstrakcyjnej::ITarget do [reprezentowania](../../parallel/concrt/reference/itarget-class.md) bloków docelowych. Typy bloków komunikatów, które `ISource`działają jako źródła, pochodzą od ; typy bloków wiadomości, które `ITarget`działają jako obiekty docelowe, pochodzą od .

Chociaż można wyprowadzić typ bloku wiadomości `ISource` `ITarget`bezpośrednio z i , Biblioteka agentów definiuje trzy klasy podstawowe, które wykonują wiele funkcji, które są wspólne dla wszystkich typów bloków komunikatów, na przykład obsługi błędów i łączenia bloków komunikatów razem w sposób bezpieczny dla współbieżności. [Współbieżność::source_block](../../parallel/concrt/reference/source-block-class.md) klasa pochodzi z `ISource` i wysyła wiadomości do innych bloków. [Współbieżność::target_block](../../parallel/concrt/reference/target-block-class.md) klasa pochodzi od `ITarget` i odbiera wiadomości z innych bloków. [Współbieżność::propagator_block](../../parallel/concrt/reference/propagator-block-class.md) klasa pochodzi z `ISource` i `ITarget` wysyła wiadomości do innych bloków i odbiera wiadomości z innych bloków. Zaleca się, aby użyć tych trzech klas podstawowych do obsługi szczegółów infrastruktury, dzięki czemu można skupić się na zachowaniu bloku wiadomości.

Klasy `source_block` `target_block`, `propagator_block` i klasy są szablonami, które są sparametryzowane na typie, który zarządza połączeniami lub łączami, między blokami źródłowymi i docelowymi oraz na typie, który zarządza sposób przetwarzania wiadomości. Biblioteka agentów definiuje dwa typy, które wykonują zarządzanie łączami, [współbieżność::single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) i [współbieżność::multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md). Klasa `single_link_registry` umożliwia bloku wiadomości, które mają być połączone z jednego źródła lub do jednego obiektu docelowego. Klasa `multi_link_registry` umożliwia blok wiadomości, które mają być połączone z wielu źródeł lub wielu obiektów docelowych. Biblioteka agentów definiuje jedną klasę, która wykonuje zarządzanie wiadomościami, [współbieżność::ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md). Klasa `ordered_message_processor` umożliwia bloki wiadomości do przetwarzania wiadomości w kolejności, w jakiej je odbiera.

Aby lepiej zrozumieć, jak bloki wiadomości odnoszą się do ich źródeł i obiektów docelowych, należy wziąć pod uwagę poniższy przykład. W tym przykładzie pokazano deklarację [współbieżności::transformator](../../parallel/concrt/reference/transformer-class.md) klasy.

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

Klasa `transformer` pochodzi od `propagator_block`, i dlatego działa zarówno jako blok źródłowy i jako blok docelowy. Akceptuje wiadomości typu `_Input` i wysyła wiadomości `_Output`typu . Klasa `transformer` określa `single_link_registry` jako menedżera łączy dla wszystkich `multi_link_registry` bloków docelowych i jako menedżera łączy dla wszystkich bloków źródłowych. W związku `transformer` z tym obiekt może mieć maksymalnie jeden obiekt docelowy i nieograniczoną liczbę źródeł.

Klasa, która wywodzi się z `source_block` musi wdrożyć sześć metod: [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets), [accept_message](reference/source-block-class.md#accept_message), [reserve_message](reference/source-block-class.md#reserve_message), [consume_message](reference/source-block-class.md#consume_message), [release_message](reference/source-block-class.md#release_message)i [resume_propagation](reference/source-block-class.md#resume_propagation). Klasa, która wywodzi się z `target_block` musi implementować [propagate_message](reference/propagator-block-class.md#propagate_message) metody i opcjonalnie można zaimplementować [send_message](reference/propagator-block-class.md#send_message) metody. Wyprowadzenie z `propagator_block` jest funkcjonalnie `source_block` `target_block`równoważne wyprowadzeniu zarówno z .

Metoda `propagate_to_any_targets` jest wywoływana przez środowisko wykonawcze do asynchronicznie lub synchronicznie przetwarzać wszystkie przychodzące wiadomości i propagować wszelkie wiadomości wychodzące. Metoda `accept_message` jest wywoływana przez bloki docelowe do akceptowania wiadomości. Wiele typów bloków wiadomości, takich jak `unbounded_buffer`, wysyłać wiadomości tylko do pierwszego obiektu docelowego, który będzie otrzymywać go. W związku z tym przenosi własność wiadomości do obiektu docelowego. Inne typy bloków komunikatów, takie jak [współbieżność::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md), oferują wiadomości do każdego z bloków docelowych. W związku `overwrite_buffer` z tym tworzy kopię wiadomości dla każdego z jego obiektów docelowych.

, `reserve_message` `consume_message`, `release_message`i `resume_propagation` metody umożliwiają blokom wiadomości uczestnictwo w rezerwacji wiadomości. Bloki docelowe `reserve_message` wywołać metodę, gdy są one oferowane wiadomości i muszą zarezerwować wiadomość do późniejszego użycia. Po bloku docelowego rezerwuje wiadomość, `consume_message` można wywołać metodę, `release_message` aby korzystać z tej wiadomości lub metody, aby anulować rezerwację. Podobnie jak `accept_message` w przypadku `consume_message` metody, implementacja może przenieść własność wiadomości lub zwrócić kopię wiadomości. Po bloku docelowego zużywa lub zwalnia zarezerwowany komunikat, środowisko `resume_propagation` uruchomieniowe wywołuje metodę. Zazwyczaj ta metoda kontynuuje propagację wiadomości, począwszy od następnej wiadomości w kolejce.

Środowisko wykonawcze `propagate_message` wywołuje metodę asynchronicznie przenieść wiadomość z innego bloku do bieżącego. Metoda `send_message` przypomina `propagate_message`, z tą różnicą, że synchronicznie, zamiast asynchronicznie, wysyła wiadomość do bloków docelowych. Domyślna implementacja `send_message` odrzuca wszystkie przychodzące wiadomości. Środowisko wykonawcze nie wywoła żadnej z tych metod, jeśli komunikat nie przekazuje opcjonalnej funkcji filtrowania skojarzonej z blokiem docelowym. Aby uzyskać więcej informacji na temat filtrów wiadomości, zobacz [Asynchroniczne bloki wiadomości](../../parallel/concrt/asynchronous-message-blocks.md).

[[Góra](#top)]

## <a name="defining-the-priority_buffer-class"></a><a name="class"></a>Definiowanie klasy priority_buffer

Klasa `priority_buffer` jest niestandardowym typem bloku wiadomości, który zamawia przychodzące wiadomości najpierw według priorytetu, a następnie według kolejności, w jakiej wiadomości są odbierane. Klasa `priority_buffer` przypomina [współbieżność::unbounded_buffer](reference/unbounded-buffer-class.md) klasy, ponieważ zawiera kolejkę wiadomości, a także dlatego, że działa zarówno jako źródło i docelowy blok komunikatów i może mieć zarówno wiele źródeł, jak i wiele obiektów docelowych. Jednak `unbounded_buffer` propagacja wiadomości opiera się tylko na kolejności, w jakiej odbiera wiadomości ze swoich źródeł.

Klasa `priority_buffer` odbiera komunikaty typu std::[krotka,](../../standard-library/tuple-class.md) które zawierają `PriorityType` i `Type` elementy. `PriorityType`odnosi się do typu, który ma priorytet każdej wiadomości; `Type` odnosi się do części danych wiadomości. Klasa `priority_buffer` wysyła wiadomości `Type`typu . Klasa `priority_buffer` zarządza również dwie kolejki komunikatów: [std::priority_queue](../../standard-library/priority-queue-class.md) obiektu dla wiadomości przychodzących i std::[obiekt kolejki](../../standard-library/queue-class.md) dla wiadomości wychodzących. Zamawianie wiadomości według priorytetu `priority_buffer` jest przydatne, gdy obiekt odbiera wiele wiadomości jednocześnie lub gdy odbiera wiele wiadomości, zanim jakiekolwiek wiadomości są odczytywane przez konsumentów.

Oprócz siedmiu metod, które klasa, która `propagator_block` wywodzi się z musi implementować, `priority_buffer` klasa zastępuje również `link_target_notification` i `send_message` metody. Klasa `priority_buffer` definiuje również dwie metody pomocy `enqueue` `dequeue`publicznej oraz metodę prywatnego `propagate_priority_order`pomocnika.

W poniższej procedurze `priority_buffer` opisano sposób implementacji klasy.

#### <a name="to-define-the-priority_buffer-class"></a>Aby zdefiniować klasę priority_buffer

1. Utwórz plik nagłówka języka `priority_buffer.h`C++ i nadaj jego nazwę . Alternatywnie można użyć istniejącego pliku nagłówka, który jest częścią projektu.

1. W `priority_buffer.h`, dodaj następujący kod.

    [!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. W `std` obszarze nazw zdefiniuj specjalizacje [std::less](../../standard-library/less-struct.md) i [std::greater,](../../standard-library/greater-struct.md) które działają na współbieżność:: obiekty[wiadomości.](../../parallel/concrt/reference/message-class.md)

    [!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   Klasa `priority_buffer` przechowuje `message` obiekty `priority_queue` w obiekcie. Te specjalizacje typu umożliwiają kolejki priorytetów sortowanie wiadomości zgodnie z ich priorytetem. Priorytet jest pierwszym elementem `tuple` obiektu.

1. W `concurrencyex` obszarze nazw zadeklarować `priority_buffer` klasę.

    [!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   Klasa `priority_buffer` wywodzi się od `propagator_block`. W związku z tym może zarówno wysyłać i odbierać wiadomości. Klasa `priority_buffer` może mieć wiele obiektów docelowych, które odbierają wiadomości typu `Type`. Może również mieć wiele źródeł, które `tuple<PriorityType, Type>`wysyłają wiadomości typu .

1. W `private` sekcji `priority_buffer` klasy dodaj następujące zmienne członkowskie.

    [!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   Obiekt `priority_queue` przechowuje przychodzące wiadomości; obiekt `queue` przechowuje wiadomości wychodzące. Obiekt `priority_buffer` może odbierać wiele wiadomości jednocześnie; `critical_section` obiekt synchronizuje dostęp do kolejki komunikatów wejściowych.

1. W `private` sekcji zdefiniuj konstruktor kopii i operator przypisania. Zapobiega to `priority_queue` możliwością przypisania obiektów.

    [!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. W `public` sekcji zdefiniuj konstruktory, które są wspólne dla wielu typów bloków komunikatów. Zdefiniuj również destruktora.

    [!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. W `public` sekcji zdefiniuj metody `enqueue` i `dequeue`. Te metody pomocnicze zapewniają alternatywny sposób wysyłania wiadomości `priority_buffer` do i odbierania wiadomości z obiektu.

    [!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

1. W `protected` sekcji zdefiniuj `propagate_to_any_targets` metodę.

    [!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   Metoda `propagate_to_any_targets` przenosi komunikat, który znajduje się z przodu kolejki wejściowej do kolejki wyjściowej i propaguje wszystkie komunikaty w kolejce wyjściowej.

1. W `protected` sekcji zdefiniuj `accept_message` metodę.

    [!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   Gdy blok docelowy `accept_message` wywołuje `priority_buffer` metodę, klasa przenosi własność wiadomości do pierwszego bloku docelowego, który ją akceptuje. (Przypomina to zachowanie `unbounded_buffer`.)

1. W `protected` sekcji zdefiniuj `reserve_message` metodę.

    [!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   Klasa `priority_buffer` zezwala blok docelowy zarezerwować wiadomość, gdy podany identyfikator wiadomości pasuje do identyfikatora wiadomości, która znajduje się na froncie kolejki. Innymi słowy obiekt docelowy może zarezerwować `priority_buffer` wiadomość, jeśli obiekt nie otrzymał jeszcze dodatkowej wiadomości i nie propagował jeszcze bieżącego.

1. W `protected` sekcji zdefiniuj `consume_message` metodę.

    [!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   Blok docelowy `consume_message` wywołuje przeniesienie własności wiadomości, która została zarezerwowana.

1. W `protected` sekcji zdefiniuj `release_message` metodę.

    [!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   Blok docelowy `release_message` wywołuje anulowanie rezerwacji do wiadomości.

1. W `protected` sekcji zdefiniuj `resume_propagation` metodę.

    [!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   Wywołanie `resume_propagation` środowiska uruchomieniowego po bloku docelowym zużywa lub zwalnia zarezerwowany komunikat. Ta metoda propaguje wszystkie komunikaty, które znajdują się w kolejce wyjściowej.

1. W `protected` sekcji zdefiniuj `link_target_notification` metodę.

    [!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   Zmienna `_M_pReservedFor` elementu członkowskiego jest definiowana przez klasę podstawową . `source_block` Ta zmienna elementu członkowskiego wskazuje blok docelowy, jeśli istnieje, który przechowuje rezerwację do wiadomości, która znajduje się z przodu kolejki wyjściowej. Środowisko uruchomieniowe wywołuje, `link_target_notification` gdy nowy `priority_buffer` obiekt docelowy jest połączony z obiektem. Ta metoda propaguje wszystkie komunikaty, które znajdują się w kolejce wyjściowej, jeśli żaden obiekt docelowy nie przechowuje rezerwacji.

1. W `private` sekcji zdefiniuj `propagate_priority_order` metodę.

    [!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   Ta metoda propaguje wszystkie komunikaty z kolejki wyjściowej. Każda wiadomość w kolejce jest oferowana do każdego bloku docelowego, dopóki jeden z bloków docelowych nie zaakceptuje wiadomości. Klasa `priority_buffer` zachowuje kolejność wiadomości wychodzących. W związku z tym pierwszy komunikat w kolejce wyjściowej musi być zaakceptowany przez blok docelowy, zanim ta metoda oferuje inny komunikat do bloków docelowych.

1. W `protected` sekcji zdefiniuj `propagate_message` metodę.

    [!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   Metoda `propagate_message` umożliwia `priority_buffer` klasy działać jako odbiornik wiadomości lub miejsce docelowe. Ta metoda odbiera komunikat, który jest oferowany przez podany blok źródłowy i wstawia tę wiadomość do kolejki priorytetu. Metoda `propagate_message` następnie asynchronicznie wysyła wszystkie komunikaty wyjściowe do bloków docelowych.

   Środowisko wykonawcze wywołuje tę metodę podczas [wywoływania funkcji współbieżności::asend](reference/concurrency-namespace-functions.md#asend) lub gdy blok komunikatów jest połączony z innymi blokami komunikatów.

1. W `protected` sekcji zdefiniuj `send_message` metodę.

    [!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   Metoda `send_message` przypomina `propagate_message`. Jednak wysyła komunikaty wyjściowe synchronicznie zamiast asynchronicznie.

   Środowisko wykonawcze wywołuje tę metodę podczas operacji synchroniczne wysyłanie, na przykład podczas [wywoływania współbieżności::send](reference/concurrency-namespace-functions.md#send) funkcji.

Klasa `priority_buffer` zawiera przeciążenia konstruktora, które są typowe w wielu typach bloków komunikatów. Niektóre przeciążenia konstruktora wziąć [współbieżność::Harmonogram](../../parallel/concrt/reference/scheduler-class.md) lub [współbieżności::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) obiektów, które umożliwiają blok komunikatów, które mają być zarządzane przez określonego harmonogramu zadań. Inne przeciążenia konstruktora wziąć funkcję filtru. Funkcje filtrowania umożliwiają blokom wiadomości akceptowanie lub odrzucanie wiadomości na podstawie jej ładunku. Aby uzyskać więcej informacji na temat filtrów wiadomości, zobacz [Asynchroniczne bloki wiadomości](../../parallel/concrt/asynchronous-message-blocks.md). Aby uzyskać więcej informacji o harmonogramach zadań, zobacz [Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Ponieważ `priority_buffer` klasa porządkuje wiadomości według priorytetu, a następnie według kolejności, w jakiej wiadomości są odbierane, ta klasa jest najbardziej przydatne, gdy odbiera wiadomości asynchronicznie, na przykład podczas [wywoływania funkcji współbieżności::asend](reference/concurrency-namespace-functions.md#asend) lub gdy blok wiadomości jest podłączony do innych bloków wiadomości.

[[Góra](#top)]

## <a name="the-complete-example"></a><a name="complete"></a>Kompletny przykład

Poniższy przykład przedstawia pełną `priority_buffer` definicję klasy.

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

Poniższy przykład jednocześnie wykonuje liczbę `asend` i [współbieżności::receive](reference/concurrency-namespace-functions.md#receive) operacji `priority_buffer` na obiekcie.

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

W tym przykładzie tworzy następujące dane wyjściowe próbki.

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

Klasa `priority_buffer` zamawia wiadomości najpierw według priorytetu, a następnie według kolejności, w jakiej odbiera wiadomości. W tym przykładzie wiadomości o większym priorytecie liczbowym są wstawiane do przodu kolejki.

[[Góra](#top)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie `priority_buffer` programu Visual Studio `priority_buffer.h` lub wklej definicję klasy `priority_buffer.cpp` w pliku o nazwie i programu testowego w pliku o nazwie, a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**cl.exe /EHsc priority_buffer.cpp**

## <a name="see-also"></a>Zobacz też

[Wskazówki dotyczące środowiska uruchomieniowego współbieżności](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania wiadomości](../../parallel/concrt/message-passing-functions.md)
