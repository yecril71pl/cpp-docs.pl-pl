---
title: Funkcje przekazywania komunikatów
ms.date: 11/04/2016
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
ms.openlocfilehash: 4e1052a59f355c4ad5a7c6b57724268c24a209b4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143294"
---
# <a name="message-passing-functions"></a>Funkcje przekazywania komunikatów

Biblioteka agentów asynchronicznych udostępnia kilka funkcji, które umożliwiają przekazywanie komunikatów między składnikami programu.

Te funkcje przekazywania komunikatów są używane z różnymi typami bloków komunikatów. Aby uzyskać więcej informacji na temat typów bloków komunikatów, które są zdefiniowane przez środowisko uruchomieniowe współbieżności, zobacz [asynchroniczne bloki komunikatów](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="top"></a>Poszczególne

W tym temacie opisano następujące funkcje przekazywania komunikatów:

- [Wyślij i asend](#send)

- [Odbieranie i try_receive](#receive)

- [Przykłady](#examples)

## <a name="send"></a>Wyślij i asend

Funkcja [concurrency:: Send](reference/concurrency-namespace-functions.md#send) wysyła komunikat do określonego obiektu docelowego synchronicznie, a funkcja [concurrency:: asend](reference/concurrency-namespace-functions.md#asend) wysyła komunikat do określonego obiektu docelowego asynchronicznie. Zarówno `send`, jak i `asend`, odczekają, aż obiekt docelowy wskazuje, że ostatecznie zaakceptuje lub odrzuci komunikat.

Funkcja `send` czeka, aż obiekt docelowy zaakceptuje lub odrzuci komunikat przed zwróceniem. Funkcja `send` zwraca **wartość true** , jeśli wiadomość została dostarczona i w przeciwnym razie ma **wartość false** . Ponieważ funkcja `send` działa synchronicznie, funkcja `send` czeka, aż obiekt docelowy otrzyma komunikat przed zwróceniem.

Z drugiej strony funkcja `asend` nie czeka, aż obiekt docelowy zaakceptuje lub odrzuci komunikat przed zwróceniem. Zamiast tego funkcja `asend` zwraca **wartość true** , jeśli obiekt docelowy akceptuje komunikat i ostatecznie go przyjmie. W przeciwnym razie `asend` zwraca **wartość false** , aby wskazać, że obiekt docelowy odrzucił komunikat lub przełożył decyzję o tym, czy ma zostać przesunięty komunikat.

[[Top](#top)]

## <a name="receive"></a>Odbieranie i try_receive

Funkcje [concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) i [concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive) odczytują dane z danego źródła. Funkcja `receive` czeka, aż dane staną się dostępne, a funkcja `try_receive` zwraca od razu.

Użyj funkcji `receive`, gdy musisz mieć dane, aby kontynuować. Użyj funkcji `try_receive`, jeśli nie musisz blokować bieżącego kontekstu lub nie musisz mieć danych, aby kontynuować.

[[Top](#top)]

## <a name="examples"></a>Pokazują

Przykłady korzystające z `send` i `asend`i `receive` funkcji można znaleźć w następujących tematach:

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Instrukcje: implementowanie różnych wzorców producent — konsument](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [Instrukcje: zapewnianie funkcji pracy dla wywoływania oraz klasy transformatora](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [Instrukcje: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [Instrukcje: wybieranie spośród zadań wykonanych](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [Instrukcje: wysyłanie komunikatu w regularnych odstępach czasu](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [Instrukcje: korzystanie z filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[[Top](#top)]

## <a name="see-also"></a>Zobacz też

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[send — Funkcja](reference/concurrency-namespace-functions.md#send)<br/>
[asend, funkcja](reference/concurrency-namespace-functions.md#asend)<br/>
[Funkcja Receive](reference/concurrency-namespace-functions.md#receive)<br/>
[Funkcja try_receive](reference/concurrency-namespace-functions.md#try_receive)
