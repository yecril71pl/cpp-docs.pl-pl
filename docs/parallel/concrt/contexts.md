---
title: Konteksty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- contexts [Concurrency Runtime]
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7be66658c9452fa97c1971ae6719dccb06dbd836
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378224"
---
# <a name="contexts"></a>Konteksty

W tym dokumencie opisano rolę kontekstów w środowisku uruchomieniowym współbieżności. Wątek, który jest dołączony do harmonogramu jest znany jako *kontekstu wykonania*, lub po prostu *kontekstu*. [Concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkcji i współbieżność::[klasy kontekstu](../../parallel/concrt/reference/context-class.md) pozwalają na kontrolę zachowania kontekstów. Użyj `wait` funkcję, aby zawiesić bieżącego kontekstu przez wyznaczony czas. Użyj `Context` klasy, gdy jest potrzebna większa kontrola nad po kontekstów block odblokowania i uzyskanie lub gdy zachodzi potrzeba oversubscribe bieżącego kontekstu.

> [!TIP]
>  Środowisko uruchomieniowe współbieżności zawiera domyślnego harmonogramu, a w związku z tym nie należy utworzyć w aplikacji. Ponieważ Harmonogram zadań ułatwia dostrajania wydajności aplikacji, zalecamy rozpoczęcie od [biblioteki wzorców równoległych (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [bibliotekę asynchronicznych agentów](../../parallel/concrt/asynchronous-agents-library.md) przypadku jesteś nowym użytkownikiem w czasie wykonywania współbieżności.

## <a name="the-wait-function"></a>Wait — funkcja

[Concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkcja daje wspólne wykonywanie bieżącego kontekstu określoną liczbę milisekund. Środowisko uruchomieniowe czas yield jest używany do wykonywania innych zadań. Po upływie określonego czasu, środowisko uruchomieniowe zmieni ustalony kontekstu wykonywania. W związku z tym `wait` funkcji może zawiesić dłużej niż wartość podana dla bieżącego kontekstu `milliseconds` parametru.

Przekazywanie 0 (zero) dla `milliseconds` parametru powoduje, że środowisko uruchomieniowe do zawieszenia bieżącego kontekstu, dopóki wszystkie konteksty active są możliwość wykonywania pracy. Umożliwia to uzyskanie zadania do innych aktywnych zadań.

### <a name="example"></a>Przykład

Aby uzyskać przykład, który używa `wait` funkcji umożliwiające uzyskanie bieżącego kontekstu, a zatem umożliwiają innych kontekstach uruchomić, zobacz [porady: Użyj grup harmonogramu do wpływają na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

## <a name="the-context-class"></a>Context — klasa

Współbieżność::[klasy kontekstu](../../parallel/concrt/reference/context-class.md) zapewnia programowania abstrakcji dla kontekstu wykonywania i oferuje dwie ważne funkcje: możliwość wspólne Blokuj odblokowywanie i uzyskanie bieżącego kontekstu i możliwość oversubscribe bieżącego kontekstu.

### <a name="cooperative-blocking"></a>Blokowanie współpracy

`Context` Klasa pozwala zablokować, lub yield bieżącego kontekstu wykonywania. Blokowanie lub reaguje jest przydatne, gdy bieżącym kontekście nie można kontynuować, ponieważ zasób jest niedostępny.

[Concurrency::Context::Block](reference/context-class.md#block) metoda blokuje bieżący kontekst. Kontekst, który jest zablokowany daje swoich zasobów do przetwarzania, aby środowisko uruchomieniowe można wykonywać inne zadania. [Concurrency::Context::Unblock](reference/context-class.md#unblock) metoda odblokowuje kontekst zablokowane. `Context::Unblock` Metoda musi zostać wywołana w innym kontekście niż ta, która wywołała `Context::Block`. Środowisko wykonawcze zgłasza [concurrency::context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md) kontekst Próba odblokowania sam.

Wspólne zablokować i odblokować kontekst zazwyczaj wywołujesz [concurrency::Context::CurrentContext](reference/context-class.md#currentcontext) wskaźnik, aby pobrać `Context` obiektu, który jest skojarzony z bieżącym wątkiem, a następnie zapisz wynik. Następnie wywołaj `Context::Block` metodę, aby zablokować bieżącego kontekstu. Później, wywołaj `Context::Unblock` z oddzielnych kontekstu można odblokować zablokowanego kontekstu.

Musi odpowiadać każdej pary wywołania `Context::Block` i `Context::Unblock`. Środowisko wykonawcze zgłasza [concurrency::context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md) podczas `Context::Block` lub `Context::Unblock` metoda jest wywoływana po kolei bez dopasowania wywołania do innej metody. Jednakże, nie trzeba wywoływać `Context::Block` przed wywołaniem `Context::Unblock`. Na przykład, jeśli w jednym kontekście wywołuje `Context::Unblock` przed innym wywołania kontekstowego `Context::Block` ten sam kontekst tego kontekstu nie zmieniają odblokowane.

[Concurrency::Context::Yield](reference/context-class.md#yield) metoda przekazuje wykonywanie kodu, tak, aby środowisko uruchomieniowe może wykonywać inne zadania, a następnie ponownie kontekstu wykonywania. Gdy wywołujesz `Context::Block` metody, środowisko wykonawcze nie zmienić termin egzaminu kontekstu.

#### <a name="example"></a>Przykład

Aby uzyskać przykład, który używa `Context::Block`, `Context::Unblock`, i `Context::Yield` metody służące do implementacji klasy kooperatywnego semafora, zobacz [porady: Korzystanie z klasy kontekstu do wdrażania semafora Cooperative](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).

##### <a name="oversubscription"></a>Nadsubskrypcja

Domyślnego harmonogramu tworzy taką samą liczbę wątków, ponieważ wątków sprzętu. Możesz użyć *nadsubskrypcji* do tworzenia dodatkowych wątków sprzętu danego wątku.

W przypadku operacji wymaga dużej mocy obliczeniowej nadsubskrypcji zazwyczaj Skaluj ponieważ wprowadza dodatkowe obciążenie. Jednak dla zadania, które mają dużej ilości opóźnienia, na przykład, odczytywanie danych z dysku lub połączenie sieciowe nadsubskrypcja może zwiększyć ogólną wydajność niektórych aplikacji.

> [!NOTE]
>  Włączyć nadsubskrypcję tylko z wątku, który został utworzony w czasie wykonywania współbieżności. Nadsubskrypcja nie obowiązuje, gdy jest wywoływana z wątku, który nie został utworzony w czasie wykonywania (w tym wątku głównego).

Aby włączyć nadsubskrypcję w bieżącym kontekście, należy wywołać [concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe) metody z `_BeginOversubscription` parametr `true`. Po włączeniu nadsubskrypcji w wątku, który został utworzony przez środowisko uruchomieniowe współbieżności powoduje środowiska uruchomieniowego utworzyć jeden dodatkowy wątek. Po wszystkich zadań, które wymagają zakończenia nadsubskrypcji wywołania `Context::Oversubscribe` z `_BeginOversubscription` parametr `false`.

Można włączyć nadsubskrypcję, wiele razy z bieżącego kontekstu, ale należy wyłączyć taką samą liczbę prób ją włączyć. Nadsubskrypcja może być też zagnieżdżona; oznacza to zadanie, które jest tworzony przez inne zadanie, które używa nadsubskrypcja może również nadsubskrybować kontekst. Jednakże jeśli zarówno zagnieżdżone zadanie, a jego elementem nadrzędnym należy na tym samym kontekście wywołanie prowadzące do `Context::Oversubscribe` powoduje utworzenie dodatkowy wątek.

> [!NOTE]
>  Środowisko wykonawcze zgłasza [concurrency::invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md) wyłączenie nadsubskrypcji przed jego włączeniem.

###### <a name="example"></a>Przykład

Na przykład, który używa nadsubskrypcji do przesuwania opóźnienia, które jest spowodowany przez odczytywanie danych z połączenia sieciowego, zobacz [porady: Użyj Nadsubskrypcji do opóźnienia przesunięcie](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

## <a name="see-also"></a>Zobacz też

[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Instrukcje: używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)<br/>
[Instrukcje: korzystanie z klasy kontekstu do wdrażania a kooperatywnego semafora](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[Instrukcje: używanie nadsubskrypcji do przesuwania opóźnienia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)

