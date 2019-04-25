---
title: Funkcje przekazywania komunikatów
ms.date: 11/04/2016
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
ms.openlocfilehash: 1a1790a08403bcc1d016a39e27c7a121c288af4d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186002"
---
# <a name="message-passing-functions"></a>Funkcje przekazywania komunikatów

Bibliotekę asynchronicznych agentów zawiera kilka funkcji, które umożliwiają przekazywanie komunikatów między składnikami.

Te funkcje przekazywania komunikatów są używane z różnymi typami bloków komunikatów. Aby uzyskać więcej informacji na temat typów blok komunikatów, które są zdefiniowane w czasie wykonywania współbieżności, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md).

##  <a name="top"></a> Sekcje

W tym temacie opisano następujące funkcje przekazywania komunikatów:

- [wysyłanie i asend —](#send)

- [odbieranie i try_receive —](#receive)

- [Przykłady](#examples)

##  <a name="send"></a> wysyłanie i asend —

[Concurrency::send](reference/concurrency-namespace-functions.md#send) funkcja wysyła komunikat do określonego celu synchronicznie i [concurrency::asend](reference/concurrency-namespace-functions.md#asend) funkcja wysyła komunikat do określonego celu asynchronicznie. Zarówno `send` i `asend` funkcje poczekaj na docelowym wskazuje, że go będzie ostatecznie zaakceptować lub odrzucić komunikat.

`send` Funkcja oczekuje na obiekt docelowy zaakceptuje lub odrzuci komunikat to przed zwróceniem. `send` Funkcja zwraca **true** jeżeli zostało dostarczone wiadomości i **false** inaczej. Ponieważ `send` funkcja działa synchronicznie, `send` funkcji czeka, aż element docelowy do odbierania wiadomości, przed jego zwracaniem.

Z drugiej strony `asend` funkcja nie czeka na docelowym zaakceptować lub odrzucić wiadomości, przed jego zwracaniem. Zamiast tego `asend` funkcja zwraca **true** Jeśli element docelowy zaakceptuje wiadomość, a ostatecznie spowoduje przejście. W przeciwnym razie `asend` zwraca **false** aby wskazać, czy element docelowy odrzucenia wiadomości lub odroczone decyzja o tym, czy komunikat o.

[[Górnej](#top)]

##  <a name="receive"></a> odbieranie i try_receive —

[Concurrency::receive](reference/concurrency-namespace-functions.md#receive) i [concurrency::try_receive](reference/concurrency-namespace-functions.md#try_receive) funkcje odczytują dane z danego źródła. `receive` Funkcja czeka na dane staną się dostępne, natomiast `try_receive` funkcja zwraca natychmiast.

Użyj `receive` działa, gdy konieczne jest posiadanie danych, aby kontynuować. Użyj `try_receive` działać, jeśli nie należy zablokować bieżącego kontekstu lub nie masz dane, aby kontynuować.

[[Górnej](#top)]

##  <a name="examples"></a> Przykłady

Aby uzyskać przykłady, które używają `send` i `asend`, i `receive` funkcji, zobacz następujące tematy:

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Instrukcje: implementowanie różnych wzorców producent — konsument](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [Instrukcje: zapewnianie funkcji pracy dla wywoływania oraz klasy transformatora](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [Instrukcje: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [Instrukcje: wybieranie spośród zadań wykonanych](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [Instrukcje: wysyłanie komunikatu w regularnych odstępach czasu](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [Instrukcje: korzystanie z filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[[Górnej](#top)]

## <a name="see-also"></a>Zobacz także

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[send — funkcja](reference/concurrency-namespace-functions.md#send)<br/>
[asend — funkcja](reference/concurrency-namespace-functions.md#asend)<br/>
[Receive — funkcja](reference/concurrency-namespace-functions.md#receive)<br/>
[try_receive — funkcja](reference/concurrency-namespace-functions.md#try_receive)
