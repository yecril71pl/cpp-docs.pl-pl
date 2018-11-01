---
title: 'Porady: implementowanie różnych wzorców producent — konsument'
ms.date: 11/04/2016
helpviewer_keywords:
- producer-consumer patterns, implementing [Concurrency Runtime]
- implementing producer-consumer patterns [Concurrency Runtime]
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
ms.openlocfilehash: 1c543e2c80ff9edea417fe8c1254bf9aa5aa37fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658292"
---
# <a name="how-to-implement-various-producer-consumer-patterns"></a>Porady: implementowanie różnych wzorców producent — konsument

W tym temacie opisano sposób implementacji wzorca producent — konsument w aplikacji. W tym wzorcu *producentów* wysyła komunikaty do bloku komunikatu i *konsumenta* odczytuje komunikaty z tego bloku.

Temat pokazuje dwa scenariusze. W pierwszego scenariusza użytkownik musi odebrać każdy komunikat, który wysyła producenta. W drugim scenariuszu konsumenta okresowo sonduje pod kątem danych, a w związku z tym nie trzeba każdego komunikatu.

Oba przykłady w tym temacie umożliwiają funkcje przekazywania komunikatów, bloki komunikatów i agentów przesyłają komunikaty od producenta do konsumenta. Agent producentów korzysta z [concurrency::send](reference/concurrency-namespace-functions.md#send) funkcję, aby pisać wiadomości do [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) obiektu. Agent klienta używa [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkcji do odczytywania komunikatów z [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) obiektu. Obaj agenci przechowują wartość wartownik do koordynowania zakończenia przetwarzania.

Aby uzyskać więcej informacji na temat agentów asynchronicznych, zobacz [agentów asynchronicznych](../../parallel/concrt/asynchronous-agents.md). Aby uzyskać więcej informacji na temat bloków komunikatów i funkcji przekazywania komunikatów, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md) i [funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md).

## <a name="example"></a>Przykład

W tym przykładzie agent producentów wysyła szereg numerów do agent odbiorcy. Użytkownik otrzymuje każda z tych liczb i oblicza średnią ich. Aplikacja zapisuje średnią z konsolą.

W tym przykładzie użyto [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) obiekt, aby włączyć producentów komunikatów do kolejki. `unbounded_buffer` Klasy implementuje `ITarget` i `ISource` tak, aby producenta i konsumenta, można wysyłać i odbierać komunikaty z udostępnionego buforu. `send` i `receive` funkcje koordynować zadanie propagowanie danych od producenta do konsumenta.

[!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
The average is 50.
```

## <a name="example"></a>Przykład

W tym przykładzie agent producentów wysyła szereg giełdowych do agent odbiorcy. Agent odbiorcy okresowo odczytuje bieżący oferty i drukuje ją do konsoli.

W tym przykładzie przypomina poprzedni, z tą różnicą, że używa [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) obiekt, aby włączyć producentów udostępniać jeden komunikat konsumenta. Co w poprzednim przykładzie `overwrite_buffer` klasy implementuje `ITarget` i `ISource` tak, aby producenta i konsumenta może działać na buforze udostępnione wiadomości.

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

W odróżnieniu od z `unbounded_buffer` obiektu `receive` funkcji nie usuwa komunikat z `overwrite_buffer` obiektu. Jeśli odbiorca odczytuje z buforu komunikatu więcej niż jeden raz przed producenta zastępuje ten komunikat, odbiornik uzyskuje dostęp do tego samego komunikatu zawsze.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `producer-consumer.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc producent consumer.cpp**

## <a name="see-also"></a>Zobacz też

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)
