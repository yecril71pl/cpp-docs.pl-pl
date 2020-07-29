---
title: Funkcje przekazywania komunikatów
ms.date: 11/04/2016
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
ms.openlocfilehash: 3709e7b5280b96b2b77ec850a06ed15d0e42a7e5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87194631"
---
# <a name="message-passing-functions"></a>Funkcje przekazywania komunikatów

Biblioteka agentów asynchronicznych udostępnia kilka funkcji, które umożliwiają przekazywanie komunikatów między składnikami programu.

Te funkcje przekazywania komunikatów są używane z różnymi typami bloków komunikatów. Aby uzyskać więcej informacji na temat typów bloków komunikatów, które są zdefiniowane przez środowisko uruchomieniowe współbieżności, zobacz [asynchroniczne bloki komunikatów](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="sections"></a><a name="top"></a>Poszczególne

W tym temacie opisano następujące funkcje przekazywania komunikatów:

- [Wyślij i asend](#send)

- [Odbieranie i try_receive](#receive)

- [Przykłady](#examples)

## <a name="send-and-asend"></a><a name="send"></a>Wyślij i asend

Funkcja [concurrency:: Send](reference/concurrency-namespace-functions.md#send) wysyła komunikat do określonego obiektu docelowego synchronicznie, a funkcja [concurrency:: asend](reference/concurrency-namespace-functions.md#asend) wysyła komunikat do określonego obiektu docelowego asynchronicznie. Zarówno `send` Funkcja, jak i, `asend` czeka, aż obiekt docelowy wskazuje, że ostatecznie zaakceptuje lub odrzuci komunikat.

`send`Funkcja czeka, aż obiekt docelowy zaakceptuje lub odrzuci komunikat przed zwróceniem. `send`Funkcja zwraca, **`true`** Jeśli wiadomość została dostarczona i **`false`** w inny sposób. Ponieważ `send` Funkcja działa synchronicznie, `send` Funkcja czeka, aż obiekt docelowy otrzymuje komunikat przed zwróceniem.

Z drugiej strony `asend` Funkcja nie czeka, aż obiekt docelowy zaakceptuje lub odrzuci komunikat przed zwróceniem. Zamiast tego `asend` Funkcja zwraca wartość, **`true`** Jeśli obiekt docelowy akceptuje komunikat i ostatecznie go przyjmie. W przeciwnym razie `asend` zwraca wartość **`false`** wskazującą, że obiekt docelowy odrzucił komunikat lub przełożył decyzję o tym, czy ma zostać przesunięty komunikat.

[[Top](#top)]

## <a name="receive-and-try_receive"></a><a name="receive"></a>Odbieranie i try_receive

Funkcje [concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) i [concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive) odczytują dane z danego źródła. `receive`Funkcja czeka, aż dane staną się dostępne, a `try_receive` Funkcja zwraca od razu.

`receive`Aby kontynuować, użyj funkcji. Użyj `try_receive` funkcji, jeśli nie musisz blokować bieżącego kontekstu lub nie musisz mieć danych, aby kontynuować.

[[Top](#top)]

## <a name="examples"></a><a name="examples"></a>Pokazują

Aby zapoznać się z przykładami korzystającymi z `send` funkcji i i `asend` `receive` , zobacz następujące tematy:

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Instrukcje: implementowanie różnych wzorców producentów i konsumentów](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [Instrukcje: zapewnianie funkcji pracy dla klas wywołania i transformatora](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [Instrukcje: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [Instrukcje: wybieranie spośród ukończonych zadań](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [Instrukcje: Wysyłanie komunikatu w regularnych odstępach czasu](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [Instrukcje: korzystanie z filtru bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[[Top](#top)]

## <a name="see-also"></a>Zobacz także

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[send — Funkcja](reference/concurrency-namespace-functions.md#send)<br/>
[asend, funkcja](reference/concurrency-namespace-functions.md#asend)<br/>
[Funkcja Receive](reference/concurrency-namespace-functions.md#receive)<br/>
[Funkcja try_receive](reference/concurrency-namespace-functions.md#try_receive)
