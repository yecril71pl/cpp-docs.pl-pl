---
title: 'Wskazówki: tworzenie aplikacji opartej o agentów'
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 20197786e3d3c2d34d29af748c1cc073902cf70d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377456"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Wskazówki: tworzenie aplikacji opartej o agentów

W tym temacie opisano sposób tworzenia podstawowej aplikacji opartej na agentach. W tym instruktażu można utworzyć agenta, który odczytuje dane z pliku tekstowego asynchronicznie. Aplikacja używa algorytmu sumy kontrolnej Adler-32 do obliczania sumy kontrolnej zawartości tego pliku.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, musisz zrozumieć następujące tematy:

- [Środki asynchroniczne](../../parallel/concrt/asynchronous-agents.md)

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkcje przekazywania wiadomości](../../parallel/concrt/message-passing-functions.md)

- [Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)

## <a name="sections"></a><a name="top"></a>Sekcje

W tym przewodniku pokazano, jak wykonać następujące zadania:

- [Tworzenie aplikacji konsoli](#createapplication)

- [Tworzenie klasy file_reader](#createagentclass)

- [Korzystanie z klasy file_reader w aplikacji](#useagentclass)

## <a name="creating-the-console-application"></a><a name="createapplication"></a>Tworzenie aplikacji konsoli

W tej sekcji pokazano, jak utworzyć aplikację konsoli Języka C++, która odwołuje się do plików nagłówkowych, które będą używane przez program. Początkowe kroki różnią się w zależności od używanej wersji programu Visual Studio. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj formantu selektor **wersji.** Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>Aby utworzyć aplikację konsoli języka C++ w programie Visual Studio 2019

1. Z menu głównego wybierz polecenie **Plik** > **nowego** > **projektu,** aby otworzyć okno **dialogowe Tworzenie nowego projektu.**

1. W górnej części okna dialogowego ustaw **język** na **C++,** ustaw **platformę** na **Windows**i ustaw **typ projektu** na **Konsola**.

1. Z filtru listy typów projektów wybierz pozycję **Aplikacja konsoli,** a następnie wybierz pozycję **Dalej**. Na następnej stronie `BasicAgent` wprowadź jako nazwę projektu i określ lokalizację projektu w razie potrzeby.

1. Wybierz przycisk **Utwórz,** aby utworzyć projekt.

1. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań**i wybierz polecenie **Właściwości**. W obszarze **Właściwości** > konfiguracji Wstępnie**skompilowane nagłówki** > **C/C++** > **wybierz** pozycję **Utwórz**.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-c-console-application-in-visual-studio-2017-and-earlier"></a>Aby utworzyć aplikację konsoli języka C++ w programie Visual Studio 2017 i wcześniejszych

1. W menu **Plik** kliknij polecenie **Nowy**, a następnie kliknij polecenie **Projekt,** aby wyświetlić okno dialogowe **Nowy projekt.**

1. W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C++** w okienku **Typy projektu,** a następnie wybierz pozycję **Aplikacja konsoli Win32** w okienku **Szablony.** Wpisz nazwę projektu, na przykład `BasicAgent`, a następnie kliknij przycisk **OK,** aby wyświetlić **Kreatora aplikacji konsoli Win32**.

1. W oknie dialogowym **Kreator aplikacji konsoli Win32** kliknij przycisk **Zakończ**.

::: moniker-end

1. W *programie pch.h* (*stdafx.h* w programie Visual Studio 2017 i wcześniejszych) dodaj następujący kod:

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   Plik nagłówka agents.h zawiera funkcje [współbieżności::agent](../../parallel/concrt/reference/agent-class.md) klasy.

1. Sprawdź, czy aplikacja została pomyślnie utworzona przez jej utworzenie i uruchomienie. Aby utworzyć aplikację, w menu **Kompilacja** kliknij polecenie **Build Solution**. Jeśli aplikacja tworzy pomyślnie, uruchom aplikację, klikając **przycisk Rozpocznij debugowanie** w menu **debugowania.**

[[Góra](#top)]

## <a name="creating-the-file_reader-class"></a><a name="createagentclass"></a>Tworzenie klasy file_reader

W tej sekcji pokazano, jak utworzyć `file_reader` klasę. Środowisko wykonawcze planuje każdego agenta do wykonywania pracy w swoim własnym kontekście. W związku z tym można utworzyć agenta, który wykonuje pracę synchronicznie, ale współdziała z innymi składnikami asynchronicznie. Klasa `file_reader` odczytuje dane z danego pliku wejściowego i wysyła dane z tego pliku do danego składnika docelowego.

#### <a name="to-create-the-file_reader-class"></a>Aby utworzyć klasę file_reader

1. Dodaj nowy plik nagłówka języka C++ do projektu. W tym celu kliknij prawym przyciskiem myszy węzeł **Pliki nagłówków** w **Eksploratorze rozwiązań**, kliknij polecenie **Dodaj**, a następnie kliknij polecenie **Nowy element**. W okienku **Szablony** wybierz pozycję **Plik nagłówka (h)**. W oknie dialogowym Dodawanie `file_reader.h` nowego **elementu** wpisz pole **Nazwa,** a następnie kliknij pozycję **Dodaj**.

1. W file_reader.h dodaj następujący kod.

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. W file_reader.h utwórz klasę o nazwie, `file_reader` która `agent`pochodzi od pliku .

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. Dodaj następujące elementy członkowskie `private` danych do sekcji klasy.

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   Element `_file_name` członkowski jest nazwą pliku, z których agent odczytuje. Element `_target` członkowski jest [współbieżność::ITarget](../../parallel/concrt/reference/itarget-class.md) obiektu, który agent zapisuje zawartość pliku. Element `_error` członkowski zawiera wszelkie błędy, które występują w okresie życia agenta.

1. Dodaj następujący kod `file_reader` dla konstruktorów do `public` sekcji `file_reader` klasy.

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   Każde przeciążenie konstruktora ustawia elementy `file_reader` członkowskie danych. Przeciążenie drugiego i trzeciego konstruktora umożliwia aplikacji użycie określonego harmonogramu z agentem. Pierwsze przeciążenie używa domyślnego harmonogramu z agentem.

1. Dodaj `get_error` metodę do sekcji publicznej `file_reader` klasy.

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   Metoda `get_error` pobiera każdy błąd, który występuje w okresie życia agenta.

1. Zaimplementuj metodę [współbieżności::agent::run](reference/agent-class.md#run) w `protected` sekcji klasy.

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

Metoda `run` otwiera plik i odczytuje z niego dane. Metoda `run` używa obsługi wyjątków do przechwytywania błędów, które występują podczas przetwarzania plików.

   Za każdym razem, gdy ta metoda odczytuje dane z pliku, wywołuje funkcję [współbieżności::asend,](reference/concurrency-namespace-functions.md#asend) aby wysłać te dane do buforu docelowego. Wysyła pusty ciąg do buforu docelowego, aby wskazać koniec przetwarzania.

Poniższy przykład przedstawia pełną zawartość file_reader.h.

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[Góra](#top)]

## <a name="using-the-file_reader-class-in-the-application"></a><a name="useagentclass"></a>Korzystanie z klasy file_reader w aplikacji

W tej sekcji pokazano, jak używać `file_reader` klasy do odczytu zawartości pliku tekstowego. Pokazuje również, jak utworzyć [współbieżność::call](../../parallel/concrt/reference/call-class.md) obiektu, który odbiera te dane pliku i oblicza jego sumy kontrolnej Adler-32.

#### <a name="to-use-the-file_reader-class-in-your-application"></a>Aby użyć klasy file_reader w aplikacji

1. W basicagent.cpp dodaj `#include` następującą instrukcję.

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. W basicagent.cpp dodaj `using` następujące dyrektywy.

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. W `_tmain` funkcji utwórz [współbieżność::event](../../parallel/concrt/reference/event-class.md) obiektu, który sygnalizuje koniec przetwarzania.

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. Utwórz `call` obiekt, który aktualizuje sumę kontrolną po odebraniu danych.

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   Ten `call` obiekt ustawia `event` również obiekt po odebraniu pustego ciągu, aby zasygnalizować koniec przetwarzania.

1. Utwórz `file_reader` obiekt, który odczytuje plik test.txt i zapisuje `call` zawartość tego pliku do obiektu.

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. Uruchom agenta i poczekaj, aż zakończy się.

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. Poczekaj, `call` aż obiekt odbierze wszystkie dane i zakończy.

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. Sprawdź czytnik plików pod kątem błędów. Jeśli nie wystąpił żaden błąd, oblicz ostateczną sumę Adler-32 i wydrukuj sumę na konsoli.

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

W poniższym przykładzie przedstawiono kompletny plik BasicAgent.cpp.

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

[[Góra](#top)]

## <a name="sample-input"></a>Przykładowe dane wejściowe

Jest to przykładowa zawartość pliku wejściowego text.txt:

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>Przykładowe dane wyjściowe

W przypadku użycia z przykładowym wejściem program generuje następujące dane wyjściowe:

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>Niezawodne programowanie

Aby zapobiec równoczesny dostęp do elementów członkowskich danych, `protected` `private` zaleca się dodanie metod, które wykonują pracę do lub sekcji klasy. Dodaj tylko metody, które wysyłają lub odbierają wiadomości do lub od agenta `public` do sekcji klasy.

Zawsze wywołać [współbieżność::agent::done](reference/agent-class.md#done) metoda, aby przenieść agenta do stanu ukończone. Zazwyczaj wywołać tę metodę przed `run` powrotem z metody.

## <a name="next-steps"></a>Następne kroki

Inny przykład aplikacji opartej na agencie można znaleźć w [przewodniku: Używanie sprzężenia w celu zapobiegania zakleszczenie](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

## <a name="see-also"></a>Zobacz też

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania wiadomości](../../parallel/concrt/message-passing-functions.md)<br/>
[Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Wskazówki: korzystanie ze złączy w celu zapobiegania zakleszczeniom](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
