---
title: 'Wskazówki: usuwanie pracy z wątku interfejs użytkownika'
ms.date: 08/19/2019
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 52bc98ef339a19c6ec2a53697f532a9a94b6c9a6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377440"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Wskazówki: usuwanie pracy z wątku interfejs użytkownika

W tym dokumencie pokazano, jak używać środowiska uruchomieniowego współbieżności, aby przenieść pracę, która jest wykonywana przez wątek interfejsu użytkownika (UI) w aplikacji Microsoft Foundation Classes (MFC) do wątku roboczego. W tym dokumencie pokazano również, jak poprawić wydajność długiej operacji rysowania.

Usuwanie pracy z wątku interfejsu użytkownika przez odciążanie operacji blokowania, na przykład rysunek, do wątków roboczych może poprawić szybkość reakcji aplikacji. W tym instruktażu używa procedury rysowania, który generuje fraktal Mandelbrot wykazać długotrwałą operację blokowania. Generowanie fraktale Mandelbrot jest również dobrym kandydatem do równoległości, ponieważ obliczenia każdego piksela są niezależne od wszystkich innych obliczeń.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego przewodnika przeczytaj następujące tematy:

- [Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkcje przekazywania wiadomości](../../parallel/concrt/message-passing-functions.md)

- [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)

- [Anulowanie w PPL](cancellation-in-the-ppl.md)

Przed rozpoczęciem tego przewodnika zaleca się również zapoznanie się z podstawami tworzenia aplikacji MFC i interfejsu GDI+. Aby uzyskać więcej informacji na temat MFC, zobacz [MFC Desktop Applications](../../mfc/mfc-desktop-applications.md). Aby uzyskać więcej informacji na temat GDI+, zobacz [GDI+](/windows/win32/gdiplus/-gdiplus-gdi-start).

## <a name="sections"></a><a name="top"></a>Sekcje

Ten instruktaż zawiera następujące sekcje:

- [Tworzenie aplikacji MFC](#application)

- [Implementacja seryjnej wersji aplikacji Mandelbrot](#serial)

- [Usuwanie pracy z wątku interfejsu użytkownika](#removing-work)

- [Poprawa wydajności rysowania](#performance)

- [Dodawanie pomocy technicznej dla anulowania](#cancellation)

## <a name="creating-the-mfc-application"></a><a name="application"></a>Tworzenie aplikacji MFC

W tej sekcji opisano sposób tworzenia podstawowej aplikacji MFC.

### <a name="to-create-a-visual-c-mfc-application"></a>Aby utworzyć aplikację MFC języka Visual C++

1. Użyj **Kreatora aplikacji MFC,** aby utworzyć aplikację MFC ze wszystkimi ustawieniami domyślnymi. Zobacz [Przewodnik: Korzystanie z nowych kontrolek powłoki MFC instrukcje](../../mfc/walkthrough-using-the-new-mfc-shell-controls.md) dotyczące otwierania kreatora dla wersji programu Visual Studio.

1. Wpisz nazwę projektu, na przykład `Mandelbrot`, a następnie kliknij przycisk **OK,** aby wyświetlić **Kreatora aplikacji MFC**.

1. W okienku **Typ aplikacji** wybierz pozycję **Pojedynczy dokument**. Upewnij się, że pole wyboru **Obsługa architektury dokumentu/widoku** jest wyczyszczone.

1. Kliknij **przycisk Zakończ,** aby utworzyć projekt i **zamknąć Kreatora aplikacji MFC**.

   Sprawdź, czy aplikacja została pomyślnie utworzona przez jej utworzenie i uruchomienie. Aby utworzyć aplikację, w menu **Kompilacja** kliknij polecenie **Build Solution**. Jeśli aplikacja tworzy pomyślnie, uruchom aplikację, klikając **przycisk Rozpocznij debugowanie** w menu **debugowania.**

## <a name="implementing-the-serial-version-of-the-mandelbrot-application"></a><a name="serial"></a>Implementacja seryjnej wersji aplikacji Mandelbrot

W tej sekcji opisano sposób rysowania fraktalu Mandelbrot. Ta wersja rysuje fractal Mandelbrot do GDI + [Bitmap obiektu,](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap) a następnie kopiuje zawartość tej mapy bitowej do okna klienta.

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>Aby zaimplementować seryjną wersję aplikacji Mandelbrot

1. W *programie pch.h* (*stdafx.h* w programie Visual Studio `#include` 2017 i wcześniejszych) dodaj następującą dyrektywę:

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. W ChildView.h, `pragma` po dyrektywie, zdefiniuj `BitmapPtr` typ. Typ `BitmapPtr` umożliwia wskaźnik do `Bitmap` obiektu, które mają być współużytkowane przez wiele składników. Obiekt `Bitmap` jest usuwany, gdy nie jest już odwołuje się do żadnego składnika.

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. W ChildView.h dodaj następujący kod `protected` do `CChildView` sekcji klasy:

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. W pliku ChildView.cpp skomentuj lub usuń następujące wiersze.

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   W debugowania kompilacji ten krok uniemożliwia `DEBUG_NEW` aplikacji przy użyciu alokatora, który jest niezgodny z GDI +.

1. W ChildView.cpp dodaj `using` dyrektywę `Gdiplus` do obszaru nazw.

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. Dodaj następujący kod do konstruktora i `CChildView` destruktora klasy, aby zainicjować i zamknąć GDI+.

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. Zaimplementuj `CChildView::DrawMandelbrot` metodę. Ta metoda rysuje fractal Mandelbrot do określonego `Bitmap` obiektu.

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. Zaimplementuj `CChildView::OnPaint` metodę. Ta metoda `CChildView::DrawMandelbrot` wywołuje, a następnie `Bitmap` kopiuje zawartość obiektu do okna.

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. Sprawdź, czy aplikacja została pomyślnie zaktualizowana przez jej tworzenie i uruchamianie.

Na poniższej ilustracji przedstawiono wyniki aplikacji Mandelbrot.

![Aplikacja Mandelbrot](../../parallel/concrt/media/mandelbrot.png "Aplikacja Mandelbrot")

Ponieważ obliczenia dla każdego piksela jest obliczeniowo drogie, wątku interfejsu użytkownika nie można przetwarzać dodatkowe komunikaty, dopóki ogólne obliczenia zakończy. Może to zmniejszyć czas reakcji w aplikacji. Można jednak złagodzić ten problem, usuwając pracę z wątku interfejsu użytkownika.

[[Góra](#top)]

## <a name="removing-work-from-the-ui-thread"></a><a name="removing-work"></a>Usuwanie pracy z wątku interfejsu użytkownika

W tej sekcji pokazano, jak usunąć pracę rysunku z wątku interfejsu użytkownika w aplikacji Mandelbrot. Przenosząc pracę rysunku z wątku interfejsu użytkownika do wątku roboczego, wątek interfejsu użytkownika może przetwarzać wiadomości, ponieważ wątek roboczy generuje obraz w tle.

Środowisko uruchomieniowe współbieżności udostępnia trzy sposoby uruchamiania zadań: [grupy zadań,](../../parallel/concrt/task-parallelism-concurrency-runtime.md) [agenci asynchroniczne](../../parallel/concrt/asynchronous-agents.md)i [zadania odciążone.](../../parallel/concrt/task-scheduler-concurrency-runtime.md) Chociaż można użyć dowolnego z tych mechanizmów, aby usunąć pracę z wątku interfejsu użytkownika, w tym przykładzie używa [współbieżności::task_group](reference/task-group-class.md) obiektu, ponieważ grupy zadań obsługują anulowanie. W tym przewodniku później używa anulowania, aby zmniejszyć ilość pracy, która jest wykonywana po przesiąknięciu okna klienta i do wykonywania oczyszczania, gdy okno jest niszczone.

W tym przykładzie użyto również [współbieżności::unbounded_buffer](reference/unbounded-buffer-class.md) obiektu, aby włączyć wątek interfejsu użytkownika i wątku roboczego do komunikowania się ze sobą. Po wątku roboczego tworzy obraz, wysyła `Bitmap` wskaźnik do `unbounded_buffer` obiektu do obiektu, a następnie księguje komunikat farby do wątku interfejsu użytkownika. Wątek interfejsu użytkownika `unbounded_buffer` następnie `Bitmap` odbiera z obiektu obiektu i rysuje go do okna klienta.

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Aby usunąć pracę rysunku z wątku interfejsu użytkownika

1. W *programie pch.h* (*stdafx.h* w programie Visual Studio `#include` 2017 i wcześniejszych) dodaj następujące dyrektywy:

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. W ChildView.h `task_group` dodaj `unbounded_buffer` i zmienne `protected` członkowskie `CChildView` do sekcji klasy. Obiekt `task_group` przechowuje zadania, które wykonują rysunek; `unbounded_buffer` obiekt posiada ukończony obraz Mandelbrot.

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. W ChildView.cpp dodaj `using` dyrektywę `concurrency` do obszaru nazw.

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. W `CChildView::DrawMandelbrot` metodzie, po `Bitmap::UnlockBits`wywołaniu do , wywołać [współbieżność::send](reference/concurrency-namespace-functions.md#send) funkcji, aby przekazać `Bitmap` obiekt do wątku interfejsu użytkownika. Następnie opublikuj komunikat o farbie w wątku interfejsu użytkownika i unieważnij obszar klienta.

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. Zaktualizuj metodę, `CChildView::OnPaint` aby otrzymać zaktualizowany `Bitmap` obiekt i narysuj obraz do okna klienta.

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   Metoda `CChildView::OnPaint` tworzy zadanie do generowania obrazu Mandelbrot, jeśli nie istnieje w buforze wiadomości. Bufor komunikatu `Bitmap` nie będzie zawierać obiektu w przypadkach, takich jak początkowy komunikat farby i gdy inne okno jest przenoszone przed oknem klienta.

1. Sprawdź, czy aplikacja została pomyślnie zaktualizowana przez jej tworzenie i uruchamianie.

Interfejs użytkownika jest teraz bardziej responsywny, ponieważ praca rysunku jest wykonywana w tle.

[[Góra](#top)]

## <a name="improving-drawing-performance"></a><a name="performance"></a>Poprawa wydajności rysowania

Generowanie fraktale Mandelbrot jest dobrym kandydatem do równoległości, ponieważ obliczenia każdego piksela są niezależne od wszystkich innych obliczeń. Aby zrównać procedurę `for` rysowania, `CChildView::DrawMandelbrot` przekonwertuj zewnętrzną pętlę w metodzie na [wywołanie algorytmu współbieżności::parallel_for,](reference/concurrency-namespace-functions.md#parallel_for) w następujący sposób.

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

Ponieważ obliczenia każdego elementu bitmapy są niezależne, nie trzeba synchronizować operacji rysowania, które uzyskują dostęp do pamięci bitmapowej. Dzięki temu wydajność skalować wraz ze wzrostem liczby dostępnych procesorów.

[[Góra](#top)]

## <a name="adding-support-for-cancellation"></a><a name="cancellation"></a>Dodawanie pomocy technicznej dla anulowania

W tej sekcji opisano sposób obsługi zmiany rozmiaru okna i anulowania wszelkich aktywnych zadań rysowania po zniszczeniu okna.

Dokument [Anulowanie w PPL](cancellation-in-the-ppl.md) wyjaśnia, jak działa anulowanie w czasie wykonywania. Anulowanie jest oparte na współpracy; w związku z tym nie występuje natychmiast. Aby zatrzymać anulowane zadanie, środowisko wykonawcze zgłasza wyjątek wewnętrzny podczas kolejnego wywołania z zadania do środowiska wykonawczego. W poprzedniej sekcji pokazano, `parallel_for` jak użyć algorytmu, aby poprawić wydajność zadania rysowania. Wywołanie `parallel_for` umożliwia środowisko uruchomieniowe, aby zatrzymać zadanie i w związku z tym umożliwia anulowanie do pracy.

### <a name="cancelling-active-tasks"></a>Anulowanie aktywnych zadań

Aplikacja Mandelbrot `Bitmap` tworzy obiekty, których wymiary odpowiadają rozmiarowi okna klienta. Za każdym razem, gdy rozmiar okna klienta jest zmieniany, aplikacja tworzy dodatkowe zadanie w tle, aby wygenerować obraz dla nowego rozmiaru okna. Aplikacja nie wymaga tych obrazów pośrednich; wymaga tylko obrazu dla ostatecznego rozmiaru okna. Aby zapobiec wykonywaniu tej dodatkowej pracy przez aplikację, można anulować `WM_SIZE` wszystkie `WM_SIZING` aktywne zadania rysowania w programach obsługi wiadomości i wiadomości, a następnie złożyć harmonogram pracy rysunku po przesiąkniętym rozmiarze okna.

Aby anulować aktywne zadania rysowania po przesiąknięciu okna, aplikacja wywołuje [metodę współbieżności::task_group::cancel](reference/task-group-class.md#cancel) w programach obsługi `WM_SIZING` i `WM_SIZE` wiadomości. Program obsługi `WM_SIZE` wiadomości wywołuje również [współbieżność::task_group::wait](reference/task-group-class.md#wait) metoda czekać na wszystkie aktywne zadania, aby zakończyć, a następnie ponownie wylicza zadanie rysowania dla zaktualizowanego rozmiaru okna.

Gdy okno klienta zostanie zniszczone, dobrą praktyką jest anulowanie wszystkich aktywnych zadań rysowania. Anulowanie wszystkich aktywnych zadań rysowania upewnia się, że wątki robocze nie publikują wiadomości w wątku interfejsu użytkownika po zniszczeniu okna klienta. Aplikacja anuluje wszystkie aktywne zadania rysowania w programie obsługi `WM_DESTROY` wiadomości.

### <a name="responding-to-cancellation"></a>Reagowanie na anulowanie

Metoda, `CChildView::DrawMandelbrot` która wykonuje zadanie rysowania, musi odpowiadać na anulowanie. Ponieważ środowisko wykonawcze używa obsługi wyjątków `CChildView::DrawMandelbrot` do anulowania zadań, metoda musi używać mechanizmu bezpiecznego dla wyjątków, aby zagwarantować, że wszystkie zasoby są poprawnie czyszczone. W tym przykładzie użyto wzorca *inicjowania pozyskiwania zasobów* (RAII), aby zagwarantować, że bity mapy bitowej są odblokowane po anulowaniu zadania.

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Aby dodać obsługę anulowania w aplikacji Mandelbrot

1. W ChildView.h w `protected` sekcji `CChildView` klasy dodaj deklaracje `OnSize`dla `OnSizing`funkcji `OnDestroy` mapy , i wiadomości.

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. W programie ChildView.cpp zmodyfikuj `WM_SIZE`mapę wiadomości, aby zawierała programy obsługi programu , `WM_SIZING`i `WM_DESTROY` wiadomości.

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. Zaimplementuj `CChildView::OnSizing` metodę. Ta metoda anuluje wszystkie istniejące zadania rysowania.

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. Zaimplementuj `CChildView::OnSize` metodę. Ta metoda anuluje wszystkie istniejące zadania rysowania i tworzy nowe zadanie rysowania dla zaktualizowanego rozmiaru okna klienta.

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. Zaimplementuj `CChildView::OnDestroy` metodę. Ta metoda anuluje wszystkie istniejące zadania rysowania.

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. W ChildView.cpp zdefiniuj `scope_guard` klasę, która implementuje wzorzec RAII.

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. Dodaj następujący kod `CChildView::DrawMandelbrot` do metody po `Bitmap::LockBits`wywołaniu:

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   Ten kod obsługuje anulowanie `scope_guard` przez utworzenie obiektu. Gdy obiekt opuszcza zakres, odblokowuje bity mapy bitowej.

1. Zmodyfikuj koniec `CChildView::DrawMandelbrot` `scope_guard` metody, aby odrzucić obiekt po odblokowaniu bitów bitmapy, ale przed wysłaniem jakichkolwiek wiadomości do wątku interfejsu użytkownika. Gwarantuje to, że wątek interfejsu użytkownika nie jest aktualizowany przed odblokowaniem bitów mapy bitowej.

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

1. Sprawdź, czy aplikacja została pomyślnie zaktualizowana przez jej tworzenie i uruchamianie.

Podczas zmieniania rozmiaru okna praca rysunkowa jest wykonywana tylko dla ostatecznego rozmiaru okna. Wszystkie aktywne zadania rysowania są również anulowane, gdy okno zostanie zniszczone.

[[Góra](#top)]

## <a name="see-also"></a>Zobacz też

[Wskazówki dotyczące środowiska uruchomieniowego współbieżności](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania wiadomości](../../parallel/concrt/message-passing-functions.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Aplikacje klasyczne MFC](../../mfc/mfc-desktop-applications.md)
