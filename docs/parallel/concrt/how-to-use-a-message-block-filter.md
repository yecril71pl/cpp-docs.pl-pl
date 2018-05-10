---
title: 'Porady: Użyj filtra bloku komunikatów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message-block filters, using [Concurrency Runtime]
- using message-block filters [Concurrency Runtime]
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92de322142e56eb9907da2e19d350c3af9c8a7d9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-a-message-block-filter"></a>Porady: korzystanie z filtra bloku komunikatów
Ten dokument pokazuje, jak użyć funkcji filtru w celu włączenia bloku komunikatów asynchronicznych o zaakceptowanie lub odrzucenie wiadomości na podstawie ładunku tej wiadomości.  
  
 Podczas tworzenia obiektu bloku komunikatów takich jak [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md), [concurrency::call](../../parallel/concrt/reference/call-class.md), lub [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md), możesz podać *funkcja filtrowania* Określa, czy blok komunikatów akceptuje lub odrzuca komunikat. Funkcja filtru jest to wygodny sposób, aby zagwarantować, że blok komunikatów odbiera tylko niektóre wartości.  
  
 Funkcje filtrowania są ważne, ponieważ umożliwiają one nawiązanie bloki komunikatów do formularza *przepływu danych sieci*. W przypadku sieci przepływu danych bloki komunikatów sterowanie przepływem danych przez przetwarzanie tylko tych wiadomości, które spełniają określone kryteria. To porównać do modelu przepływu sterowania, gdy przepływ danych jest regulowany za pomocą struktury sterujące, takie jak warunkowe instrukcje, pętle i tak dalej.  
  
 Ten dokument zawiera podstawowy przykład sposobu użycia filtr komunikatu. Dodatkowe przykłady używających filtry komunikatów i model przepływu danych do łączenia bloki komunikatów, zobacz [wskazówki: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md) i [wskazówki: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md) .  
  
## <a name="example"></a>Przykład  
 Należy wziąć pod uwagę następujące funkcji `count_primes`, która przedstawia podstawowe sposoby użycia bloku komunikatów, który Filtruj wiadomości przychodzących. Blok komunikatów dołącza liczb pierwszych do [std::vector](../../standard-library/vector-class.md) obiektu. `count_primes` Funkcja wysyła kilka numerów dla bloku komunikatów, odbiera wartości dane wyjściowe z bloku komunikatów i wyświetla te numery, które są prime do konsoli.  
  
 [!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_1.cpp)]  
  
 `transformer` Obiektu przetwarza wszystkie wartości wejściowe; wymaga jednak tylko wartości, które są pierwsze. Mimo że aplikacja może być zapisany, aby nadawca wysyła tylko liczb pierwszych, wymagania odbiorcy wiadomości nie zawsze być znane.  
  
## <a name="example"></a>Przykład  
 Następująca funkcja `count_primes_filter`, wykonuje to samo zadanie `count_primes` funkcji. Jednak `transformer` obiekt w tej wersji używa funkcji filtru do akceptowania tylko wartości, które są pierwsze. Funkcja, która wykonuje akcję odbiera tylko liczb pierwszych; w związku z tym nie ma do wywołania `is_prime` funkcji.  
  
 Ponieważ `transformer` obiekt odbiera tylko liczb pierwszych `transformer` sam obiekt może zawierać liczb pierwszych. Innymi słowy `transformer` obiektu w tym przykładzie nie jest wymagane do dodania liczb pierwszych do `vector` obiektu.  
  
 [!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_2.cpp)]  
  
 `transformer` Obiektu teraz przetwarza tylko wartości, które są pierwsze. W poprzednim przykładzie `transformer` obiektu przetwarza wszystkie komunikaty. W związku z tym w poprzednim przykładzie musi otrzymać taką samą liczbę wiadomości, które wysyła. W tym przykładzie użyto wynik [concurrency::send](reference/concurrency-namespace-functions.md#send) funkcji, aby określić, ile komunikatów można otrzymywać `transformer` obiektu. `send` Funkcja zwraca `true` gdy bufor komunikatów akceptuje wiadomości i `false` gdy bufor komunikatów odrzuca komunikat. W związku z tym liczbę razy, czy bufor komunikatów akceptuje komunikat odpowiada liczba liczb pierwszych.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia pełny przykład. Przykład wywołuje zarówno `count_primes` funkcji i `count_primes_filter` funkcji.  
  
 [!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_3.cpp)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `primes-filter.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc blokad filter.cpp**  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Funkcja filtru może być funkcją lambda, wskaźnik funkcji lub obiekt funkcji. Każda funkcja filtru przyjmuje jeden z następujących formatów:  
  
```Output  
bool (T)  
bool (T const &)  
```  
  
 Aby usunąć niepotrzebne kopiowanie danych, należy użyć drugiej formy w przypadku typu agregacji, który jest przekazywany przez wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)   
 [Wskazówki: Tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)   
 [Wskazówki: Tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [transformer, klasa](../../parallel/concrt/reference/transformer-class.md)
