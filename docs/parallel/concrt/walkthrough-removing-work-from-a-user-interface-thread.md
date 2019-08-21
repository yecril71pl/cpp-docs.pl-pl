---
title: 'Przewodnik: Usuwanie pracy z wątku interfejsu użytkownika'
ms.date: 08/19/2019
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 2ee15d4660984c9afb77cb20f8ef0dab25a8b933
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631710"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Przewodnik: Usuwanie pracy z wątku interfejsu użytkownika

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

##  <a name="top"></a>Poszczególne

Ten Instruktaż zawiera następujące sekcje:

- [Tworzenie aplikacji MFC](#application)

- [Implementowanie wersji szeregowej aplikacji Mandelbrot](#serial)

- [Usuwanie pracy z wątku interfejsu użytkownika](#removing-work)

- [Poprawianie wydajności rysowania](#performance)

- [Dodawanie obsługi anulowania](#cancellation)

##  <a name="application"></a>Tworzenie aplikacji MFC

W tej sekcji opisano, jak utworzyć podstawową aplikację MFC.

### <a name="to-create-a-visual-c-mfc-application"></a>Aby utworzyć aplikację Visual C++ MFC

1. Użyj **Kreatora aplikacji MFC** , aby utworzyć aplikację MFC ze wszystkimi ustawieniami domyślnymi. Zobacz [Przewodnik: Aby uzyskać instrukcje dotyczące sposobu otwierania](../../mfc/walkthrough-using-the-new-mfc-shell-controls.md) kreatora dla używanej wersji programu Visual Studio, użyj nowych formantów powłoki MFC.

1. Wpisz nazwę projektu, na przykład `Mandelbrot`, a następnie kliknij przycisk **OK** , aby wyświetlić **Kreatora aplikacji MFC**.

1. W okienku **Typ aplikacji** wybierz pozycję **pojedynczy dokument**. Upewnij się, że pole wyboru **Obsługa architektury dokumentu/widoku** jest wyczyszczone.

1. Kliknij przycisk **Zakończ** , aby utworzyć projekt i zamknąć **Kreatora aplikacji MFC**.

   Sprawdź, czy aplikacja została utworzona pomyślnie, kompilując ją i uruchamiając. Aby skompilować aplikację, w menu **kompilacja** kliknij polecenie **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom aplikację, klikając polecenie **Rozpocznij debugowanie** w menu **debugowanie** .

##  <a name="serial"></a>Implementowanie wersji szeregowej aplikacji Mandelbrot

W tej sekcji opisano sposób rysowania Mandelbrot Fractal. Ta wersja pobiera Mandelbrot Fractal do obiektu [mapy BITOWEJ](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap) GDI+, a następnie kopiuje zawartość tej mapy bitowej do okna klienta.

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>Aby zaimplementować wersję seryjną aplikacji Mandelbrot

1. W obszarze *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i starszych) Dodaj następującą `#include` dyrektywę:

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. W ChildView. h, po `pragma` dyrektywie, `BitmapPtr` Zdefiniuj typ. Typ włącza wskaźnik `Bitmap` do obiektu, który ma być współużytkowany przez wiele składników. `BitmapPtr` `Bitmap` Obiekt jest usuwany, gdy nie jest już przywoływany przez żaden składnik.

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. W ChildView. h Dodaj następujący kod do `protected` sekcji `CChildView` klasy:

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. W ChildView. cpp, Skomentuj lub usuń następujące wiersze.

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   W przypadku kompilacji debugowania ten krok uniemożliwia aplikacji użycie `DEBUG_NEW` alokatora, który jest niezgodny z interfejsem GDI+.

1. W ChildView. cpp Dodaj `using` dyrektywę `Gdiplus` do przestrzeni nazw.

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. Dodaj następujący kod do konstruktora i destruktora klasy, `CChildView` aby zainicjować i zamknąć GDI+.

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. Zaimplementuj `CChildView::DrawMandelbrot` metodę. Ta metoda służy do rysowania Mandelbrot Fractal do określonego `Bitmap` obiektu.

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. Zaimplementuj `CChildView::OnPaint` metodę. Ta metoda wywołuje `CChildView::DrawMandelbrot` , a następnie kopiuje zawartość `Bitmap` obiektu do okna.

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. Sprawdź, czy aplikacja została pomyślnie zaktualizowana, kompilując ją i uruchamiając.

Na poniższej ilustracji przedstawiono wyniki aplikacji Mandelbrot.

![Aplikacja Mandelbrot](../../parallel/concrt/media/mandelbrot.png "Aplikacja Mandelbrot")

Ponieważ obliczenia dla każdego piksela są w sposób obliczeniowy kosztowne, wątek interfejsu użytkownika nie może przetwarzać dodatkowych komunikatów do momentu zakończenia całkowitego obliczenia. Może to zmniejszyć czas odpowiedzi aplikacji. Można jednak zwolnić ten problem przez usunięcie pracy z wątku interfejsu użytkownika.

[[Top](#top)]

##  <a name="removing-work"></a>Usuwanie pracy z wątku interfejsu użytkownika

W tej sekcji przedstawiono sposób usuwania pracy rysowania z wątku interfejsu użytkownika w aplikacji Mandelbrot. Przenosząc zadania rysowania z wątku interfejsu użytkownika do wątku roboczego, wątek interfejsu użytkownika może przetwarzać komunikaty w miarę jak wątek roboczy generuje obraz w tle.

Środowisko uruchomieniowe współbieżności oferuje trzy sposoby uruchamiania zadań: [grup zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md), [agentów asynchronicznych](../../parallel/concrt/asynchronous-agents.md)i uproszczonych [zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Chociaż można użyć dowolnego z tych mechanizmów do usuwania pracy z wątku interfejsu użytkownika, w tym przykładzie użyto obiektu [concurrency:: task_group](reference/task-group-class.md) , ponieważ grupy zadań obsługują anulowanie. W tym instruktażu później zostanie użyta funkcja anulowania w celu zmniejszenia ilości pracy wykonywanej po zmianie rozmiaru okna klienta i przeprowadzenia czyszczenia, gdy okno zostanie zniszczone.

Ten przykład używa również obiektu [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) , aby umożliwić komunikację wątku interfejsu użytkownika i wątku roboczego ze sobą. Po utworzeniu obrazu przez wątek roboczy wysyła on wskaźnik do `Bitmap` `unbounded_buffer` obiektu, a następnie ogłasza komunikat programu Paint do wątku interfejsu użytkownika. Wątek interfejsu użytkownika odbiera następnie z `unbounded_buffer` `Bitmap` obiektu obiekt i rysuje go w oknie klienta.

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Aby usunąć rysunek roboczy z wątku interfejsu użytkownika

1. W obszarze *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i starszych) Dodaj następujące `#include` dyrektywy:

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. W ChildView. h, Dodaj `task_group` i `unbounded_buffer` Zmienne Członkowskie `CChildView` do `protected` sekcji klasy. Obiekt zawiera zadania, które wykonują rysowanie `unbounded_buffer` ; obiekt zawiera ukończony obraz Mandelbrot. `task_group`

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. W ChildView. cpp Dodaj `using` dyrektywę `concurrency` do przestrzeni nazw.

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. W metodzie po `Bitmap::UnlockBits`wywołaniu, wywołaj funkcję `Bitmap` [concurrency:: Send](reference/concurrency-namespace-functions.md#send) , aby przekazać obiekt do wątku interfejsu użytkownika. `CChildView::DrawMandelbrot` Następnie opublikuj komunikat programu Paint w wątku interfejsu użytkownika i Unieważnij obszar klienta.

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. Zaktualizuj metodę w celu otrzymania zaktualizowanego `Bitmap` obiektu i narysowania obrazu w oknie klienta. `CChildView::OnPaint`

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   `CChildView::OnPaint` Metoda tworzy zadanie w celu wygenerowania obrazu Mandelbrot, jeśli nie istnieje w buforze komunikatów. Bufor komunikatów nie będzie zawierał `Bitmap` obiektu w takich przypadkach, jak początkowy komunikat programu Paint i gdy inne okno zostanie przeniesione przed oknem klienta.

1. Sprawdź, czy aplikacja została pomyślnie zaktualizowana, kompilując ją i uruchamiając.

Interfejs użytkownika jest teraz bardziej wydajny, ponieważ zadania rysowania są wykonywane w tle.

[[Top](#top)]

##  <a name="performance"></a>Poprawianie wydajności rysowania

Generowanie Mandelbrot Fractal jest dobrym kandydatem do przetwarzanie równoległe, ponieważ obliczenia każdego piksela są niezależne od wszystkich innych obliczeń. Aby zrównoleglanie procedurę rysowania, przekonwertuj pętlę `for` zewnętrzną `CChildView::DrawMandelbrot` w metodzie na wywołanie algorytmu [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) w następujący sposób.

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

Ponieważ obliczenia każdego elementu mapy bitowej są niezależne, nie trzeba synchronizować operacji rysowania, które uzyskują dostęp do pamięci mapy bitowej. Umożliwia to skalowanie wydajności w miarę wzrostu liczby dostępnych procesorów.

[[Top](#top)]

##  <a name="cancellation"></a>Dodawanie obsługi anulowania

W tej sekcji opisano, jak obsłużyć zmianę rozmiarów okien i anulować aktywne zadania rysowania, gdy okno zostanie zniszczone.

Anulowanie dokumentu [w PPL](cancellation-in-the-ppl.md) wyjaśnia, jak anulowanie działa w czasie wykonywania. Anulowanie jest spółdzielnią; w związku z tym nie występuje od razu. Aby zatrzymać anulowane zadanie, środowisko uruchomieniowe zgłasza wyjątek wewnętrzny podczas kolejnego wywołania z zadania do środowiska uruchomieniowego. W poprzedniej sekcji przedstawiono sposób użycia `parallel_for` algorytmu w celu zwiększenia wydajności zadania rysowania. Wywołanie `parallel_for` umożliwiające programowi uruchomieniowemu zatrzymanie zadania i w związku z tym umożliwia anulowanie działania.

### <a name="cancelling-active-tasks"></a>Anulowanie aktywnych zadań

Aplikacja Mandelbrot tworzy `Bitmap` obiekty, których wymiary są zgodne z rozmiarem okna klienta. Za każdym razem, gdy rozmiar okna klienta zostanie zmieniony, aplikacja tworzy dodatkowe zadanie w tle w celu wygenerowania obrazu dla nowego rozmiaru okna. Aplikacja nie wymaga obrazów pośrednich. wymaga tylko obrazu dla końcowego rozmiaru okna. Aby zapobiec wykonywaniu przez aplikację tej dodatkowej pracy, można anulować wszystkie aktywne zadania rysowania w obsłudze komunikatów dla `WM_SIZE` komunikatów i `WM_SIZING` , a następnie ponownie zaplanować pracę po zmianie rozmiaru okna.

Aby anulować aktywne zadania rysowania po zmianie rozmiaru okna, aplikacja wywołuje metodę [concurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) w obsłudze dla `WM_SIZING` i `WM_SIZE` komunikatów. Procedura obsługi `WM_SIZE` komunikatu wywołuje również metodę [concurrency:: task_group:: wait](reference/task-group-class.md#wait) , aby czekać na zakończenie wszystkich aktywnych zadań, a następnie ponownie planuje zadanie rysowania dla zaktualizowanego rozmiaru okna.

Po zniszczeniu okna klienta dobrym sposobem jest anulowanie wszystkich aktywnych zadań rysowania. Anulowanie aktywnych zadań rysowania sprawia, że wątki robocze nie publikują komunikatów w wątku interfejsu użytkownika po zniszczeniu okna klienta. Aplikacja anuluje wszystkie aktywne zadania rysowania w programie obsługi `WM_DESTROY` wiadomości.

### <a name="responding-to-cancellation"></a>Odpowiadanie na anulowanie

`CChildView::DrawMandelbrot` Metoda, która wykonuje zadanie rysowania, musi odpowiedzieć na anulowanie. Ponieważ środowisko uruchomieniowe używa obsługi wyjątków w celu anulowania zadań `CChildView::DrawMandelbrot` , metoda musi używać mechanizmu bezpiecznego pod względem wyjątku, aby zagwarantować, że wszystkie zasoby są prawidłowo czyszczone. W tym przykładzie zastosowano wzorzec *pozyskiwania zasobów* (RAII) w celu zagwarantowania, że bity bitmapy są odblokowywane, gdy zadanie zostanie anulowane.

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Aby dodać obsługę anulowania w aplikacji Mandelbrot

1. W ChildView. h, w `protected` sekcji `CChildView` klasy `OnSize`, Dodaj deklaracje dla funkcji map wiadomości, `OnSizing`i `OnDestroy` .

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. W ChildView. cpp zmodyfikuj mapę wiadomości tak, aby zawierała procedury obsługi dla `WM_SIZE`komunikatów `WM_SIZING`, i `WM_DESTROY` .

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. Zaimplementuj `CChildView::OnSizing` metodę. Ta metoda anuluje wszystkie istniejące zadania rysowania.

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. Zaimplementuj `CChildView::OnSize` metodę. Ta metoda anuluje wszystkie istniejące zadania rysowania i tworzy nowe zadanie rysowania dla zaktualizowanego rozmiaru okna klienta.

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. Zaimplementuj `CChildView::OnDestroy` metodę. Ta metoda anuluje wszystkie istniejące zadania rysowania.

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. W ChildView. cpp Zdefiniuj `scope_guard` klasę, która implementuje wzorzec RAII.

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. Dodaj następujący kod do `CChildView::DrawMandelbrot` metody po `Bitmap::LockBits`wywołaniu:

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   Ten kod obsługuje anulowanie przez utworzenie `scope_guard` obiektu. Gdy obiekt opuszcza zakres, odblokowuje bity mapy bitowej.

1. Zmodyfikuj koniec `CChildView::DrawMandelbrot` metody, aby `scope_guard` odrzucić obiekt po odblokowaniu bitów mapy bitowej, ale przed wysłaniem jakichkolwiek komunikatów do wątku interfejsu użytkownika. Dzięki temu wątek interfejsu użytkownika nie zostanie zaktualizowany przed odblokowaniem bitów mapy bitowej.

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

9. Sprawdź, czy aplikacja została pomyślnie zaktualizowana, kompilując ją i uruchamiając.

W przypadku zmiany rozmiaru okna zadania rysowania są wykonywane tylko dla końcowego rozmiaru okna. Wszystkie aktywne zadania rysowania są również anulowane, gdy okno zostanie zniszczone.

[[Top](#top)]

## <a name="see-also"></a>Zobacz także

[Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Aplikacje klasyczne MFC](../../mfc/mfc-desktop-applications.md)
