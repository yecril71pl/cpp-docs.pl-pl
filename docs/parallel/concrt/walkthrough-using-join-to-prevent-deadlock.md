---
title: "Wskazówki: Używanie w celu zapobiegania zakleszczeniom | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- preventing deadlock with joins [Concurrency Runtime]
- deadlock, preventing [Concurrency Runtime]
- non-greedy joins, example
- join class, example
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3553ac8948e10271da449356bde20d2a9ae4378b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-using-join-to-prevent-deadlock"></a>Wskazówki: korzystanie ze złączy w celu zapobiegania zakleszczeniom
W tym temacie używa lokali problem philosophers ilustrujący sposób użycia [concurrency::join](../../parallel/concrt/reference/join-class.md) klasę, aby zapobiec zakleszczenie w aplikacji. W aplikacji *zakleszczenie* występuje, gdy dwie lub więcej procesów każdego przechowywania zasobu i wzajemnie poczekaj, aż inny proces zwolnić innego zasobu.  
  
 Lokali problem philosophers jest określonych przykładem ogólne zbiór problemów, które mogą wystąpić, gdy zestaw zasobów są współużytkowane przez wiele współbieżnych procesów.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przed skorzystaniem z tego przewodnika, przeczytaj następujące tematy:  
  
- [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)  
  
- [Wskazówki: Tworzenie aplikacji opartej o agentów](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)  
  
- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)  
  
- [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)  
  
- [Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)  
  
##  <a name="top"></a>Sekcje  
 Ten przewodnik zawiera następujące sekcje:  
  
- [Lokali Problem Philosophers](#problem)  
  
- [Implementacja prostego](#deadlock)  
  
- [Przy użyciu w celu zapobiegania zakleszczeniom](#solution)  
  
##  <a name="problem"></a>Lokali Problem Philosophers  
 Lokali problem philosophers przedstawiono, jak zakleszczenie występuje w aplikacji. Ten problem pięć philosophers znajdują się w tabeli round. Każdy philosopher przełącza między myśląc i jedzenia. Każdy philosopher musi udostępniać chopstick po sąsiada po lewej stronie, druga chopstick z sąsiada po prawej stronie. Na poniższej ilustracji przedstawiono ten układ.  
  
 ![Problem Philosophers jadalni](../../parallel/concrt/media/dining_philosophersproblem.png "dining_philosophersproblem")  
  
 Aby jeść, philosopher musi posiadać dwie chopsticks. Jeśli co philosopher zawiera tylko jeden chopstick i oczekuje na inną, następnie jeść może nie philosopher, a wszystkie blokować go.  
  
 [[Górnej](#top)]  
  
##  <a name="deadlock"></a>Implementacja prostego  
 W poniższym przykładzie przedstawiono prosty stosowania lokali problem philosophers. `philosopher` Klasy, która jest pochodną [concurrency::agent](../../parallel/concrt/reference/agent-class.md), umożliwia każdego philosopher, które będą działać niezależnie. W przykładzie użyto udostępnionej macierzy [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) obiektów, aby dać każdej `philosopher` obiekt wyłącznego dostępu do pary chopsticks.  
  
 Do wykonania na ilustracji, powiązania `philosopher` klasa reprezentuje jeden philosopher. `int` Każdego chopstick reprezentuje zmienną. `critical_section` Obiektów służyć jako posiadaczy, na których chopsticks rest. `run` Metody symuluje życia philosopher. `think` Metody symuluje czynność planowania i `eat` metody symuluje czynność jedzenia.  
  
 A `philosopher` obiektu blokuje zarówno `critical_section` obiektów, aby symulować usunięcie chopsticks od posiadaczy przed wywołuje `eat` metody. Po wywołaniu `eat`, `philosopher` obiektu zwraca chopsticks posiadaczom przez ustawienie `critical_section` obiektów z powrotem do stanu odblokowane.  
  
 `pickup_chopsticks` Przedstawiono metody może mieć miejsce zakleszczenia. Jeśli co `philosopher` obiekt uzyskuje dostęp do jednego z blokad, a następnie nie `philosopher` obiektu można kontynuować, ponieważ inne blokady jest kontrolowany przez inną `philosopher` obiektu.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
  
### <a name="code"></a>Kod  
 [!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_1.cpp)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `philosophers-deadlock.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc philosophers-deadlock.cpp**  
  
 [[Górnej](#top)]  
  
##  <a name="solution"></a>Przy użyciu w celu zapobiegania zakleszczeniom  
 W tej sekcji pokazano, jak użyć funkcji przekazywania wiadomości i buforów komunikatów, aby wykluczyć ryzyko zakleszczenia.  
  
 Do powiązania w tym przykładzie do tego wcześniej `philosopher` klasy zastępuje wszystkie `critical_section` obiektu za pomocą [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) obiektu i `join` obiektu. `join` Obiektu służy jako kryterium, która dostarcza chopsticks do philosopher.  
  
 W tym przykładzie użyto `unbounded_buffer` klasy, ponieważ gdy element docelowy otrzymuje komunikat z `unbounded_buffer` obiekt wiadomość zostanie usunięta z kolejki wiadomości. Dzięki temu `unbounded_buffer` obiekt przechowujący chopstick komunikat z informacją, że jest dostępny. `unbounded_buffer` Obiekt przechowujący żaden komunikat wskazuje, że chopstick jest używana.  
  
 W tym przykładzie użyto niezachłanne `join` obiektu, ponieważ niezachłanne złączenia daje każdego `philosopher` obiekt dostęp do obu chopsticks tylko wtedy, gdy oba `unbounded_buffer` obiekty zawierają wiadomości. Zachłanne złączenia nie uniemożliwi zakleszczenia, ponieważ zachłanne złączenia akceptuje wiadomości, gdy tylko staną się dostępne. Zakleszczenie może wystąpić, jeśli jest to wszystkie intensywnie `join` obiekty wyświetlony jeden z komunikatów, ale czekają na innych stanie się dostępne.  
  
 Aby uzyskać więcej informacji na temat intensywnie i niezachłanne sprzężeń oraz różnice między różne typy buforu komunikatu, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md).  
  
#### <a name="to-prevent-deadlock-in-this-example"></a>W celu uniknięcia zakleszczenia w tym przykładzie  
  
1.  Usuń poniższy kod w przykładzie.  
  
 [!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_2.cpp)]  
  
2.  Zmień typ `_left` i `_right` elementów członkowskich danych `philosopher` klasy do `unbounded_buffer`.  
  
 [!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_3.cpp)]  
  
3.  Modyfikowanie `philosopher` konstruktora, aby wykonać `unbounded_buffer` obiekty jako jego parametrów.  
  
 [!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_4.cpp)]  
  
4.  Modyfikowanie `pickup_chopsticks` niezachłanne metodę `join` obiektu do odbierania wiadomości z buforów komunikatów, dla obu chopsticks.  
  
 [!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_5.cpp)]  
  
5.  Modyfikowanie `putdown_chopsticks` metodę, aby zwolnić dostęp do chopsticks, wysyłając wiadomość do buforów komunikatów, dla obu chopsticks.  
  
 [!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_6.cpp)]  
  
6.  Modyfikowanie `run` metody do przechowywania wyników `pickup_chopsticks` — metoda oraz przekazywanie tych wyników, aby `putdown_chopsticks` metody.  
  
 [!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_7.cpp)]  
  
7.  Modyfikowanie deklaracja `chopsticks` zmiennej w `wmain` funkcję, która ma być tablicą `unbounded_buffer` obiektów, aby pomieścić każdego jeden komunikat.  
  
 [!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_8.cpp)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniżej pokazano przykład używającej niezachłanne `join` obiektów, aby wyeliminować ryzyko zakleszczenia.  
  
### <a name="code"></a>Kod  
 [!code-cpp[concrt-philosophers-join#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_9.cpp)]  
  
### <a name="comments"></a>Komentarze  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```Output  
aristotle ate 50 times.  
descartes ate 50 times.  
hobbes ate 50 times.  
socrates ate 50 times.  
plato ate 50 times.  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `philosophers-join.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc philosophers-join.cpp**  
  
 [[Górnej](#top)]  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność środowiska wykonawczego — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)   
 [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)   
 [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)   
 [Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)
