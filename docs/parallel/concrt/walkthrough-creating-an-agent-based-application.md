---
title: 'Wskazówki: tworzenie aplikacji opartej o agentów'
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 4e67b3fc3363955ae02973847912c021eca95ded
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219485"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Wskazówki: tworzenie aplikacji opartej o agentów

W tym temacie opisano sposób tworzenia podstawowej aplikacji opartej na agencie. W tym instruktażu można utworzyć agenta, który asynchronicznie odczytuje dane z pliku tekstowego. Aplikacja używa algorytmu sumy kontrolnej Adler-32 do obliczania sumy kontrolnej zawartości tego pliku.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, należy zapoznać się z następującymi tematami:

- [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)

- [Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)

## <a name="sections"></a><a name="top"></a>Poszczególne

W tym instruktażu przedstawiono sposób wykonywania następujących zadań:

- [Tworzenie aplikacji konsoli](#createapplication)

- [Tworzenie klasy file_reader](#createagentclass)

- [Korzystanie z klasy file_reader w aplikacji](#useagentclass)

## <a name="creating-the-console-application"></a><a name="createapplication"></a>Tworzenie aplikacji konsolowej

W tej sekcji pokazano, jak utworzyć aplikację konsolową w języku C++, która odwołuje się do plików nagłówkowych, które będą używane w programie. Początkowe kroki różnią się w zależności od używanej wersji programu Visual Studio. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj kontrolki selektora **wersji** . Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>Aby utworzyć aplikację konsolową w języku C++ w programie Visual Studio 2019

1. Z menu głównego wybierz pozycję **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Tworzenie nowego projektu** .

1. W górnej części okna dialogowego Ustaw **Język** na **C++**, ustaw **platformę** na **Windows**i ustaw **Typ projektu** na **Console**.

1. Z listy filtrowane typy projektów wybierz pozycję **Aplikacja konsolowa** , a następnie wybierz przycisk **dalej**. Na następnej stronie wprowadź `BasicAgent` jako nazwę projektu i określ lokalizację projektu w razie potrzeby.

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt.

1. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań**i wybierz polecenie **Właściwości**. We **właściwościach konfiguracji**prekompilowane nagłówki prekompilowanego  >  **nagłówka C/C++**  >  **Precompiled Headers**  >  **Precompiled header** wybierz pozycję **Utwórz**.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-c-console-application-in-visual-studio-2017-and-earlier"></a>Aby utworzyć aplikację konsolową w języku C++ w programie Visual Studio 2017 i starszych

1. W menu **plik** kliknij pozycję **Nowy**, a następnie kliknij pozycję **projekt** , aby wyświetlić okno dialogowe **Nowy projekt** .

1. W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C++** w okienku **typy projektów** , a następnie wybierz pozycję **aplikacja konsoli Win32** w okienku **Szablony** . Wpisz nazwę projektu, na przykład, `BasicAgent` a następnie kliknij przycisk **OK** , aby wyświetlić **Kreatora aplikacji konsolowej Win32**.

1. W oknie dialogowym **Kreator aplikacji konsolowej Win32** kliknij przycisk **Zakończ**.

::: moniker-end

1. W *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i starszych) Dodaj następujący kod:

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   Plik nagłówkowy. h zawiera funkcje klasy [concurrency:: Agent](../../parallel/concrt/reference/agent-class.md) .

1. Sprawdź, czy aplikacja została utworzona pomyślnie, kompilując ją i uruchamiając. Aby skompilować aplikację, w menu **kompilacja** kliknij polecenie **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom aplikację, klikając polecenie **Rozpocznij debugowanie** w menu **debugowanie** .

[[Top](#top)]

## <a name="creating-the-file_reader-class"></a><a name="createagentclass"></a>Tworzenie klasy file_reader

W tej sekcji pokazano, jak utworzyć `file_reader` klasę. Środowisko uruchomieniowe planuje wykonanie pracy we własnym kontekście przez każdego agenta. W związku z tym można utworzyć agenta, który wykonuje zadania synchronicznie, ale współdziała z innymi składnikami asynchronicznie. `file_reader`Klasa odczytuje dane z danego pliku wejściowego i wysyła dane z tego pliku do danego składnika docelowego.

#### <a name="to-create-the-file_reader-class"></a>Aby utworzyć klasę file_reader

1. Dodaj nowy plik nagłówkowy C++ do projektu. Aby to zrobić, kliknij prawym przyciskiem myszy węzeł **pliki nagłówkowe** w **Eksplorator rozwiązań**, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy element**. W okienku **Szablony** wybierz pozycję **plik nagłówka (. h)**. W oknie dialogowym **Dodaj nowy element** wpisz `file_reader.h` w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.

1. W file_reader. h Dodaj następujący kod.

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. W file_reader. h Utwórz klasę o nazwie `file_reader` , która pochodzi od `agent` .

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. Dodaj następujące elementy członkowskie danych do **`private`** sekcji klasy.

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   `_file_name`Element członkowski jest nazwą pliku, z której odczytuje Agent. `_target`Element członkowski jest obiektem [concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md) , do którego Agent zapisuje zawartość pliku. `_error`Składowa zawiera dowolny błąd występujący w trakcie okresu istnienia agenta.

1. Dodaj następujący kod dla `file_reader` konstruktorów do **`public`** sekcji `file_reader` klasy.

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   Każde przeciążenie konstruktora ustawia `file_reader` elementy członkowskie danych. Drugie i trzecie przeciążenie konstruktora umożliwia aplikacji użycie określonego harmonogramu z agentem. Pierwsze Przeciążenie używa domyślnego harmonogramu z agentem.

1. Dodaj `get_error` metodę do publicznej sekcji `file_reader` klasy.

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   `get_error`Metoda pobiera każdy błąd występujący w trakcie okresu istnienia agenta.

1. Zaimplementuj metodę [concurrency:: Agent:: Run](reference/agent-class.md#run) w **`protected`** sekcji klasy.

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

`run`Metoda otwiera plik i odczytuje z niego dane. `run`Metoda używa obsługi wyjątków do przechwytywania błędów występujących podczas przetwarzania plików.

   Za każdym razem, gdy ta metoda odczytuje dane z pliku, wywołuje funkcję [concurrency:: asend](reference/concurrency-namespace-functions.md#asend) , aby wysłać te dane do bufora docelowego. Wysyła pusty ciąg do buforu docelowego, aby wskazać koniec przetwarzania.

Poniższy przykład pokazuje kompletną zawartość file_reader. h.

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[Top](#top)]

## <a name="using-the-file_reader-class-in-the-application"></a><a name="useagentclass"></a>Korzystanie z klasy file_reader w aplikacji

W tej sekcji pokazano, jak za pomocą `file_reader` klasy odczytać zawartość pliku tekstowego. Przedstawiono w nim również sposób tworzenia obiektu [concurrency:: Call](../../parallel/concrt/reference/call-class.md) , który odbiera dane tego pliku i oblicza sumę kontrolną Adler-32.

#### <a name="to-use-the-file_reader-class-in-your-application"></a>Aby użyć klasy file_reader w aplikacji

1. W BasicAgent. cpp Dodaj następującą `#include` instrukcję.

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. W BasicAgent. cpp Dodaj następujące **`using`** dyrektywy.

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. W `_tmain` funkcji Utwórz obiekt [concurrency:: Event](../../parallel/concrt/reference/event-class.md) , który sygnalizuje koniec przetwarzania.

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. Utwórz `call` obiekt, który aktualizuje sumę kontrolną po odebraniu danych.

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   Ten `call` obiekt ustawia również `event` obiekt, gdy odbierze pusty ciąg, aby sygnalizować zakończenie przetwarzania.

1. Utwórz `file_reader` obiekt, który odczytuje z pliku test.txt i zapisuje zawartość tego pliku do `call` obiektu.

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. Uruchom agenta i poczekaj na jego zakończenie.

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. Poczekaj, aż `call` obiekt odbierze wszystkie dane i zakończy.

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. Sprawdź, czy czytnik plików nie ma błędów. Jeśli nie wystąpił błąd, Oblicz końcową sumę Adler-32 i wydrukuj sumę w konsoli.

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

Poniższy przykład pokazuje kompletny plik. cpp BasicAgent.

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

[[Top](#top)]

## <a name="sample-input"></a>Przykładowe dane wejściowe

Jest to Przykładowa zawartość pliku wejściowego, text.txt:

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>Przykładowe dane wyjściowe

W przypadku użycia z przykładowymi danymi wejściowymi ten program tworzy następujące dane wyjściowe:

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>Niezawodne programowanie

Aby zapobiec współbieżnemu dostępowi do elementów członkowskich danych, zalecamy dodanie metod, które wykonują prace **`protected`** do **`private`** sekcji lub klasy. Należy dodawać tylko metody, które wysyłają lub odbierają wiadomości do lub z agenta do **`public`** sekcji klasy.

Zawsze Wywołaj metodę [concurrency:: Agent::d jedną](reference/agent-class.md#done) metodą, aby przenieść agenta do stanu ukończone. Ta metoda jest zazwyczaj wywoływana przed zwróceniem z `run` metody.

## <a name="next-steps"></a>Następne kroki

Aby zapoznać się z innym przykładem aplikacji opartej na agencie, zobacz [Przewodnik: Używanie funkcji join w celu zapobiegania zakleszczeniom](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

## <a name="see-also"></a>Zobacz także

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)<br/>
[Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Przewodnik: używanie sprzężenia w celu zapobiegania zakleszczeniom](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
