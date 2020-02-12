---
title: 'Wskazówki: usuwanie pracy z wątku interfejs użytkownika'
ms.date: 08/19/2019
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 518044d4e3adea44c3776793c8277939076066d6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140709"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Wskazówki: usuwanie pracy z wątku interfejs użytkownika

W tym dokumencie przedstawiono sposób użycia środowisko uruchomieniowe współbieżności do przenoszenia pracy wykonywanej przez wątek interfejsu użytkownika (UI) w aplikacji Microsoft Foundation Classes (MFC) do wątku roboczego. W tym dokumencie pokazano również, jak zwiększyć wydajność długotrwałej operacji rysowania.

Usuwanie pracy z wątku interfejsu użytkownika przez odciążenie operacji blokowania, na przykład rysowania, do wątków roboczych może zwiększyć czas odpowiedzi aplikacji. W tym instruktażu jest stosowana procedura rysowania, która generuje Mandelbrot Fractal w celu zademonstrowania długotrwałej operacji blokowania. Generacja Mandelbrot Fractal jest również dobrym kandydatem do przetwarzanie równoległe, ponieważ obliczenia każdego piksela są niezależne od wszystkich innych obliczeń.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu zapoznaj się z następującymi tematami:

- [Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)

- [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)

- [Anulowanie w PPL](cancellation-in-the-ppl.md)

Zalecamy także zapoznanie się z podstawowymi informacjami na temat programowania aplikacji MFC i GDI+ przed rozpoczęciem tego instruktażu. Aby uzyskać więcej informacji na temat MFC, zobacz [aplikacje klasyczne MFC](../../mfc/mfc-desktop-applications.md). Aby uzyskać więcej informacji na temat interfejsu GDI+, zobacz [GDI+](/windows/win32/gdiplus/-gdiplus-gdi-start).

## <a name="top"></a>Poszczególne

Ten Instruktaż zawiera następujące sekcje:

- [Tworzenie aplikacji MFC](#application)

- [Implementowanie wersji szeregowej aplikacji Mandelbrot](#serial)

- [Usuwanie pracy z wątku interfejsu użytkownika](#removing-work)

- [Poprawianie wydajności rysowania](#performance)

- [Dodawanie obsługi anulowania](#cancellation)

## <a name="application"></a>Tworzenie aplikacji MFC

W tej sekcji opisano, jak utworzyć podstawową aplikację MFC.

### <a name="to-create-a-visual-c-mfc-application"></a>Aby utworzyć aplikację Visual C++ MFC

1. Użyj **Kreatora aplikacji MFC** , aby utworzyć aplikację MFC ze wszystkimi ustawieniami domyślnymi. Zobacz [Przewodnik: używanie nowych formantów powłoki MFC](../../mfc/walkthrough-using-the-new-mfc-shell-controls.md) w celu uzyskania instrukcji dotyczących sposobu otwierania Kreatora dla używanej wersji programu Visual Studio.

1. Wpisz nazwę projektu, na przykład `Mandelbrot`, a następnie kliknij przycisk **OK** , aby wyświetlić **Kreatora aplikacji MFC**.

1. W okienku **Typ aplikacji** wybierz pozycję **pojedynczy dokument**. Upewnij się, że pole wyboru **Obsługa architektury dokumentu/widoku** jest wyczyszczone.

1. Kliknij przycisk **Zakończ** , aby utworzyć projekt i zamknąć **Kreatora aplikacji MFC**.

   Sprawdź, czy aplikacja została utworzona pomyślnie, kompilując ją i uruchamiając. Aby skompilować aplikację, w menu **kompilacja** kliknij polecenie **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom aplikację, klikając polecenie **Rozpocznij debugowanie** w menu **debugowanie** .

## <a name="serial"></a>Implementowanie wersji szeregowej aplikacji Mandelbrot

W tej sekcji opisano sposób rysowania Mandelbrot Fractal. Ta wersja pobiera Mandelbrot Fractal do obiektu [mapy BITOWEJ](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap) GDI+, a następnie kopiuje zawartość tej mapy bitowej do okna klienta.

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>Aby zaimplementować wersję seryjną aplikacji Mandelbrot

1. W obszarze *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i starszych) Dodaj następującą dyrektywę `#include`:

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. W ChildView. h, po dyrektywie `pragma` Zdefiniuj typ `BitmapPtr`. Typ `BitmapPtr` umożliwia współużytkowanie wskaźnika do obiektu `Bitmap` przez wiele składników. Obiekt `Bitmap` jest usuwany, gdy nie jest już przywoływany przez żaden składnik.

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. W ChildView. h Dodaj następujący kod do sekcji `protected` klasy `CChildView`:

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. W ChildView. cpp, Skomentuj lub usuń następujące wiersze.

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   W przypadku kompilacji debugowania ten krok uniemożliwia aplikacji użycie alokatora `DEBUG_NEW`, który jest niezgodny z interfejsem GDI+.

1. W ChildView. cpp Dodaj dyrektywę `using` do przestrzeni nazw `Gdiplus`.

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. Dodaj następujący kod do konstruktora i destruktora klasy `CChildView`, aby zainicjować i zamknąć GDI+.

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. Zaimplementuj metodę `CChildView::DrawMandelbrot`. Ta metoda służy do rysowania Mandelbrot Fractal do określonego obiektu `Bitmap`.

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. Zaimplementuj metodę `CChildView::OnPaint`. Ta metoda wywołuje `CChildView::DrawMandelbrot` a następnie kopiuje zawartość obiektu `Bitmap` do okna.

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. Sprawdź, czy aplikacja została pomyślnie zaktualizowana, kompilując ją i uruchamiając.

Na poniższej ilustracji przedstawiono wyniki aplikacji Mandelbrot.

![Aplikacja Mandelbrot](../../parallel/concrt/media/mandelbrot.png "Aplikacja Mandelbrot")

Ponieważ obliczenia dla każdego piksela są w sposób obliczeniowy kosztowne, wątek interfejsu użytkownika nie może przetwarzać dodatkowych komunikatów do momentu zakończenia całkowitego obliczenia. Może to zmniejszyć czas odpowiedzi aplikacji. Można jednak zwolnić ten problem przez usunięcie pracy z wątku interfejsu użytkownika.

[[Top](#top)]

## <a name="removing-work"></a>Usuwanie pracy z wątku interfejsu użytkownika

W tej sekcji przedstawiono sposób usuwania pracy rysowania z wątku interfejsu użytkownika w aplikacji Mandelbrot. Przenosząc zadania rysowania z wątku interfejsu użytkownika do wątku roboczego, wątek interfejsu użytkownika może przetwarzać komunikaty w miarę jak wątek roboczy generuje obraz w tle.

Środowisko uruchomieniowe współbieżności oferuje trzy sposoby uruchamiania zadań: [grup zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md), [agentów asynchronicznych](../../parallel/concrt/asynchronous-agents.md)i [uproszczonych zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Chociaż można użyć dowolnego z tych mechanizmów do usuwania pracy z wątku interfejsu użytkownika, w tym przykładzie użyto obiektu [concurrency:: task_group](reference/task-group-class.md) , ponieważ grupy zadań obsługują anulowanie. W tym instruktażu później zostanie użyta funkcja anulowania w celu zmniejszenia ilości pracy wykonywanej po zmianie rozmiaru okna klienta i przeprowadzenia czyszczenia, gdy okno zostanie zniszczone.

W tym przykładzie używa się również obiektu [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) , aby umożliwić komunikację między WĄTKIEM interfejsu użytkownika i wątkiem roboczym. Po utworzeniu obrazu przez wątek roboczy, wysyła on wskaźnik do obiektu `Bitmap` do obiektu `unbounded_buffer`, a następnie ogłasza komunikat programu Paint w wątku interfejsu użytkownika. Wątek interfejsu użytkownika odbiera następnie z obiektu `unbounded_buffer` obiekt `Bitmap` i rysuje go w oknie klienta.

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Aby usunąć rysunek roboczy z wątku interfejsu użytkownika

1. W obszarze *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i starszych) Dodaj następujące dyrektywy `#include`:

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. W ChildView. h Dodaj Zmienne Członkowskie `task_group` i `unbounded_buffer` do sekcji `protected` klasy `CChildView`. Obiekt `task_group` zawiera zadania, które wykonują rysowanie; Obiekt `unbounded_buffer` zawiera ukończony obraz Mandelbrot.

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. W ChildView. cpp Dodaj dyrektywę `using` do przestrzeni nazw `concurrency`.

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. W `CChildView::DrawMandelbrot` metodzie po wywołaniu `Bitmap::UnlockBits`, wywołaj funkcję [concurrency:: Send](reference/concurrency-namespace-functions.md#send) , aby przekazać obiekt `Bitmap` do wątku interfejsu użytkownika. Następnie opublikuj komunikat programu Paint w wątku interfejsu użytkownika i Unieważnij obszar klienta.

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. Zaktualizuj metodę `CChildView::OnPaint`, aby otrzymać zaktualizowany obiekt `Bitmap` i narysować obraz do okna klienta.

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   Metoda `CChildView::OnPaint` tworzy zadanie w celu wygenerowania obrazu Mandelbrot, jeśli nie istnieje w buforze komunikatów. Bufor komunikatów nie będzie zawierał obiektu `Bitmap` w przypadkach, takich jak początkowy komunikat programu Paint i gdy inne okno zostanie przeniesione przed oknem klienta.

1. Sprawdź, czy aplikacja została pomyślnie zaktualizowana, kompilując ją i uruchamiając.

Interfejs użytkownika jest teraz bardziej wydajny, ponieważ zadania rysowania są wykonywane w tle.

[[Top](#top)]

## <a name="performance"></a>Poprawianie wydajności rysowania

Generowanie Mandelbrot Fractal jest dobrym kandydatem do przetwarzanie równoległe, ponieważ obliczenia każdego piksela są niezależne od wszystkich innych obliczeń. Aby zrównoleglanie procedurę rysowania, przekonwertuj pętlę zewnętrznego `for` w metodzie `CChildView::DrawMandelbrot` na wywołanie metody [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) , jak pokazano poniżej.

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

Ponieważ obliczenia każdego elementu mapy bitowej są niezależne, nie trzeba synchronizować operacji rysowania, które uzyskują dostęp do pamięci mapy bitowej. Umożliwia to skalowanie wydajności w miarę wzrostu liczby dostępnych procesorów.

[[Top](#top)]

## <a name="cancellation"></a>Dodawanie obsługi anulowania

W tej sekcji opisano, jak obsłużyć zmianę rozmiarów okien i anulować aktywne zadania rysowania, gdy okno zostanie zniszczone.

Anulowanie dokumentu [w PPL](cancellation-in-the-ppl.md) wyjaśnia, jak anulowanie działa w czasie wykonywania. Anulowanie jest spółdzielnią; w związku z tym nie występuje od razu. Aby zatrzymać anulowane zadanie, środowisko uruchomieniowe zgłasza wyjątek wewnętrzny podczas kolejnego wywołania z zadania do środowiska uruchomieniowego. W poprzedniej sekcji pokazano, jak używać algorytmu `parallel_for`, aby zwiększyć wydajność zadania rysowania. Wywołanie `parallel_for` pozwala na zatrzymanie zadania przez środowisko uruchomieniowe i w związku z tym umożliwia anulowanie działania.

### <a name="cancelling-active-tasks"></a>Anulowanie aktywnych zadań

Aplikacja Mandelbrot tworzy obiekty `Bitmap`, których wymiary są zgodne z rozmiarem okna klienta. Za każdym razem, gdy rozmiar okna klienta zostanie zmieniony, aplikacja tworzy dodatkowe zadanie w tle w celu wygenerowania obrazu dla nowego rozmiaru okna. Aplikacja nie wymaga obrazów pośrednich. wymaga tylko obrazu dla końcowego rozmiaru okna. Aby zapobiec wykonywaniu przez aplikację tej dodatkowej pracy, można anulować wszystkie aktywne zadania rysowania w obsłudze komunikatów dla `WM_SIZE` i `WM_SIZING` komunikatów, a następnie ponownie zaplanować prace rysowania po zmianie rozmiaru okna.

Aby anulować aktywne zadania rysowania po zmianie rozmiaru okna, aplikacja wywołuje metodę [concurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) w obsłudze dla `WM_SIZING` i `WM_SIZE` komunikatów. Procedura obsługi komunikatu `WM_SIZE` również wywołuje metodę [concurrency:: task_group:: wait](reference/task-group-class.md#wait) , aby poczekać na zakończenie wszystkich aktywnych zadań, a następnie ponownie planuje zadanie rysowania dla zaktualizowanego rozmiaru okna.

Po zniszczeniu okna klienta dobrym sposobem jest anulowanie wszystkich aktywnych zadań rysowania. Anulowanie aktywnych zadań rysowania sprawia, że wątki robocze nie publikują komunikatów w wątku interfejsu użytkownika po zniszczeniu okna klienta. Aplikacja anuluje wszystkie aktywne zadania rysowania w programie obsługi komunikatu `WM_DESTROY`.

### <a name="responding-to-cancellation"></a>Odpowiadanie na anulowanie

Metoda `CChildView::DrawMandelbrot`, która wykonuje zadanie rysowania, musi odpowiedzieć na anulowanie. Ponieważ środowisko uruchomieniowe używa obsługi wyjątków w celu anulowania zadań, Metoda `CChildView::DrawMandelbrot` musi używać mechanizmu bezpiecznego pod względem wyjątku, aby zagwarantować, że wszystkie zasoby są prawidłowo czyszczone. W tym przykładzie zastosowano wzorzec *pozyskiwania zasobów* (RAII) w celu zagwarantowania, że bity bitmapy są odblokowywane, gdy zadanie zostanie anulowane.

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Aby dodać obsługę anulowania w aplikacji Mandelbrot

1. W ChildView. h, w sekcji `protected` klasy `CChildView`, Dodaj deklaracje dla funkcji mapy wiadomości `OnSize`, `OnSizing`i `OnDestroy`.

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. W ChildView. cpp zmodyfikuj mapę wiadomości tak, aby zawierała programy obsługi dla wiadomości `WM_SIZE`, `WM_SIZING`i `WM_DESTROY`.

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. Zaimplementuj metodę `CChildView::OnSizing`. Ta metoda anuluje wszystkie istniejące zadania rysowania.

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. Zaimplementuj metodę `CChildView::OnSize`. Ta metoda anuluje wszystkie istniejące zadania rysowania i tworzy nowe zadanie rysowania dla zaktualizowanego rozmiaru okna klienta.

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. Zaimplementuj metodę `CChildView::OnDestroy`. Ta metoda anuluje wszystkie istniejące zadania rysowania.

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. W ChildView. cpp Zdefiniuj klasę `scope_guard`, która implementuje wzorzec RAII.

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. Dodaj następujący kod do metody `CChildView::DrawMandelbrot` po wywołaniu `Bitmap::LockBits`:

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   Ten kod obsługuje anulowanie przez utworzenie obiektu `scope_guard`. Gdy obiekt opuszcza zakres, odblokowuje bity mapy bitowej.

1. Zmodyfikuj koniec metody `CChildView::DrawMandelbrot`, aby odrzucić obiekt `scope_guard` po odblokowaniu bitów mapy bitowej, ale przed wysłaniem jakichkolwiek komunikatów do wątku interfejsu użytkownika. Dzięki temu wątek interfejsu użytkownika nie zostanie zaktualizowany przed odblokowaniem bitów mapy bitowej.

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

9. Sprawdź, czy aplikacja została pomyślnie zaktualizowana, kompilując ją i uruchamiając.

W przypadku zmiany rozmiaru okna zadania rysowania są wykonywane tylko dla końcowego rozmiaru okna. Wszystkie aktywne zadania rysowania są również anulowane, gdy okno zostanie zniszczone.

[[Top](#top)]

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Aplikacje klasyczne MFC](../../mfc/mfc-desktop-applications.md)
