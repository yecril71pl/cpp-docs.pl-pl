---
title: 'Przewodnik: Tworzenie aplikacji opartej o agentów'
ms.date: 11/04/2016
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 1d55c9879a3dd90bb4a40b61a3bf958dbe960bc3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290095"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Przewodnik: Tworzenie aplikacji opartej o agentów

W tym temacie opisano sposób tworzenia podstawowych aplikacji opartej o agentów. W tym instruktażu można utworzyć agenta, który asynchronicznie odczytuje dane z pliku tekstowego. Aplikacja używa algorytmu sumy kontrolnej Adler 32 do obliczania sumy kontrolnej zawartości tego pliku.

## <a name="prerequisites"></a>Wymagania wstępne

Należy zrozumieć następujące tematy w celu przeprowadzenia tego instruktażu:

- [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)

- [Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)

##  <a name="top"></a> Sekcje

W tym instruktażu pokazano, jak wykonywać następujące zadania:

- [Tworzenie aplikacji konsoli](#createapplication)

- [Tworzenie klasy file_reader](#createagentclass)

- [Korzystając z klasy file_reader w aplikacji](#useagentclass)

##  <a name="createapplication"></a> Tworzenie aplikacji konsoli

W tej sekcji przedstawiono sposób tworzenia aplikacji konsoli Visual C++, która odwołuje się pliki nagłówkowe, które ma być używany.

#### <a name="to-create-a-visual-c-application-by-using-the-win32-console-application-wizard"></a>Aby utworzyć aplikację Visual C++ przy użyciu kreatora aplikacji konsoli Win32

1. Na **pliku** menu, kliknij przycisk **New**, a następnie kliknij przycisk **projektu** do wyświetlenia **nowy projekt** okno dialogowe.

1. W **nowy projekt** okno dialogowe, wybierz opcję **Visual C++** w węźle **typów projektów** okienka, a następnie wybierz **Aplikacja konsoli Win32** w **szablony** okienka. Wpisz nazwę projektu, na przykład `BasicAgent`, a następnie kliknij przycisk **OK** do wyświetlenia **Kreatora aplikacji konsoli Win32**.

1. W **Kreatora aplikacji konsoli Win32** okno dialogowe, kliknij przycisk **Zakończ**.

1. W pliku stdafx.h należy dodać następujący kod.

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   Agents.h pliku nagłówka zawiera funkcje [concurrency::agent](../../parallel/concrt/reference/agent-class.md) klasy.

1. Sprawdź, czy aplikacja została pomyślnie utworzona, tworząc i uruchamiając go. Aby skompilować aplikację, na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom ją, klikając pozycję **Rozpocznij debugowanie** na **debugowania** menu.

[[Górnej](#top)]

##  <a name="createagentclass"></a> Tworzenie klasy file_reader

W tej sekcji przedstawiono sposób tworzenia `file_reader` klasy. Środowisko uruchomieniowe planuje każdego agenta w celu wykonania pracy w kontekście swój własny. W związku z tym można utworzyć agenta, który wykonuje pracę synchronicznie, ale współdziała z innymi składnikami asynchronicznie. `file_reader` Klasy odczytuje dane z danego pliku wejściowego i wysyła dane z tego pliku do składnika docelowej.

#### <a name="to-create-the-filereader-class"></a>Aby utworzyć klasę file_reader

1. Dodaj nowy plik nagłówkowy C++ do projektu. Aby to zrobić, kliknij prawym przyciskiem myszy **pliki nagłówkowe** w węźle **Eksploratora rozwiązań**, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy element**. W **szablony** okienku wybierz **plik nagłówka (.h)**. W **Dodaj nowy element** okno dialogowe, typ `file_reader.h` w **nazwa** pole, a następnie kliknij przycisk **Dodaj**.

1. W file_reader.h Dodaj następujący kod.

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. W file_reader.h, należy utworzyć klasę, która nosi nazwę `file_reader` który pochodzi od klasy `agent`.

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. Dodaj następujące elementy członkowskie danych do `private` części swojej klasy.

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   `_file_name` Element członkowski jest nazwą pliku, odczytująca agenta. `_target` Element członkowski jest [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) obiektu, że agent zapisuje zawartość pliku. `_error` Elementu członkowskiego zawiera wszelkie błędy występujące w cyklu życia agenta.

1. Dodaj następujący kod do `file_reader` konstruktorów `public` części `file_reader` klasy.

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   Ustawia każdego przeciążenia konstruktora `file_reader` składowych danych. Przeciążenia konstruktora drugiego i trzeciego umożliwia aplikacji do użycia określonego harmonogramu za pomocą agenta. Pierwsze przeciążenie używa domyślnego harmonogramu z agenta.

1. Dodaj `get_error` metody do sekcji publicznej `file_reader` klasy.

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   `get_error` Metoda pobiera wszelkie błędy występujące w cyklu życia agenta.

1. Implementowanie [concurrency::agent::run](reference/agent-class.md#run) method in Class metoda `protected` części swojej klasy.

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

`run` Metoda otwiera plik i odczytuje dane z niego. `run` Metoda używa obsługi wyjątków do przechwytywania błędów występujących podczas przetwarzania pliku.

   Każdorazowo, ta metoda odczytuje dane z pliku, wywoływanych przez nią [concurrency::asend](reference/concurrency-namespace-functions.md#asend) funkcję, aby wysyłać te dane do bufora docelowego. Pusty ciąg wysyła do jego bufor docelowy, aby wskazać koniec przetwarzania.

Pełna zawartość file_reader.h można znaleźć w poniższym przykładzie.

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[Górnej](#top)]

##  <a name="useagentclass"></a> Korzystając z klasy file_reader w aplikacji

W tej sekcji pokazano, jak używać `file_reader` klasy, aby odczytać zawartość pliku tekstowego. Ponadto przedstawiono sposób tworzenia [concurrency::call](../../parallel/concrt/reference/call-class.md) obiekt, który odbiera dane tego pliku, a następnie oblicza jego sumy kontrolnej Adler-32.

#### <a name="to-use-the-filereader-class-in-your-application"></a>Aby użyć klasy file_reader w aplikacji

1. W BasicAgent.cpp, Dodaj następujący kod `#include` instrukcji.

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. W BasicAgent.cpp, Dodaj następujący kod `using` dyrektywy.

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. W `_tmain` funkcji, Utwórz [concurrency::event](../../parallel/concrt/reference/event-class.md) obiekt, który sygnalizuje koniec przetwarzania.

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. Utwórz `call` obiekt, który aktualizuje sumę kontrolną, po odebraniu danych.

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   To `call` obiektu spowoduje także ustawienie `event` obiektu po odebraniu pusty ciąg do sygnalizowania zakończenia przetwarzania.

1. Tworzenie `file_reader` obiekt, który odczytuje jako plik i zapisuje zawartość tego pliku do `call` obiektu.

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. Uruchom agenta i poczekaj na zakończenie jego działania.

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. Poczekaj, aż `call` obiekt, aby otrzymywać wszystkie dane i Zakończ.

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. Sprawdź czytnik plików błędów. Jeśli żaden błąd nie wystąpił, obliczyć sumę końcowym Adler 32 i drukować sumę do konsoli.

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

Poniższy przykład przedstawia kompletny plik BasicAgent.cpp.

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

[[Górnej](#top)]

## <a name="sample-input"></a>Przykładowe dane wejściowe

To jest zawartość przykładowej text.txt pliku wejściowego:

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>Przykładowe dane wyjściowe

W przypadku użycia za pomocą przykładowe dane wejściowe, program generuje następujące wyniki:

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>Niezawodne programowanie

Aby zapobiec równoczesny dostęp do elementów członkowskich danych, zaleca się dodawania metod, które wykonują prace na `protected` lub `private` części swojej klasy. Tylko Dodaj metody, które wysyłać ani odbierać wiadomości do lub z agenta aby `public` części swojej klasy.

Zawsze wywołuj [concurrency::agent:: gotowe](reference/agent-class.md#done) metodę, aby przenieść agenta do stanu ukończenia. Zazwyczaj ta metoda jest wywoływana przed zwróceniem z `run` metody.

## <a name="next-steps"></a>Następne kroki

Inny przykład aplikacji opartej o agentów, zobacz [instruktażu: Za pomocą, aby zapobiec zakleszczeniu](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

## <a name="see-also"></a>Zobacz także

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)<br/>
[Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Przewodnik: korzystanie ze złączy w celu zapobiegania zakleszczeniom](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
