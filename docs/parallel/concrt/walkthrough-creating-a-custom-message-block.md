---
title: "Wskazówki: Tworzenie niestandardowego bloku komunikatów | Dokumentacja firmy Microsoft"
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
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9ff7dd60dbb91d88377f481510ea0e213f18098a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-creating-a-custom-message-block"></a>Wskazówki: tworzenie niestandardowego bloku komunikatów
Ten dokument zawiera opis sposobu tworzenia komunikat niestandardowy typ bloku, któremu porządkuje komunikaty przychodzące według priorytetu.  
  
 Mimo że typów bloku komunikatów wbudowane zapewniają szerokiego zakresu funkcji, można utworzyć własny typ bloku komunikatów i dostosować go do wymagań aplikacji. Opis typów bloku wbudowanych wiadomości, które są udostępniane przez biblioteki agentów asynchronicznych, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przeczytaj następujące dokumenty przed skorzystaniem z tego przewodnika:  
  
- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)  
  
- [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)  
  
##  <a name="top"></a>Sekcje  
 Ten przewodnik zawiera następujące sekcje:  
  
- [Projektowanie niestandardowego bloku komunikatów](#design)  
  
- [Definiowanie priority_buffer — klasa](#class)  
  
- [Pełny przykład](#complete)  
  
##  <a name="design"></a>Projektowanie niestandardowego bloku komunikatów  
 Bloki komunikatów uczestniczyć w czynność wysyłania i odbierania wiadomości. Blok komunikatów, który wysyła wiadomości jest nazywany *bloku źródłowego*. Blok komunikatów, który odbiera komunikaty nosi nazwę *blok docelowy*. Blok komunikatów, który zarówno wysyła i odbiera komunikaty nosi nazwę *bloku propagator*. Biblioteki agentów korzysta z klasy abstrakcyjnej [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) do reprezentowania bloków źródła i klasa abstrakcyjna [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) do reprezentowania bloki docelowej. Blok komunikatów typy tej czynności, jak źródeł pochodzi od `ISource`; bloku komunikatów typy tej czynności jako obiekty docelowe pochodzi od `ITarget`.  
  
 Mimo że może pochodzić z typ bloku komunikatów bezpośrednio z `ISource` i `ITarget`, biblioteka agentów definiuje trzy klas podstawowych, które wykonywać podobne funkcje, które są wspólne dla wszystkich typów bloku komunikatów, na przykład obsługa błędów i łączenie bloków komunikatów w sposób bezpieczny współbieżności. [Concurrency::source_block](../../parallel/concrt/reference/source-block-class.md) pochodną klasy `ISource` i wysyła wiadomości do innych bloków. [Concurrency::target_block](../../parallel/concrt/reference/target-block-class.md) pochodną klasy `ITarget` i odbiera komunikaty z innych bloków. [Concurrency::propagator_block](../../parallel/concrt/reference/propagator-block-class.md) pochodną klasy `ISource` i `ITarget` i wysyła wiadomości do innych bloków i odbiera komunikaty z innych bloków. Zalecane jest użycie tych trzech klas podstawowych do obsługi infrastruktury szczegóły, dzięki czemu można skupić się na zachowanie z bloku komunikatów.  
  
 `source_block`, `target_block`, I `propagator_block` klasy są szablony, które mają zdefiniowane na typ, który zarządza połączeniami lub łączy, między źródłowa i docelowa bloków oraz na typ, który zarządza, przetwarzanie wiadomości. Biblioteki agentów definiują dwa typy, wykonujących zarządzania łącze [concurrency::single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) i [concurrency::multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md). `single_link_registry` Klasa umożliwia blok komunikat mógł być połączone z jednego źródła lub jeden obiekt docelowy. `multi_link_registry` Klasa umożliwia bloku komunikatów być połączone z wielu źródeł lub wielu elementów docelowych. Biblioteki agentów definiuje jedną klasę, która zajmuje się zarządzaniem komunikat [concurrency::ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md). `ordered_message_processor` Klasa umożliwia bloki komunikatów do przetwarzania komunikatów w kolejności odbierze je.  
  
 Aby lepiej zrozumieć, jak bloki komunikatów odnoszą się do ich źródeł i obiektów docelowych, należy wziąć pod uwagę poniższym przykładzie. W tym przykładzie pokazano deklaracja [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) klasy.  
  
 [!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]  
  
 `transformer` Pochodną klasy `propagator_block`i w związku z tym działa jako bloku źródła, a blok docelowy. Akceptuje komunikaty typu `_Input` i wysyła komunikaty typu `_Output`. `transformer` Określa klasę `single_link_registry` Menedżer łącza dla bloków docelowych i `multi_link_registry` Menedżer łącza dla bloków źródła. W związku z tym `transformer` obiekt może zawierać maksymalnie jeden element docelowy i nieograniczoną liczbę źródeł.  
  

 Klasa, która pochodzi z `source_block` musi implementować metody: [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets), [accept_message](reference/source-block-class.md#accept_message), [reserve_message](reference/source-block-class.md#reserve_message), [ consume_message](reference/source-block-class.md#consume_message), [release_message](reference/source-block-class.md#release_message), i [resume_propagation](reference/source-block-class.md#resume_propagation). Klasa, która pochodzi z `target_block` musi implementować [propagate_message](reference/propagator-block-class.md#propagate_message) — metoda i opcjonalnie można zaimplementować [send_message](reference/propagator-block-class.md#send_message) metody. Wyprowadzanie z `propagator_block` jest funkcjonalnym odpowiednikiem wynikających z obu `source_block` i `target_block`.  


  
 `propagate_to_any_targets` Metoda jest wywoływana przez środowisko uruchomieniowe asynchronicznie lub synchronicznie przetwarzanie komunikaty przychodzące i Propaguj żadnych wiadomości wychodzącej. `accept_message` Metoda jest wywoływana przez bloki docelowy ma akceptować komunikaty. Wiele komunikatów typów bloku, takich jak `unbounded_buffer`, wysyłania wiadomości tylko do pierwszego elementu docelowego, który otrzyma on. W związku z tym przesyła własność wiadomości do obiektu docelowego. Typy innych bloku komunikatów, takie jak [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md), oferują wiadomości do każdego z jego bloków docelowej. W związku z tym `overwrite_buffer` tworzy kopię komunikat dla każdego z jego elementów docelowych.  
  
 `reserve_message`, `consume_message`, `release_message`, I `resume_propagation` metody włączyć bloki komunikatów do udziału w rezerwacji wiadomości. Docelowy blokuje wywołania `reserve_message` metody, gdy są oferowane komunikat i rezerwacji komunikat do późniejszego użycia. Po bloku docelowego rezerwuje wiadomości, można wywołać `consume_message` metodę, aby korzystać z tej wiadomości lub `release_message` metody próbę anulowania rezerwacji. Jak `accept_message` metody, wdrażanie `consume_message` można przetransferować własność wiadomości lub zwróć kopia wiadomości. Po bloku docelowego zużywa lub zwalnia zastrzeżony komunikat, wywołuje środowiska uruchomieniowego `resume_propagation` metody. Zwykle ta metoda jest nadal propagacji wiadomości, począwszy od następnej wiadomości w kolejce.  
  
 Wywołania środowiska uruchomieniowego `propagate_message` metody asynchronicznie transferu do bieżącej wiadomości z inny blok. `send_message` Podobny metody `propagate_message`, ale synchronicznie, zamiast asynchronicznie, wysyła komunikat do bloków docelowej. Domyślna implementacja `send_message` odrzuca komunikaty przychodzące. Środowisko uruchomieniowe nie mogą wywoływać żadnej z tych metod Jeśli wiadomość nie zostały spełnione funkcji opcjonalny filtr, która jest skojarzona z blok docelowy. Aby uzyskać więcej informacji o filtrach komunikatów, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md).  
  
 [[Górnej](#top)]  
  
##  <a name="class"></a>Definiowanie priority_buffer — klasa  
 `priority_buffer` Klasa jest komunikat niestandardowy typ bloku, któremu porządkuje wiadomości przychodzących najpierw według priorytetu, a następnie według kolejności, w którym są odbierane wiadomości. `priority_buffer` Podobny klasy [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) klasy, ponieważ posiada kolejki komunikatów, a także ponieważ działa jako źródło i blok komunikatów docelowej i może mieć zarówno wielu źródeł i wielu obiekty docelowe. Jednak `unbounded_buffer` podstaw komunikatu propagacji tylko w kolejności, w którym odbiera komunikaty z jego źródeł.  
  
 `priority_buffer` Klasy odbiera komunikaty typu std::[krotki](../../standard-library/tuple-class.md) zawierających `PriorityType` i `Type` elementy. `PriorityType`odwołuje się do typ, który przechowuje priorytet każdy komunikat; `Type` odwołuje się do danych części wiadomości. `priority_buffer` Klasy wysyła komunikaty typu `Type`. `priority_buffer` Klasy zarządza także dwa kolejki komunikatów: [std::priority_queue](../../standard-library/priority-queue-class.md) obiektu dla komunikatów przychodzących i std::[kolejki](../../standard-library/queue-class.md) obiektu dla komunikatów wychodzących. Kolejność według priorytetu wiadomości jest przydatna, gdy `priority_buffer` obiekt odbiera jednocześnie wiele komunikatów lub gdy odbierze ona wiele komunikatów przed komunikaty są odczytywane przez konsumentów.  
  
 Oprócz siedmiu metod czy klasę, która pochodzi z `propagator_block` musi implementować `priority_buffer` klasy również zastąpienia `link_target_notification` i `send_message` metody. `priority_buffer` Klasy definiuje również dwie metody pomocnika publiczne, `enqueue` i `dequeue`i metodę pomocnika prywatnej `propagate_priority_order`.  
  
 W poniższej procedurze opisano sposób wykonania `priority_buffer` klasy.  
  
#### <a name="to-define-the-prioritybuffer-class"></a>Aby zdefiniować klasę priority_buffer  
  
1.  Utwórz plik nagłówka C++ i nadaj mu nazwę `priority_buffer.h`. Alternatywnie można użyć istniejącego pliku nagłówka, który jest częścią projektu.  
  
2.  W `priority_buffer.h`, Dodaj następujący kod.  
  
 [!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]  
  
3.  W `std` przestrzeni nazw, zdefiniuj specjalizacjach [std::less](../../standard-library/less-struct.md) i [std::greater](../../standard-library/greater-struct.md) które działają na współbieżności::[komunikat](../../parallel/concrt/reference/message-class.md) obiektów.  
  
 [!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]  
  
     `priority_buffer` Klasy magazynów `message` obiekty w `priority_queue` obiektu. Te specjalizacje typu Włącz kolejkę priorytet do sortowania wiadomości zgodnie z ich priorytet. Priorytet jest pierwszym elementem `tuple` obiektu.  
  
4.  W `concurrencyex` przestrzeni nazw, Zadeklaruj `priority_buffer` klasy.  
  
 [!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]  
  
     `priority_buffer` Pochodną klasy `propagator_block`. W związku z tym go mogą wysyłać i odbierać wiadomości. `priority_buffer` Klasa może mieć wielu elementów docelowych, który odbiera komunikaty typu `Type`. Może istnieć wiele źródeł, które wysyłają komunikaty typu `tuple<PriorityType, Type>`.  
  
5.  W `private` sekcji `priority_buffer` klasy, Dodaj następujące zmienne Członkowskie.  
  
 [!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]  
  
     `priority_queue` Obiekt przechowuje komunikaty przychodzące; `queue` obiekt zawiera komunikatów wychodzących. A `priority_buffer` obiektu mogą odbierać komunikaty wielu jednocześnie; `critical_section` obiektu synchronizuje dostępu do kolejki komunikatów wejściowych.  
  
6.  W `private` sekcji, zdefiniuj konstruktora kopiującego i operatora przypisania. Zapobiega to `priority_queue` obiektów jest możliwa do przypisania.  
  
 [!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]  
  
7.  W `public` sekcji, definiować konstruktorów, które są wspólne dla wielu typów bloku komunikatów. Również definiować destruktor.  
  
 [!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]  
  
8.  W `public` sekcji, definiować metody `enqueue` i `dequeue`. Te metody pomocnika udostępniają alternatywny sposób wysyłać i odbierać komunikaty z `priority_buffer` obiektu.  
  
 [!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]  
  
9. W `protected` sekcji, zdefiniuj `propagate_to_any_targets` metody.  
  
 [!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]  
  
     `propagate_to_any_targets` Metody przesyła komunikat z przodu kolejki wejściowej do kolejki danych wyjściowych i propaguje wszystkie wiadomości w kolejce danych wyjściowych.  
  
10. W `protected` sekcji, zdefiniuj `accept_message` metody.  
  
 [!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]  
  
     Gdy blok docelowy wywołania `accept_message` metody `priority_buffer` klasy przesyła własność wiadomości do pierwszy blok docelowy, który akceptuje on. (Przypomina to zachowanie `unbounded_buffer`.)  
  
11. W `protected` sekcji, zdefiniuj `reserve_message` metody.  
  
 [!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]  
  
     `priority_buffer` Klasa pozwala na docelowy blok do zarezerwowania wiadomość, gdy komunikat podany identyfikator jest zgodny z identyfikatorem komunikatu, który znajduje się na początek kolejki. Innymi słowy, element docelowy może zarezerwować komunikat, jeśli `priority_buffer` obiekt nie otrzymano jeszcze dodatkowy komunikat i nie ma jeszcze propagowane się bieżący.  
  
12. W `protected` sekcji, zdefiniuj `consume_message` metody.  
  
 [!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]  
  
     Blok docelowy wywołania `consume_message` do przeniesienia własności komunikat, który jest on zarezerwowany.  
  
13. W `protected` sekcji, zdefiniuj `release_message` metody.  
  
 [!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]  
  
     Blok docelowy wywołania `release_message` anulowania rezerwacji jej do wiadomości.  
  
14. W `protected` sekcji, zdefiniuj `resume_propagation` metody.  
  
 [!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]  
  
     Wywołania środowiska uruchomieniowego `resume_propagation` po bloku docelowego zużywa lub zwalnia zastrzeżony komunikat. Ta metoda propaguje wszystkie wiadomości w kolejce danych wyjściowych.  
  
15. W `protected` sekcji, zdefiniuj `link_target_notification` metody.  
  
 [!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]  
  
     `_M_pReservedFor` Zmiennej członkowskiej jest zdefiniowany przez klasę podstawową `source_block`. Tej zmiennej członkowskiej wskazuje blok docelowy, jeśli posiada rezerwacji wiadomość, która jest z przodu kolejki wyjściowej. Wywołania środowiska uruchomieniowego `link_target_notification` gdy nowy element docelowy jest połączony z `priority_buffer` obiektu. Ta metoda propaguje się komunikaty, które znajdują się w kolejki wyjściowej, jeśli docelowy nie posiada rezerwacji.  
  
16. W `private` sekcji, zdefiniuj `propagate_priority_order` metody.  
  
 [!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]  
  
     Ta metoda propaguje wszystkich wiadomości z kolejki wyjściowej. Każdy blok docelowy każdej wiadomości w kolejce jest oferowana dopóki nie akceptuje jeden bloków docelowego komunikatu. `priority_buffer` Klasy zachowuje kolejności komunikatów wychodzących. W związku z tym do pierwszej wiadomości w kolejce dane wyjściowe muszą zostać zaakceptowane przez blok docelowy, zanim ta metoda oferuje inne wiadomości na blokach docelowej.  
  
17. W `protected` sekcji, zdefiniuj `propagate_message` metody.  
  
 [!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]  
  
     `propagate_message` Umożliwia metody `priority_buffer` klasy do działania jako odbiornik wiadomości lub docelowego. Ta metoda odbiera komunikat, który jest oferowany przez blok udostępnionego źródła i wstawia tej wiadomości do kolejki o priorytecie. `propagate_message` Metody asynchronicznie wysyła następnie wszystkie komunikaty wyjściowe do bloków docelowej.  
  

     Środowisko uruchomieniowe wywołuje tę metodę w przypadku wywołania [concurrency::asend](reference/concurrency-namespace-functions.md#asend) funkcji lub gdy blok komunikatów jest podłączone do innych bloków komunikatów.  

  
18. W `protected` sekcji, zdefiniuj `send_message` metody.  
  
 [!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]  
  
     `send_message` Podobny metody `propagate_message`. Jednak wysyła komunikaty wyjściowe synchronicznie zamiast asynchronicznie.  
  

     Środowisko uruchomieniowe wywołuje tę metodę podczas operacji synchronicznych send, np. podczas wywoływania [concurrency::send](reference/concurrency-namespace-functions.md#send) funkcji.  
  
 `priority_buffer` Klasa zawiera przeciążeń konstruktora, które są typowe w wielu typów bloku komunikatów. Niektóre konstruktora overloads podjęcia [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) lub [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) obiektów, które umożliwiają bloku komunikatów, które mają być zarządzane przez harmonogram zadań określonego. Inne przeciążenia konstruktora zająć funkcji filtru. Funkcje filtrowania Włącz bloki komunikatów zaakceptować lub odrzucić komunikat na podstawie jego ładunku. Aby uzyskać więcej informacji o filtrach komunikatów, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md). Aby uzyskać więcej informacji na temat planiści zadań, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
 Ponieważ `priority_buffer` klasy są porządkowane wiadomości według priorytetu, a następnie według kolejności, w którym są odbierane wiadomości, ta klasa jest najbardziej przydatna po odebraniu wiadomości asynchronicznie, na przykład podczas wywoływania [concurrency::asend](reference/concurrency-namespace-functions.md#asend)funkcji lub gdy blok komunikatów jest podłączone do innych bloków komunikatów.  
  
 [[Górnej](#top)]  
  
##  <a name="complete"></a>Pełny przykład  
 W poniższym przykładzie pokazano pełne definicji `priority_buffer` klasy.  
  
 [!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]  
  
 Poniższy przykład jednocześnie wykonuje szereg `asend` i [concurrency::receive](reference/concurrency-namespace-functions.md#receive) operacji na `priority_buffer` obiektu.  

  
 [!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]  
  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe.  
  
```Output  
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36  
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24  
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12  
```  
  
 `priority_buffer` Klasy są porządkowane wiadomości najpierw według priorytetu, a następnie według kolejności, w którym odbiera wiadomości. W tym przykładzie wiadomości o priorytecie liczbowym większa są wstawiane do przodu kolejki.  
  
 [[Górnej](#top)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub Wklej definicji `priority_buffer` klasy w pliku o nazwie `priority_buffer.h` i program testu w pliku o nazwie `priority_buffer.cpp` , a następnie uruchom następujące polecenie w programie Visual Studio Okno wiersza polecenia.  
  
 **Cl.exe priority_buffer.cpp/ehsc**  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność środowiska wykonawczego — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)
