---
title: 'Instrukcje: Używanie Nadsubskrypcji do przesuwania opóźnienia'
ms.date: 11/04/2016
helpviewer_keywords:
- oversubscription, using [Concurrency Runtime]
- using oversubscription [Concurrency Runtime]
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
ms.openlocfilehash: d74a081f71f044cab90a8e6fdc64530eaaf87ed8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257946"
---
# <a name="how-to-use-oversubscription-to-offset-latency"></a>Instrukcje: Używanie Nadsubskrypcji do przesuwania opóźnienia

Nadsubskrypcja może zwiększyć ogólną wydajność niektórych aplikacji, które zawiera zadania, które mają dużej ilości opóźnienia. W tym temacie pokazano, jak używanie nadsubskrypcji do opóźnienia, które jest spowodowany przez odczytywanie danych z połączeniem sieciowym.

## <a name="example"></a>Przykład

W tym przykładzie użyto [bibliotekę asynchronicznych agentów](../../parallel/concrt/asynchronous-agents-library.md) pobierać pliki z serwerami HTTP. `http_reader` Klasa pochodzi od [concurrency::agent](../../parallel/concrt/reference/agent-class.md) i używa komunikatów przekazywania do asynchronicznego odczytu nazwy adresu URL, których można pobrać.

`http_reader` Klasy używa [concurrency::task_group](reference/task-group-class.md) klasy, które można jednocześnie odczytać każdego pliku. Każde zadanie wywołuje [concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe) metody z `_BeginOversubscription` parametr **true** Aby włączyć nadsubskrypcję w bieżącym kontekście. Każde zadanie wykorzystuje następnie Microsoft Foundation Classes (MFC) [CInternetSession](../../mfc/reference/cinternetsession-class.md) i [CHttpFile](../../mfc/reference/chttpfile-class.md) klasy, aby pobrać plik. Na koniec każdego zadania wywołuje `Context::Oversubscribe` z `_BeginOversubscription` parametr **false** wyłączyć nadsubskrypcji.

Po włączeniu nadsubskrypcji środowisko uruchomieniowe tworzy jeden dodatkowy wątek do uruchamiania zadań. Każdy z tych wątków również oversubscribe bieżącego kontekstu, a tym samym utworzyć dodatkowe wątki. `http_reader` Klasy używa [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) obiektu, aby ograniczyć liczbę wątków, z których korzysta aplikacja. Agent inicjuje buforu ze stałą liczbą wartości tokenu. Dla każdej operacji pobierania agenta odczytuje wartość tokenu z buforu, zanim operacja rozpoczyna się, a następnie zapisuje wartości powrót do buforu po zakończeniu operacji. Jeśli bufor jest pusty, agent będzie czekał jednej z operacji pobierania do zapisania wartości z powrotem do buforu.

Poniższy przykład ogranicza liczbę jednoczesnych zadań dwa razy liczba wątków sprzętu. Ta wartość jest dobry punkt wyjścia do użycia podczas eksperymentować nadsubskrypcji. Można użyć wartość, która mieści się w środowisku przetwarzania lub dynamicznie zmieniać tej wartości, aby odpowiedzieć na rzeczywistego obciążenia.

[!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_1.cpp)]

Ten przykład generuje następujące dane wyjściowe na komputerze, który ma cztery procesory:

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

Przykład mogą działać szybciej po włączeniu nadsubskrypcji, ponieważ dodatkowe zadania są uruchamiane podczas gdy inne zadania, poczekaj na zakończenie operacji ukrytego.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `download-oversubscription.cpp` i następnie uruchom jeden z następujących poleceń w **Visual Studio Command Prompt** okna.

**cl.exe /EHsc /MD /D "_AFXDLL" download-oversubscription.cpp**

**Cl.exe/ehsc/MT pobierania oversubscription.cpp**

## <a name="robust-programming"></a>Niezawodne programowanie

Zawsze wyłączaj nadsubskrypcji po nie są już potrzebne. Należy wziąć pod uwagę funkcja, która nie obsługuje wyjątek, który jest generowany przez inną funkcję. Jeśli nie wyłączysz nadsubskrypcji zanim funkcja zwróci, wykonywania dodatkowej pracy równolegle będzie również oversubscribe bieżącego kontekstu.

Możesz użyć *inicjowania jest pozyskiwanie zasobów* wzorca (RAII), aby ograniczyć nadsubskrypcji do podanego zakresu. W obszarze wzór RAII to struktura danych jest przydzielany na stosie. Tej struktury danych inicjuje lub uzyskuje zasobu, gdy jest tworzony i niszczy lub zwalnia tego zasobu, kiedy niszczony jest struktury danych. Wzór RAII gwarantuje, że destruktor jest wywoływany przed zasięgu kończy działanie. W związku z tym, gdy wyjątek jest zgłaszany, lub gdy funkcja zawiera wiele zasobu jest poprawnie zarządzany `return` instrukcji.

W poniższym przykładzie zdefiniowano strukturę, która nosi nazwę `scoped_blocking_signal`. Konstruktor obiektu `scoped_blocking_signal` struktury włącza nadsubskrypcji i destruktor wyłącza nadsubskrypcji.

[!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_2.cpp)]

Poniższy przykład modyfikuje treści `download` metody Użyj RAII, aby upewnić się, że nadsubskrypcja jest wyłączone, zanim funkcja zwróci. Ta metoda zapewnia, że `download` metoda jest bezpieczna pod względem wyjątków.

[!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_3.cpp)]

## <a name="see-also"></a>Zobacz także

[Konteksty](../../parallel/concrt/contexts.md)<br/>
[Context::oversubscribe — metoda](reference/context-class.md#oversubscribe)
