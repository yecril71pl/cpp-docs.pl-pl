---
title: Funkcje przekazywania komunikatów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9eecb7d2a45079ff14740167a192eafaab268150
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688053"
---
# <a name="message-passing-functions"></a>Funkcje przekazywania komunikatów
Biblioteki agentów asynchronicznych zawiera kilka funkcji, które umożliwiają przekazywanie komunikatów między składnikami.  
  
 Te funkcje przekazywania komunikatów są używane z różnymi typami bloku komunikatów. Aby uzyskać więcej informacji o typach bloku komunikatów, które są zdefiniowane przez współbieżności środowiska wykonawczego, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md).  
  
##  <a name="top"></a> Sekcje  
 W tym temacie opisano następujące funkcje przekazywania komunikatów:  
  
-   [Wyślij i asend —](#send)  
  
-   [odbieranie i try_receive —](#receive)  
  
-   [Przykłady](#examples)  
  
##  <a name="send"></a> Wyślij i asend —  

 [Concurrency::send](reference/concurrency-namespace-functions.md#send) funkcja wysyła komunikat do określonego obiektu docelowego synchronicznie i [concurrency::asend](reference/concurrency-namespace-functions.md#asend) funkcja wysyła komunikat do określonego obiektu docelowego asynchronicznie. Zarówno `send` i `asend` funkcje poczekaj docelowy wskazuje, że go zostanie ostatecznie zaakceptować lub odrzucić komunikat.  
  
 `send` Funkcja oczekuje na obiekt docelowy zaakceptuje lub odrzuci komunikat, zanim zwraca. `send` Funkcja zwraca `true` Jeśli wiadomość zostanie dostarczona i `false` inaczej. Ponieważ `send` funkcja działa synchronicznie, `send` funkcja oczekuje na komunikat, zanim zwraca obiekt docelowy.  
  
 Z drugiej strony `asend` funkcji bez oczekiwania dla obiektu docelowego zaakceptować lub odrzucić komunikat, zanim zwraca. Zamiast tego `asend` funkcja zwraca `true` docelowy akceptuje wiadomości i ostatecznie spowoduje przejście. W przeciwnym razie `asend` zwraca `false` wskazująca, czy element docelowy odrzucone wiadomości lub odroczone decyzja o tym, czy komunikat.  
  
 [[Górnej](#top)]  
  
##  <a name="receive"></a> odbieranie i try_receive —  

 [Concurrency::receive](reference/concurrency-namespace-functions.md#receive) i [concurrency::try_receive](reference/concurrency-namespace-functions.md#try_receive) funkcje odczytać danych z danego źródła. `receive` Funkcja czeka na danych stanie się dostępna, podczas gdy `try_receive` funkcja zwraca natychmiast.  
  
 Użyj `receive` działać, jeśli musi mieć danych, aby kontynuować. Użyj `try_receive` działać, jeśli nie można zablokować bieżącego kontekstu lub nie masz dane, aby kontynuować.  
  
 [[Górnej](#top)]  
  
##  <a name="examples"></a> Przykłady  
 Aby uzyskać przykłady pokazujące, które używają `send` i `asend`, i `receive` funkcji, zobacz następujące tematy:  
  
-   [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [Instrukcje: implementowanie różnych wzorców producent — konsument](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)  
  
-   [Instrukcje: zapewnianie funkcji pracy dla wywoływania oraz klasy transformatora](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)  
  
-   [Instrukcje: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)  
  
-   [Instrukcje: wybieranie spośród zadań wykonanych](../../parallel/concrt/how-to-select-among-completed-tasks.md)  
  
-   [Instrukcje: wysyłanie komunikatu w regularnych odstępach czasu](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)  
  
-   [Instrukcje: korzystanie z filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
  
 [[Górnej](#top)]  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)   
 [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)   
 [send — funkcja](reference/concurrency-namespace-functions.md#send)   
 [asend — funkcja](reference/concurrency-namespace-functions.md#asend)   
 [Receive — funkcja](reference/concurrency-namespace-functions.md#receive)   
 [try_receive — funkcja](reference/concurrency-namespace-functions.md#try_receive)


