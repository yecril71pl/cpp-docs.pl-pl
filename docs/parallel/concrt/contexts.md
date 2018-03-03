---
title: Konteksty | Dokumentacja firmy Microsoft
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
- contexts [Concurrency Runtime]
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01ec145de3c41aeb30bdd308794d9f8d90a3f3e1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="contexts"></a>Konteksty

Ten dokument zawiera opis roli kontekstów współbieżność środowiska wykonawczego. Wątek, który jest dołączony do harmonogramu jest nazywany *kontekstu wykonywania*, lub po prostu *kontekstu*. [Concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkcji i współbieżność::[klasy kontekstu](../../parallel/concrt/reference/context-class.md) umożliwiają kontrolowanie zachowania kontekstach. Użyj `wait` Funkcja wstrzymania bieżącego kontekstu w wyznaczonym czasie. Użyj `Context` klasy, gdy potrzebujesz większej kontroli nad po kontekstów zablokować odblokować i uzyskanie lub kiedy zachodzi potrzeba oversubscribe bieżącego kontekstu.  
  
> [!TIP]
>  Współbieżność środowiska wykonawczego zapewnia harmonogram domyślny, i dlatego nie trzeba utworzyć w aplikacji. Harmonogram zadań ułatwia dostrojenie wydajności aplikacji, dlatego zaleca się uruchamiania z [równoległych biblioteki wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) w przypadku jesteś nowym użytkownikiem współbieżności środowiska wykonawczego.  
  
## <a name="the-wait-function"></a>Wait — funkcja  

 [Concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkcji implikuje wspólnie wykonywania bieżącego kontekstu określoną liczbę milisekund. Środowisko uruchomieniowe czas yield jest używany do wykonywania innych zadań. Po upływie określonego czasu, środowisko uruchomieniowe zmienia harmonogram kontekstu wykonywania. W związku z tym `wait` funkcja może wstrzymać bieżącego kontekstu dłuższa niż podana wartość `milliseconds` parametru.  
  
 Przekazywanie 0 (zero) dla `milliseconds` parametr powoduje, że środowisko uruchomieniowe wstrzymania bieżącego kontekstu, dopóki wszystkie konteksty active są możliwość wykonywania pracy. Umożliwia to uzyskanie zadania inne aktywne zadania.  
  
### <a name="example"></a>Przykład  
 Na przykład, który używa `wait` funkcji umożliwiające uzyskanie bieżącego kontekstu i w związku z tym mogą zostać w innych kontekstach, uruchamianie, zobacz [porady: Użyj grup harmonogramu do wpływ kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).  
  
## <a name="the-context-class"></a>Context — klasa  
 Współbieżność::[klasy kontekstu](../../parallel/concrt/reference/context-class.md) zapewnia programowania abstrakcji dla kontekstu wykonywania i oferuje dwie ważne funkcje: możliwość wspólnie zablokować odblokować i uzyskanie bieżącego kontekstu i możliwość oversubscribe bieżącego kontekstu.  
  
### <a name="cooperative-blocking"></a>Blokowanie wspólnych  
 `Context` Klasa umożliwia blokowanie lub yield bieżącego kontekstu wykonywania. Blokowanie lub reaguje jest przydatne w przypadku bieżącego kontekstu nie może kontynuować, ponieważ zasób nie jest dostępna.  
  

 [Concurrency::Context::Block](reference/context-class.md#block) metody blokuje bieżącego kontekstu. Kontekst, który jest zablokowany daje jego zasoby przetwarzania, aby środowiska uruchomieniowego można wykonywać inne zadania. [Concurrency::Context::Unblock](reference/context-class.md#unblock) metody odblokowuje zablokowanego kontekstu. `Context::Unblock` Metoda musi zostać wywołana z innego kontekstu niż ten, który wywołuje `Context::Block`. Środowisko uruchomieniowe zgłasza [concurrency::context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md) kontekst Próba odblokowania sam.  
  
 Aby wspólnie blokować i odblokowywać kontekst, należy zwykle wywołać [concurrency::Context::CurrentContext](reference/context-class.md#currentcontext) pobrać wskaźnika do `Context` obiekt, który jest skojarzony z bieżącym wątkiem, a następnie zapisz wynik. Następnie wywołaj `Context::Block` metodę, aby zablokować bieżącego kontekstu. Później, wywołaj `Context::Unblock` z oddzielnych kontekstu, aby odblokować zablokowanego kontekstu.  
  
 Każda para wywołania musi odpowiadać `Context::Block` i `Context::Unblock`. Środowisko uruchomieniowe zgłasza [concurrency::context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md) podczas `Context::Block` lub `Context::Unblock` metoda jest wywoływana po kolei bez pasującego wywołania do innej metody. Jednak nie trzeba wywołać `Context::Block` przed wywołaniem `Context::Unblock`. Na przykład, jeśli wymaga jednego kontekstu `Context::Unblock` przed innego wywołania kontekstowego `Context::Block` na tym samym kontekście pozostaje odblokowany tego kontekstu.  
  
 [Concurrency::Context::Yield](reference/context-class.md#yield) — metoda daje wykonywania, dzięki czemu środowiska uruchomieniowego można wykonywać inne zadania, a następnie ponownie kontekstu wykonywania. Podczas wywoływania `Context::Block` metody środowiska uruchomieniowego nie zaplanować kontekstu.  

  
#### <a name="example"></a>Przykład  
 Na przykład, który używa `Context::Block`, `Context::Unblock`, i `Context::Yield` metody służące do implementacji klasy kooperatywnego semafora, zobacz [porady: Korzystanie z klasy kontekstu do zaimplementowania semafora wspólnego](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).  
  
##### <a name="oversubscription"></a>Nadsubskrypcji  
 Domyślny harmonogram tworzy taką samą liczbę wątków, są wątki dostępnego sprzętu. Można użyć *nadsubskrypcji* można utworzyć dodatkowe wątki wątku danego sprzętu.  
  
 Dla operacji, w praktyce znacznym nadsubskrypcji zwykle nie działa, ponieważ wprowadza ona dodatkowe obciążenie. Jednak dla zadania, które mają wysokie zużycie opóźnienia, na przykład Odczyt danych z dysku lub z połączeniem sieciowym nadsubskrypcji może zwiększyć ogólną wydajność niektórych aplikacji.  
  
> [!NOTE]
>  Włącz nadsubskrypcji tylko z wątku, który został utworzony przez współbieżności środowiska wykonawczego. Nadsubskrypcji nie ma znaczenia, gdy jest wywoływana z wątku, który nie został utworzony przez środowisko uruchomieniowe (łącznie z wątku głównego).  
  
 Aby włączyć nadsubskrypcji w bieżącym kontekście, należy wywołać [concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe) metody z `_BeginOversubscription` ustawiono parametr `true`. Po włączeniu nadsubskrypcji w wątku, który został utworzony przez współbieżności środowiska wykonawczego powoduje środowiska wykonawczego utworzyć jeden wątek dodatkowe. Po wszystkich zadań, które wymagają zakończenia nadsubskrypcji, wywołaj `Context::Oversubscribe` z `_BeginOversubscription` ustawiono parametr `false`.  

  
 Można włączyć nadsubskrypcji wiele razy z bieżącego kontekstu, ale należy wyłączyć taką samą liczbę razy, które ją włączyć. Nadsubskrypcji mogą być zagnieżdżone; oznacza to, że zadanie, które jest tworzone przez inne zadanie, która używa nadsubskrypcji można również oversubscribe kontekst. Jednak jeśli zarówno zadania zagnieżdżonego, jak i jego elementu nadrzędnego należą do tego samego kontekstu, tylko peryferyjnych wywołanie `Context::Oversubscribe` powoduje utworzenie dodatkowego wątku.  
  
> [!NOTE]
>  Środowisko uruchomieniowe zgłasza [concurrency::invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md) wyłączenie nadsubskrypcji przed jej włączeniem.  
  
###### <a name="example"></a>Przykład  
 Na przykład, który używa nadsubskrypcji do przesuwania opóźnienia, powodowany przez odczyt danych z połączenia sieci, zobacz [porady: użycie Nadsubskrypcji do opóźnienia przesunięcie](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Porady: Używanie grup harmonogramu do wywierania wpływu na kolejność wykonywania](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)   
 [Porady: Korzystanie z klasy kontekstu do wdrażania Kooperatywnego semafora](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)   
 [Instrukcje: używanie nadsubskrypcji do przesuwania opóźnienia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)

