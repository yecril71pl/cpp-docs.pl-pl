---
title: 'Porady: implementowanie różnych wzorców producent — konsument'
ms.date: 11/04/2016
helpviewer_keywords:
- producer-consumer patterns, implementing [Concurrency Runtime]
- implementing producer-consumer patterns [Concurrency Runtime]
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
ms.openlocfilehash: 70813adf6715a2bcaf4af7370ce43d99c44263bd
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413778"
---
# <a name="how-to-implement-various-producer-consumer-patterns"></a>Porady: implementowanie różnych wzorców producent — konsument

W tym temacie opisano sposób implementacji wzorca producenta dla konsumentów w aplikacji. W tym wzorcu *producent* wysyła komunikaty do bloku komunikatów, a *konsument* odczytuje komunikaty z tego bloku.

W temacie przedstawiono dwa scenariusze. W pierwszym scenariuszu konsument musi odebrać każdy komunikat wysyłany przez producenta. W drugim scenariuszu konsument okresowo sonduje dane i w związku z tym nie musi odbierać poszczególnych komunikatów.

Oba przykłady w tym temacie służą do przesyłania komunikatów od producenta do konsumenta przy użyciu funkcji agentów, bloków komunikatów i przekazywania komunikatów. Agent produkcyjny używa funkcji [concurrency:: Send](reference/concurrency-namespace-functions.md#send) do zapisu komunikatów do obiektu [concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md) . Agent odbiorcy używa funkcji [concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) do odczytywania komunikatów z obiektu [concurrency:: ISource](../../parallel/concrt/reference/isource-class.md) . Oba agenci przechowują wartość wskaźnikową, aby koordynować koniec przetwarzania.

Aby uzyskać więcej informacji na temat agentów asynchronicznych, zobacz [agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md). Aby uzyskać więcej informacji na temat bloków komunikatów i funkcji przekazywania komunikatów, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md) i [funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md).

## <a name="example-send-series-of-numbers-to-consumer-agent"></a>Przykład: Wyślij serię liczb do agenta klienta

W tym przykładzie agent produkcyjny wysyła szereg numerów do agenta konsumenta. Konsument otrzymuje każdą z tych liczb i obliczy ich średnią. Aplikacja zapisuje średnią w konsoli programu.

Ten przykład używa obiektu [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) , aby umożliwić producentowi kolejkowanie komunikatów. `unbounded_buffer`Klasa implementuje `ITarget` i `ISource` tak, aby producent i odbiorca mogli wysyłać i odbierać komunikaty do i z udostępnionego buforu. `send`Funkcje i `receive` koordynują zadanie propagowania danych od producenta do konsumenta.

[!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
The average is 50.
```

## <a name="example-send-series-of-stock-quotes-to-consumer-agent"></a>Przykład: Wyślij serię notowań giełdowych do agenta klienta

W tym przykładzie agent produkcyjny wysyła serię notowań giełdowych do agenta konsumenta. Agent konsumenta okresowo odczytuje bieżącą ofertę i drukuje ją w konsoli programu.

Ten przykład przypomina poprzednią, z tą różnicą, że używa obiektu [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) , aby umożliwić producentowi udostępnianie jednej wiadomości klientowi. Tak jak w poprzednim przykładzie, `overwrite_buffer` Klasa implementuje `ITarget` i `ISource` tak, aby producent i odbiorca mogli działać w buforze komunikatów udostępnionych.

[!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_2.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe.

```Output
Current quote is 24.44.
Current quote is 24.44.
Current quote is 24.65.
Current quote is 24.99.
Current quote is 23.76.
Current quote is 22.30.
Current quote is 25.89.
```

W przeciwieństwie do `unbounded_buffer` obiektu, `receive` Funkcja nie usuwa komunikatu z `overwrite_buffer` obiektu. Jeśli odbiorca odczytuje z buforu komunikatów więcej niż jeden raz przed zastąpieniem tego komunikatu przez producenta, odbiorca uzyskuje ten sam komunikat za każdym razem.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie, `producer-consumer.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**cl.exe/EHsc Producer-Consumer. cpp**

## <a name="see-also"></a>Zobacz także

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)
