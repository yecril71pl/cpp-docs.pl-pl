---
title: "Porady: Implementowanie różnych wzorców producent — konsument | Dokumentacja firmy Microsoft"
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
- producer-consumer patterns, implementing [Concurrency Runtime]
- implementing producer-consumer patterns [Concurrency Runtime]
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0efafe17cd524c241e709d3c3c59233a130cdf95
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-implement-various-producer-consumer-patterns"></a>Porady: implementowanie różnych wzorców producent — konsument
W tym temacie opisano Implementowanie wzorca producent — konsument w aplikacji. W tym wzorcu *producent* wysyła komunikaty do bloku komunikatów i *konsumenta* odczytuje wiadomości z tego bloku.  
  
 Temat przedstawiono dwa scenariusze. W pierwszego scenariusza klient musi odebrać każdy komunikat, który wysyła producenta. W drugim scenariuszu konsumenta okresowo sonduje danych i w związku z tym nie ma każdy komunikat.  
  
 Oba przykłady w tym temacie korzystając z agentów, bloki komunikatów i funkcje przekazywania komunikatów do przekazywania wiadomości od producenta do konsumenta. Producent agent używa [concurrency::send](reference/concurrency-namespace-functions.md#send) funkcja komunikaty, aby zapisać [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) obiektu. Agent użytkownika użyje [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkcji do czytania wiadomości z [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) obiektu. Zarówno agentów przytrzymaj wartość wartownik do koordynowania zakończenie przetwarzania.  
  
 Aby uzyskać więcej informacji na temat agentów asynchronicznych, zobacz [agentów asynchronicznych](../../parallel/concrt/asynchronous-agents.md). Aby uzyskać więcej informacji na temat bloki komunikatów i funkcje przekazywania komunikatów, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md) i [funkcji przekazywania wiadomości](../../parallel/concrt/message-passing-functions.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie agent producent wysyła serii liczb znajdujących się agent odbiorcy. Klient otrzymuje każda z tych numerów i oblicza średnią ich. Aplikacja zapisuje średnią do konsoli.  
  
 W tym przykładzie użyto [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) obiekt, aby włączyć producent komunikatów do kolejki. `unbounded_buffer` Klasa implementuje `ITarget` i `ISource` tak, aby wysyłać i odbierać komunikaty z udostępnionego buforu producenta i konsumenta. `send` i `receive` funkcje koordynować zadanie propagowanie danych od producenta do konsumenta.  
  
 [!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_1.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```Output  
The average is 50.  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie agent producent wysyła szereg giełdowych się agent odbiorcy. Agent odbiorcy okresowo odczytuje bieżący oferty i wysłania go do konsoli.  
  
 W tym przykładzie przypomina poprzedni, z wyjątkiem tego, że używa [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) obiekt, aby włączyć producent na współużytkowanie jeden komunikat z klienta. Tak jak w poprzednim przykładzie `overwrite_buffer` klasa implementuje `ITarget` i `ISource` tak, aby producenta i że użytkownik może działać dla bufora udostępnianego komunikatu.  
  
 [!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_2.cpp)]  
  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe.  
  
```Output  
Current quote is 24.44.  
Current quote is 24.44.  
Current quote is 24.65.  
Current quote is 24.99.  
Current quote is 23.76.  
Current quote is 22.30.  
Current quote is 25.89.  
```  
  
 W odróżnieniu od z `unbounded_buffer` obiektu `receive` funkcja nie usuwa komunikat z `overwrite_buffer` obiektu. Jeżeli konsumenta odczytuje z buforu komunikatu więcej niż jeden raz przed producenta spowoduje zastąpienie tego komunikatu, odbiornik pobiera ten sam komunikat zawsze.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `producer-consumer.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc producent consumer.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)   
 [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)   
 [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)
