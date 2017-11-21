---
title: "Wskazówki: Tworzenie aplikacji opartej o agentów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 245952bd8dfb9acc8fc8550955232a30b9dbfe9f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Wskazówki: tworzenie aplikacji opartej o agentów
W tym temacie opisano sposób tworzenia podstawowej aplikacji opartej o agentów. W ramach tego przewodnika można utworzyć agenta asynchronicznie odczytuje dane z pliku tekstowego. Aplikacja używa algorytmu sumy kontrolnej Adler 32 do obliczania sum kontrolnych zawartość tego pliku.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Należy poznać następujące tematy w tym przewodniku:  
  
- [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)  
  
- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)  
  
- [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)  
  
- [Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)  
  
##  <a name="top"></a>Sekcje  
 W tym przewodniku pokazano, jak wykonać następujące zadania:  
  
- [Tworzenie aplikacji konsoli](#createapplication)  
  
- [Tworzenie file_reader — klasa](#createagentclass)  
  
- [W aplikacji przy użyciu file_reader — klasa](#useagentclass)  
  
##  <a name="createapplication"></a>Tworzenie aplikacji konsoli  
 W tej sekcji przedstawiono sposób tworzenia aplikacji konsoli Visual C++, która odwołuje się do pliki nagłówkowe, które ma być używany.  
  
#### <a name="to-create-a-visual-c-application-by-using-the-win32-console-application-wizard"></a>Aby utworzyć aplikację Visual C++ przy użyciu kreatora aplikacji konsoli Win32  
  
1.  Na **pliku** menu, kliknij przycisk **nowy**, a następnie kliknij przycisk **projektu** do wyświetlenia **nowy projekt** okno dialogowe.  
  
2.  W **nowy projekt** okno dialogowe, wybierz opcję **Visual C++** w węźle **typy projektów** okienka, a następnie wybierz **aplikacji konsoli Win32** w **szablony** okienka. Wpisz nazwę projektu, na przykład `BasicAgent`, a następnie kliknij przycisk **OK** do wyświetlenia **Kreatora aplikacji konsoli Win32**.  
  
3.  W **Kreatora aplikacji konsoli Win32** okno dialogowe, kliknij przycisk **Zakończ**.  
  
4.  W pliku stdafx.h Dodaj następujący kod.  
  
 [!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]  
  
     Agents.h pliku nagłówka zawiera funkcje [concurrency::agent](../../parallel/concrt/reference/agent-class.md) klasy.  
  
5.  Sprawdź, czy aplikacja została pomyślnie utworzona tworzenia i uruchamiania go. Do skompilowania aplikacji, na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Jeśli aplikacja tworzy się pomyślnie, uruchom aplikację, klikając **Rozpocznij debugowanie** na **debugowania** menu.  
  
 [[Górnej](#top)]  
  
##  <a name="createagentclass"></a>Tworzenie file_reader — klasa  
 W tej sekcji przedstawiono sposób tworzenia `file_reader` klasy. Środowisko uruchomieniowe planuje każdego agenta do wykonywania pracy w kontekście własny. W związku z tym można utworzyć agenta, który wykonuje pracę synchronicznie, ale wchodzi w interakcję z innymi składnikami asynchronicznie. `file_reader` Klasy odczytuje dane z danym pliku wejściowego i wysyła dane z tego pliku do elementu docelowego podanego składnika.  
  
#### <a name="to-create-the-filereader-class"></a>Aby utworzyć klasę file_reader  
  
1.  Dodaj nowy plik nagłówka C++ do projektu. Aby to zrobić, kliknij prawym przyciskiem myszy **pliki nagłówkowe** w węźle **Eksploratora rozwiązań**, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy element**. W **szablony** okienku wybierz **plik nagłówków (.h)**. W **Dodaj nowy element** okno dialogowe, typ `file_reader.h` w **nazwa** a następnie kliknij przycisk **Dodaj**.  
  
2.  W file_reader.h Dodaj następujący kod.  
  
 [!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]  
  
3.  W file_reader.h, Utwórz klasę o nazwie `file_reader` która pochodzi z `agent`.  
  
 [!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]  
  
4.  Dodaj następujące elementy członkowskie danych do `private` sekcji klasy.  
  
 [!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]  
  
     `_file_name` Element członkowski jest nazwa pliku odczytująca agenta. `_target` Element członkowski jest [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) obiektów, że agent zapisuje zawartość pliku. `_error` Elementu członkowskiego zawiera wszelkie błędy występujące w okresie obowiązywania agenta.  
  
5.  Dodaj następujący kod do `file_reader` konstruktorów `public` sekcji `file_reader` klasy.  
  
 [!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]  
  
     Ustawia każdego przeładowania konstruktora `file_reader` elementy członkowskie danych. Przeładowania konstruktora drugiego i trzeciego umożliwia aplikacji można użyć określonego harmonogramu z agenta. Pierwszy przeciążenia używa domyślnego harmonogramu z agenta.  
  
6.  Dodaj `get_error` metody do sekcji publicznego `file_reader` klasy.  
  
 [!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]  
  
     `get_error` Metoda pobiera wszelkie błędy występujące w okresie obowiązywania agenta.  
  

7.  Implementowanie [concurrency::agent::run](reference/agent-class.md#run) metoda `protected` sekcji klasy.  

  
 [!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]  
  
`run` Metoda otwiera plik i odczytuje dane z niego. `run` Metoda używa obsługi wyjątków do przechwytywania błędów występujących podczas przetwarzania pliku.  
  
   Zawsze, ta metoda odczytuje dane z pliku, wywołuje [concurrency::asend](reference/concurrency-namespace-functions.md#asend) funkcja do wysyłania danych do buforu docelowego. Pusty ciąg wysyła do docelowego buforu wskazująca na zakończenie przetwarzania.  

  
 W poniższym przykładzie przedstawiono Pełna zawartość file_reader.h.  
  
 [!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]  
  
 [[Górnej](#top)]  
  
##  <a name="useagentclass"></a>W aplikacji przy użyciu file_reader — klasa  
 W tej sekcji przedstawiono sposób użycia `file_reader` klasy można odczytać zawartości pliku tekstowego. Przedstawiono również sposób tworzenia [concurrency::call](../../parallel/concrt/reference/call-class.md) obiekt, który odbiera dane tego pliku, a następnie oblicza sumy kontrolnej jego Adler-32.  
  
#### <a name="to-use-the-filereader-class-in-your-application"></a>Aby użyć klasy file_reader w aplikacji  
  
1.  W BasicAgent.cpp, Dodaj następujący `#include` instrukcji.  
  
 [!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]  
  
2.  W BasicAgent.cpp, Dodaj następujący `using` dyrektywy.  
  
 [!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]  
  
3.  W `_tmain` funkcji, należy utworzyć [concurrency::event](../../parallel/concrt/reference/event-class.md) obiekt, który sygnalizuje koniec przetwarzania.  
  
 [!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]  
  
4.  Utwórz `call` obiekt, który aktualizuje sumę kontrolną, gdy odbiera dane.  
  
 [!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]  
  
     To `call` obiektu również ustawia `event` obiektu, gdy odbierze pusty ciąg, która sygnalizuje koniec przetwarzania.  
  
5.  Utwórz `file_reader` test.txt pliku odczytuje i zapisuje zawartość tego pliku do obiektu `call` obiektu.  
  
 [!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]  
  
6.  Uruchom agenta, a następnie zaczekaj na jego zakończenie.  
  
 [!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]  
  
7.  Poczekaj, aż `call` obiekt, aby odbierać wszystkie dane i Zakończ.  
  
 [!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]  
  
8.  Sprawdź czytnika plików błędów. Jeśli nie wystąpił żaden błąd, obliczenia złożenie wyników Adler 32 i drukowanie sum do konsoli.  
  
 [!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]  
  
 Poniższy przykład przedstawia pełny plik BasicAgent.cpp.  
  
 [!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]  
  
 [[Górnej](#top)]  
  
## <a name="sample-input"></a>Przykładowe dane wejściowe  
 To przykładowe zawartość text.txt pliku wejściowego:  
  
```Output  
The quick brown fox  
jumps  
over the lazy dog  
```  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
 W przypadku użycia z przykładowe dane wejściowe, ten program tworzy następujące dane wyjściowe:  
  
```Output  
Adler-32 sum is fefb0d75  
```  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Aby zapobiec równoczesny dostęp do elementów członkowskich danych, zaleca się dodanie metody, które współpracują w celu wykonania `protected` lub `private` sekcji klasy. Metody, które wysyłać ani odbierać wiadomości do lub z agenta, aby dodać tylko `public` sekcji klasy.  
  

 Wywoływanie zawsze [concurrency::agent:: gotowe](reference/agent-class.md#done) metodę, aby przenieść agenta do stanu ukończenia. Zwykle ta metoda jest wywoływana przed zwróceniem z `run` metody.  

  
## <a name="next-steps"></a>Następne kroki  
 Na przykład innej aplikacji opartej o agentów zobacz [wskazówki: przy użyciu w celu zapobiegania zakleszczeniom](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)   
 [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)   
 [Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)   
 [Wskazówki: Używanie w celu zapobiegania zakleszczeniom](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)

