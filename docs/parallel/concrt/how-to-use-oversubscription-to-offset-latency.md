---
title: "Porady: używanie Nadsubskrypcji do przesuwania opóźnienia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- oversubscription, using [Concurrency Runtime]
- using oversubscription [Concurrency Runtime]
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e1a8f059abffd261de2002ed5d18067c48d74876
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-oversubscription-to-offset-latency"></a>Porady: używanie nadsubskrypcji do przesuwania opóźnienia
Nadsubskrypcji może zwiększyć ogólną wydajność niektórych aplikacji, które zawiera zadania, które mają wysokie zużycie opóźnienia. W tym temacie przedstawiono sposób używanie nadsubskrypcji do przesuwania opóźnienia, które jest spowodowany przez odczyt danych z połączenia sieciowego.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) do pobierania plików z serwerów HTTP. `http_reader` Pochodną klasy [concurrency::agent](../../parallel/concrt/reference/agent-class.md) i używa komunikatów przekazywanie asynchronicznie odczytać nazwy których adres URL do pobrania.  
  
 `http_reader` Klasy używa [concurrency::task_group](reference/task-group-class.md) klasy można jednocześnie odczytać każdego pliku. Każde zadanie wymaga [concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe) metody z `_BeginOversubscription` ustawiona `true` umożliwiające nadsubskrypcji w bieżącym kontekście. Każde zadanie używa Microsoft Foundation Classes (MFC) [CInternetSession](../../mfc/reference/cinternetsession-class.md) i [CHttpFile](../../mfc/reference/chttpfile-class.md) klasy można pobrać pliku. Na koniec każdego zadania wywołuje `Context::Oversubscribe` z `_BeginOversubscription` ustawiona `false` wyłączyć nadsubskrypcji.  
  
 Po włączeniu nadsubskrypcji środowiska uruchomieniowego tworzy jeden wątek dodatkowe do uruchamiania zadania. Każdy z tych wątków również oversubscribe bieżącego kontekstu i tym samym utworzenia dodatkowych wątków. `http_reader` Klasy używa [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) obiekt, aby ograniczyć liczbę wątków używanych przez aplikację. Agent inicjuje bufor o stałą liczbę wartości tokenów. Dla każdej operacji pobierania agenta odczytuje wartość tokenu z buforu, zanim operacja uruchamiania, a następnie zapisuje tę wartość wstecz do buforu po zakończeniu operacji. Jeśli bufor jest pusty, agent będzie czekał jednej z operacji pobierania wartość celu zapisania w buforze.  
  
 Poniższy przykład ogranicza liczbę jednoczesnych zadań dwa razy liczba wątków dostępnych sprzętu. Ta wartość jest dobry punkt wyjścia do użycia podczas eksperymentować nadsubskrypcji. Można użyć wartość, która pasuje do środowiska przetwarzania lub dynamicznie Zmień tę wartość na odpowiedź do rzeczywistego obciążenia.  
  
 [!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_1.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe na komputerze, który ma cztery procesory:  
  
```Output  
Downloading http://www.adatum.com/...  
Downloading http://www.adventure-works.com/...  
Downloading http://www.alpineskihouse.com/...  
Downloading http://www.cpandl.com/...  
Downloading http://www.cohovineyard.com/...  
Downloading http://www.cohowinery.com/...  
Downloading http://www.cohovineyardandwinery.com/...  
Downloading http://www.contoso.com/...  
Downloading http://www.consolidatedmessenger.com/...  
Downloading http://www.fabrikam.com/...  
Downloading http://www.fourthcoffee.com/...  
Downloading http://www.graphicdesigninstitute.com/...  
Downloading http://www.humongousinsurance.com/...  
Downloading http://www.litwareinc.com/...  
Downloading http://www.lucernepublishing.com/...  
Downloading http://www.margiestravel.com/...  
Downloading http://www.northwindtraders.com/...  
Downloading http://www.proseware.com/...  
Downloading http://www.fineartschool.net...  
Downloading http://www.tailspintoys.com/...  
Downloaded 1801040 bytes in 3276 ms.  
```  
  
 Przykład można uruchomić szybciej, gdy nadsubskrypcji jest włączone, ponieważ dodatkowe zadania są uruchamiane podczas innych zadań, poczekaj na zakończenie operacji ukryty.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `download-oversubscription.cpp` , a następnie uruchom jeden z następujących poleceń w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc / / MD /D "_AFXDLL" pobierania oversubscription.cpp**  
  
 **Cl.exe/ehsc/MT pobierania oversubscription.cpp**  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Zawsze wyłączyć nadsubskrypcji po nie są już potrzebne. Należy wziąć pod uwagę funkcję, która nie zapewnia obsługi wyjątku zgłoszonego przez inną funkcję. Jeśli nie wyłączysz nadsubskrypcji przed funkcja zwraca, żadnych dodatkowych działań równoległych będzie również oversubscribe bieżącego kontekstu.  
  
 Można użyć *inicjowania jest nabywania zasobów* wzorca (RAII), aby ograniczyć nadsubskrypcji do danego zakresu. W obszarze wzorzec RAII to struktura danych został przydzielony na stosie. Tej struktury danych inicjuje lub uzyskuje zasobu, gdy jest tworzony i niszczy lub zwalnia tego zasobu, gdy zostanie zniszczony struktury danych. Wzorzec RAII gwarantuje, że destruktor jest wywoływana przed opuszcza otaczającego zakresu. W związku z tym zasobu jest poprawnie zarządzany, jest zwracany wyjątek, lub gdy funkcja zawiera wiele `return` instrukcje.  
  
 W poniższym przykładzie zdefiniowano strukturę o nazwie `scoped_blocking_signal`. Konstruktor obiektu `scoped_blocking_signal` struktury włącza nadsubskrypcji i destruktor wyłącza nadsubskrypcji.  
  
 [!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_2.cpp)]  
  
 Poniższy przykład modyfikuje treści `download` metody RAII upewnij się, że nadsubskrypcji jest wyłączone, zanim funkcja zwraca wartość. Ta metoda zapewnia, że `download` metoda jest bezpieczne wyjątku.  
  
 [!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_3.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Konteksty](../../parallel/concrt/contexts.md)   
 [Context::Oversubscribe — metoda](reference/context-class.md#oversubscribe)


