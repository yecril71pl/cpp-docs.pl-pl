---
title: Konteksty
ms.date: 11/04/2016
helpviewer_keywords:
- contexts [Concurrency Runtime]
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
ms.openlocfilehash: 7df75ae7c1ac2b1d8c0b73ff1f1e3f2800d559b9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87194878"
---
# <a name="contexts"></a>Konteksty

W tym dokumencie opisano rolę kontekstów w środowisko uruchomieniowe współbieżności. Wątek, który jest dołączony do harmonogramu, jest znany jako *kontekst wykonywania*lub po prostu *kontekst*. Funkcja [concurrency:: wait](reference/concurrency-namespace-functions.md#wait) oraz Klasa concurrency::[Context](../../parallel/concrt/reference/context-class.md) umożliwiają sterowanie zachowaniem kontekstów. Użyj `wait` funkcji, aby zawiesić bieżący kontekst przez określony czas. Użyj `Context` klasy, gdy potrzebujesz większej kontroli nad tym, kiedy konteksty blokują, odblokują i implikują, lub gdy chcesz zasubskrybować bieżący kontekst.

> [!TIP]
> Środowisko uruchomieniowe współbieżności udostępnia domyślny harmonogram i dlatego nie jest konieczne tworzenie go w aplikacji. Ponieważ Harmonogram zadań ułatwia dostosowanie wydajności aplikacji, zalecamy rozpoczęcie od [biblioteki równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) , jeśli są one nowe dla środowisko uruchomieniowe współbieżności.

## <a name="the-wait-function"></a>Funkcja oczekiwania

Funkcja [concurrency:: wait](reference/concurrency-namespace-functions.md#wait) wspólnie daje wykonywanie bieżącego kontekstu przez określoną liczbę milisekund. Środowisko uruchomieniowe używa czasu Yield do wykonywania innych zadań. Po upływie określonego czasu środowisko uruchomieniowe ponownie planuje kontekst wykonania. W związku z tym `wait` Funkcja może zawiesić bieżący kontekst dłużej niż wartość podana dla `milliseconds` parametru.

Przekazanie wartości 0 (zero) dla `milliseconds` parametru spowoduje zawieszenie przez środowisko uruchomieniowe bieżącego kontekstu do momentu, gdy wszystkie inne aktywne konteksty będą miały możliwość wykonania pracy. Dzięki temu można uzyskać zadanie dla wszystkich innych aktywnych zadań.

### <a name="example"></a>Przykład

Aby zapoznać się z przykładem korzystającym z `wait` funkcji w celu uzyskania bieżącego kontekstu i w związku z tym zezwolić na uruchamianie innych kontekstów, zobacz [jak: korzystanie z grup harmonogramu w celu wywierania wpływu na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

## <a name="the-context-class"></a>Klasa kontekstu

Klasa concurrency::[Context](../../parallel/concrt/reference/context-class.md) zapewnia abstrakcję programowania dla kontekstu wykonywania i oferuje dwie ważne funkcje: zdolność do współblokowania, odblokowywania i przekazywania bieżącego kontekstu oraz możliwość zasubskrybowania bieżącego kontekstu.

### <a name="cooperative-blocking"></a>Blokowanie współpracy

`Context`Klasa pozwala zablokować lub uzyskać bieżący kontekst wykonania. Blokowanie lub przekazanie jest przydatne, gdy bieżący kontekst nie może być kontynuowany, ponieważ zasób nie jest dostępny.

Metoda [concurrency:: Context:: Block](reference/context-class.md#block) blokuje bieżący kontekst. Zablokowany kontekst zapewnia zasoby przetwarzania, aby środowisko uruchomieniowe mogły wykonywać inne zadania. Metoda [concurrency:: Context:: Unblock](reference/context-class.md#unblock) blokuje zablokowany kontekst. `Context::Unblock`Metoda musi być wywołana z innego kontekstu niż ten, który został wywołany `Context::Block` . Środowisko uruchomieniowe zgłasza [współbieżność:: context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md) , jeśli kontekst próbuje odblokować siebie.

Aby wspólnie blokować i odblokować kontekst, zazwyczaj wywołuje się [concurrency:: Context:: CurrentContext](reference/context-class.md#currentcontext) , aby pobrać wskaźnik do `Context` obiektu, który jest skojarzony z bieżącym wątkiem i zapisać wynik. Następnie należy wywołać `Context::Block` metodę, aby zablokować bieżący kontekst. Później, wywołaj `Context::Unblock` z osobnego kontekstu, aby odblokować zablokowany kontekst.

Należy dopasować każdą parę wywołań do `Context::Block` i `Context::Unblock` . Środowisko uruchomieniowe zgłasza [współbieżność:: context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md) , gdy `Context::Block` `Context::Unblock` Metoda or jest wywoływana jednokrotnie bez pasującego wywołania do innej metody. Nie trzeba jednak dzwonić `Context::Block` przed wywołaniem `Context::Unblock` . Na przykład jeśli jeden kontekst wywołuje `Context::Unblock` przed innym wywołaniem kontekstu `Context::Block` dla tego samego kontekstu, ten kontekst pozostaje odblokowany.

Metoda [concurrency:: Context:: Yield](reference/context-class.md#yield) daje wykonanie, tak aby środowisko uruchomieniowe mogły wykonywać inne zadania, a następnie ponownie zaplanować wykonywanie. Po wywołaniu `Context::Block` metody, środowisko uruchomieniowe nie planuje ponownie kontekstu.

#### <a name="example"></a>Przykład

Aby zapoznać się z przykładem `Context::Block` , który używa `Context::Unblock` metod, i `Context::Yield` do implementowania wspólnej klasy semaforów, zobacz [How to: Use the Context Class to Implement The Spółdzielczy semafor](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).

##### <a name="oversubscription"></a>Nadsubskrypcji

Domyślny harmonogram tworzy tę samą liczbę wątków, ponieważ dostępne są wątki sprzętowe. Można użyć *nadsubskrypcji* , aby utworzyć dodatkowe wątki dla danego wątku sprzętowego.

W przypadku operacji intensywnie korzystających z obliczeń nadmiarowe przeważnie nie są skalowane, ponieważ wprowadzają dodatkowe koszty. Jednak w przypadku zadań z dużą ilością opóźnień, na przykład odczytywania danych z dysku lub z połączenia sieciowego, nadpłata może zwiększyć ogólną wydajność niektórych aplikacji.

> [!NOTE]
> Włącz nadsubskrypcję tylko z wątku, który został utworzony przez środowisko uruchomieniowe współbieżności. Nadsubskrypcja nie działa, gdy jest wywoływana z wątku, który nie został utworzony przez środowisko uruchomieniowe (w tym główny wątek).

Aby włączyć nadsubskrypcje w bieżącym kontekście, wywołaj metodę [concurrency:: Context::](reference/context-class.md#oversubscribe) Subscription z `_BeginOversubscription` parametrem ustawionym na **`true`** . Po włączeniu nadsubskrypcji w wątku, który został utworzony przez środowisko uruchomieniowe współbieżności, powoduje to utworzenie jednego dodatkowego wątku przez środowisko uruchomieniowe. Po wszystkich zadaniach, które wymagają ukończenia nadsubskrypcji, wywołaj `Context::Oversubscribe` z `_BeginOversubscription` parametrem ustawionym na **`false`** .

Można włączyć nadsubskrypcję wiele razy z bieżącego kontekstu, ale należy wyłączyć tę samą liczbę razy. Nadsubskrypcja może być również zagnieżdżona; oznacza to, że zadanie tworzone przez inne zadanie, które korzysta z nadmiarowej subskrypcji, może również zasubskrybować jego kontekst. Jeśli jednak zarówno zadanie zagnieżdżone, jak i jego element nadrzędny należą do tego samego kontekstu, tylko zewnętrzne wywołanie `Context::Oversubscribe` powoduje utworzenie dodatkowego wątku.

> [!NOTE]
> Środowisko uruchomieniowe zgłasza [współbieżność:: invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md) , jeśli subskrypcja jest wyłączona, zanim zostanie włączona.

###### <a name="example"></a>Przykład

Aby zapoznać się z przykładem, który używa nadsubskrypcji w celu przesunięcia opóźnienia, który jest spowodowany odczytem danych z połączenia sieciowego, zobacz [jak: używanie nadsubskrypcji w celu przesunięcia opóźnienia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

## <a name="see-also"></a>Zobacz także

[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Instrukcje: używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)<br/>
[Instrukcje: korzystanie z klasy kontekstu w celu zaimplementowania współdziałania ze wspólnym semaforem](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[Instrukcje: używanie nadsubskrypcji do opóźnienia przesunięcia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)
