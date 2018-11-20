---
title: 'Wskazówki: usuwanie pracy z wątku interfejs użytkownika'
ms.date: 11/19/2018
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 1230cf2b3fa510aeca8516e41cf30f9665987d05
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176318"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Wskazówki: usuwanie pracy z wątku interfejs użytkownika

W tym dokumencie przedstawiono sposób przenoszenia pracy wykonywanej przez wątek interfejsu użytkownika (UI) w aplikacji Microsoft Foundation Classes (MFC) do wątku roboczego za pomocą środowiska uruchomieniowego współbieżności. Również w tym dokumencie pokazano, jak poprawić wydajność długotrwałej operacji rysowania.

Usuwanie pracy z wątku interfejsu użytkownika dzięki przeniesieniu operacji blokowania, na przykład rysunku, aby wątków może zwiększyć szybkość reakcji aplikacji. W tym instruktażu wykorzystano rysowania procedury, która generuje fraktalowy Mandelbrot, aby zademonstrować długotrwałej operacji blokowania. Generowanie fraktalowy Mandelbrot jest również dobrym kandydatem do przetwarzania równoległego, ponieważ obliczenie każdego piksela jest niezależna od wszystkich pozostałych obliczeń.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu, przeczytaj następujące tematy:

- [Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)

- [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)

- [Anulowanie w PPL](cancellation-in-the-ppl.md)

Zalecamy również, że rozumiesz podstawy tworzenia aplikacji MFC i GDI +, przed rozpoczęciem tego instruktażu. Aby uzyskać więcej informacji na temat MFC, zobacz [aplikacji pulpitu MFC](../../mfc/mfc-desktop-applications.md). Aby uzyskać więcej informacji na temat interfejsu GDI + zobacz [GDI +](https://msdn.microsoft.com/library/windows/desktop/ms533798).

##  <a name="top"></a> Sekcje

Ten przewodnik zawiera następujące sekcje:

- [Tworzenie aplikacji MFC](#application)

- [Implementowanie Serial wersję aplikacji Mandelbrot](#serial)

- [Usuwanie pracy z wątku interfejsu użytkownika](#removing-work)

- [Poprawa wydajności rysowania](#performance)

- [Dodanie obsługi anulowania](#cancellation)

##  <a name="application"></a> Tworzenie aplikacji MFC

W tej sekcji opisano sposób tworzenia podstawowych aplikacji MFC.

### <a name="to-create-a-visual-c-mfc-application"></a>Aby utworzyć aplikację Visual C++ MFC

1. Na **pliku** menu, kliknij przycisk **New**, a następnie kliknij przycisk **projektu**.

1. W **nowy projekt** dialogowym **zainstalowane szablony** okienku wybierz **Visual C++**, a następnie w **szablony** wybierz opcję **Aplikacji MFC**. Wpisz nazwę projektu, na przykład `Mandelbrot`, a następnie kliknij przycisk **OK** do wyświetlenia **Kreator aplikacji MFC**.

1. W **typ aplikacji** okienku wybierz **pojedynczego dokumentu**. Upewnij się, że **Obsługa architektury dokument/widok** pole wyboru jest wyczyszczone.

1. Kliknij przycisk **Zakończ** Aby utworzyć projekt i zamknąć **Kreator aplikacji MFC**.

   Sprawdź, czy aplikacja została pomyślnie utworzona, tworząc i uruchamiając go. Aby skompilować aplikację, na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom ją, klikając pozycję **Rozpocznij debugowanie** na **debugowania** menu.

##  <a name="serial"></a> Implementowanie Serial wersję aplikacji Mandelbrot

W tej sekcji opisano sposób rysowania fraktalowy Mandelbrot. Ta wersja rysuje fraktalowy Mandelbrot GDI + [mapy bitowej](/windows/desktop/api/gdiplusheaders/nl-gdiplusheaders-bitmap) obiektu, a następnie kopiuje zawartość tej mapy bitowej do okna klienta.

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>Aby zaimplementować serial wersję aplikacji Mandelbrot

1. W pliku stdafx.h należy dodać następujące `#include` dyrektywy:

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. W ChildView.h po `pragma` dyrektywy, zdefiniuj `BitmapPtr` typu. `BitmapPtr` Typu umożliwia wskaźnik do `Bitmap` obiektu być współużytkowane przez wiele składników. `Bitmap` Obiekt zostanie usunięty, gdy nie jest już wywoływane przez dowolny składnik.

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. W ChildView.h, Dodaj następujący kod do `protected` części `CChildView` klasy:

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. W ChildView.cpp komentarz lub usuń następujące wiersze.

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   W kompilacjach do debugowania krok ten zapobiega aplikację przy użyciu `DEBUG_NEW` alokatora, który jest niezgodny z użyciem interfejsu GDI +.

1. W ChildView.cpp, Dodaj `using` dyrektywę `Gdiplus` przestrzeni nazw.

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. Dodaj następujący kod do Konstruktor i destruktor `CChildView` klasy do inicjowania i zamknąć GDI +.

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. Implementowanie `CChildView::DrawMandelbrot` metody. Ta metoda pobiera fraktalowy Mandelbrot określonej `Bitmap` obiektu.

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. Implementowanie `CChildView::OnPaint` metody. Ta metoda wywołuje `CChildView::DrawMandelbrot` , a następnie kopiuje zawartość `Bitmap` obiektu do okna.

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. Upewnij się, że aplikacja została pomyślnie zaktualizowana, tworząc i uruchamiając go.

Poniższa ilustracja przedstawia wyniki aplikacji Mandelbrot.

![Aplikacja Mandelbrot](../../parallel/concrt/media/mandelbrot.png "aplikacji Mandelbrot")

Ponieważ obliczenia dla każdego piksela jest obliczeniowo kosztowne, wątku interfejsu użytkownika nie może przetworzyć dodatkowe komunikaty, dopóki nie zakończy się ogólną obliczeń. Może to zmniejszyć czas odpowiedzi w aplikacji. Można jednak zwolnić ten problem, przez usuwanie pracy z wątku interfejsu użytkownika.

[[Górnej](#top)]

##  <a name="removing-work"></a> Usuwanie pracy z wątku interfejsu użytkownika

W tej sekcji pokazano, jak usunąć rysowania pracy z wątku interfejsu użytkownika w aplikacji Mandelbrot. Przenosząc na rysunku pracy z wątku interfejsu użytkownika do wątku roboczego wątku interfejsu użytkownika można przetwarzania komunikatów wątku roboczego generuje obraz w tle.

Środowisko uruchomieniowe współbieżności zapewnia trzy sposoby uruchamiania zadań: [grupy zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md), [agentów asynchronicznych](../../parallel/concrt/asynchronous-agents.md), i [zadań lekkich](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Mimo że można usunąć pracy z wątku interfejsu użytkownika, można użyć jednego z tych mechanizmów, w tym przykładzie użyto [concurrency::task_group](reference/task-group-class.md) obiektu, ponieważ grupy zadań obsługują anulowania. W tym przewodniku używa anulowania później, aby zmniejszyć ilość pracy, które jest wykonywane, gdy zmieniany jest rozmiar okna klienta i do wykonywania oczyszczania, kiedy niszczony jest okno.

W tym przykładzie również użyto [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) obiektu, aby umożliwić wątku interfejsu użytkownika i wątku roboczego do komunikowania się ze sobą. Po wątku roboczego powoduje obrazu, wysyła wskaźnik do `Bitmap` obiekt `unbounded_buffer` obiektu, a następnie wysyła komunikat o malowaniu wątku interfejsu użytkownika. Wątek interfejsu użytkownika odbiera od `unbounded_buffer` obiektu `Bitmap` obiektu i rysuje go w oknie klienta.

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Aby usunąć rysowania pracy z wątku interfejsu użytkownika

1. W pliku stdafx.h należy dodać następujące `#include` dyrektywy:

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. W ChildView.h, Dodaj `task_group` i `unbounded_buffer` zmienne Członkowskie `protected` części `CChildView` klasy. `task_group` Obiekt zawiera zadania, które wykonywać Rysowanie; `unbounded_buffer` obiekt zawiera obraz Mandelbrot ukończone.

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. W ChildView.cpp, Dodaj `using` dyrektywę `concurrency` przestrzeni nazw.

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. W `CChildView::DrawMandelbrot` po wywołaniu metody `Bitmap::UnlockBits`, wywołaj [concurrency::send](reference/concurrency-namespace-functions.md#send) funkcję, aby przekazać `Bitmap` obiektu wątku interfejsu użytkownika. Następnie opublikuj komunikat o malowaniu wątku interfejsu użytkownika i unieważnić obszaru klienta.

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. Aktualizacja `CChildView::OnPaint` metodę, aby odbierać zaktualizowane `Bitmap` obiektu i narysuj obraz w oknie klienta.

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   `CChildView::OnPaint` Metoda tworzy zadanie do generowania obrazu Mandelbrot, jeśli nie istnieje w buforu komunikatu. Buforu komunikatu nie będzie zawierać `Bitmap` obiektu w przypadkach, takich jak komunikat malowania początkowej i inne okno jest przenoszony przed okna klienta.

1. Upewnij się, że aplikacja została pomyślnie zaktualizowana, tworząc i uruchamiając go.

Interfejs użytkownika jest teraz bardziej dynamiczny, ponieważ rysowania praca jest wykonywana w tle.

[[Górnej](#top)]

##  <a name="performance"></a> Poprawa wydajności rysowania

Generowanie fraktalowy Mandelbrot jest dobrym kandydatem do przetwarzania równoległego, ponieważ obliczenie każdego piksela jest niezależna od wszystkich pozostałych obliczeń. Równoległe przetwarzanie procedury rysowania, przekonwertować zewnętrzny `for` pętli w `CChildView::DrawMandelbrot` metoda do wywołania [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytmu, w następujący sposób.

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

Ponieważ obliczenie każdy element bitmapy jest niezależny, nie masz do synchronizowania operacji rysowania, które mają dostęp do pamięci mapy bitowej. Dzięki temu wydajność skalowania w miarę zwiększania procesorów dostępnych liczby.

[[Górnej](#top)]

##  <a name="cancellation"></a> Dodanie obsługi anulowania

W tej sekcji opisano, jak obsługiwać zmiany rozmiaru okna i jak anulować wszystkie aktywne zadania rysowania, kiedy niszczony jest okna.

Dokument [anulowanie w PPL](cancellation-in-the-ppl.md) wyjaśniono, jak działa anulowanie w środowisku uruchomieniowym. Anulowanie jest wspólne; w związku z tym gdy nie występuje natychmiast. Aby zatrzymać anulowanych zadań, środowisko wykonawcze zgłasza wyjątek wewnętrzny podczas kolejnych wywołań z zadania w czasie wykonywania. Poprzedniej sekcji pokazano, jak używać `parallel_for` algorytmu, aby poprawić wydajność rysowania zadania. Wywołanie `parallel_for` umożliwia środowiska uruchomieniowego, można zatrzymać zadania, a w związku z tym umożliwia anulowanie pracy.

### <a name="cancelling-active-tasks"></a>Anulowanie aktywnych zadań

Tworzy aplikację Mandelbrot `Bitmap` obiektów, którego wymiary zgodny z rozmiarem okna klienta. Za każdym razem, gdy zmianie rozmiaru okna klienta, aplikacja tworzy zadania dodatkowych informacji uzupełniających w taki sposób, aby wygenerować obraz dla nowego rozmiaru okna. Aplikacja nie wymaga tych obrazów pośrednich; wymaga on tylko obraz dla rozmiaru okna końcowej. Aby zapobiec aplikacji z wykonywania dodatkowej pracy, możesz anulować wszystkie aktywne zadania rysowania w obsługi komunikatów dla `WM_SIZE` i `WM_SIZING` wiadomości i następnie rysowania Zaplanuj ponownie działać po zmianie rozmiaru okna.

Aby anulować aktywne zadania rysowania przy zmianie rozmiaru okna, aplikacja wywołuje [concurrency::task_group::cancel](reference/task-group-class.md#cancel) metody w procedurach obsługi dla `WM_SIZING` i `WM_SIZE` wiadomości. Obsługa `WM_SIZE` komunikatu także wywołania [CONCURRENCY::task_group:: wait](reference/task-group-class.md#wait) metoda oczekiwania dla wszystkich aktywnych zadań do wykonania, a następnie zmieni ustalony rysowania zadania dla rozmiaru okna zaktualizowane.

Kiedy niszczony jest okna klienta, jest dobrym rozwiązaniem, aby anulować wszystkie aktywne zadania rysowania. Trwa anulowanie wszelkich aktywnych zadań rysowania sprawia, że się upewnić, że wątków roboczych nie publikowały wiadomości do wątku interfejsu użytkownika po oknie klienta zostanie zniszczony. Aplikacja anuluje wszystkie aktywne zadania rysunku programu obsługi dla `WM_DESTROY` wiadomości.

### <a name="responding-to-cancellation"></a>Odpowiadanie na anulowanie

`CChildView::DrawMandelbrot` Metody, która wykonuje zadanie rysowania, musi odpowiadać na operację anulowania. Ponieważ środowisko wykonawcze używa obsługi wyjątków, aby anulować zadania, `CChildView::DrawMandelbrot` metody należy użyć mechanizmu bezpieczne pod względem wyjątków w celu zagwarantowania, że wszystkie zasoby są prawidłowo oczyszczony. W tym przykładzie użyto *inicjowania jest pozyskiwanie zasobów* wzorzec (RAII) gwarantuje, że bity mapy bitowej są odblokowane, gdy zadanie zostanie anulowane.

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Aby dodać obsługę anulowania w aplikacji Mandelbrot

1. W ChildView.h w `protected` części `CChildView` klasy, Dodaj deklaracje dla `OnSize`, `OnSizing`, i `OnDestroy` funkcje mapy komunikatów.

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. ChildView.cpp, zmodyfikuj mapy komunikatów, które ma zawierać programy obsługi dla `WM_SIZE`, `WM_SIZING`, i `WM_DESTROY` wiadomości.

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. Implementowanie `CChildView::OnSizing` metody. Ta metoda anuluje wszystkie istniejące zadania rysowania.

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. Implementowanie `CChildView::OnSize` metody. Ta metoda anuluje wszystkie istniejące zadania rysowania i tworzy nowe zadanie rysunku dla rozmiaru okna zaktualizowanego klienta.

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. Implementowanie `CChildView::OnDestroy` metody. Ta metoda anuluje wszystkie istniejące zadania rysowania.

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. W ChildView.cpp, zdefiniuj `scope_guard` klasy, która implementuje wzorzec RAII.

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. Dodaj następujący kod do `CChildView::DrawMandelbrot` metoda po wywołaniu `Bitmap::LockBits`:

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   Ten kod obsługuje anulowanie, tworząc `scope_guard` obiektu. Gdy obiekt opuszcza zakresu, odblokowuje bity mapy bitowej.

1. Modyfikowanie koniec `CChildView::DrawMandelbrot` metodę, aby odrzucić `scope_guard` obiektu po bity mapy bitowej są odblokowane, ale zanim jakiekolwiek komunikaty są wysyłane do wątku interfejsu użytkownika. Daje to gwarancję, że wątek interfejsu użytkownika nie zostanie zaktualizowana, zanim bity mapy bitowej są odblokowane.

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

9. Upewnij się, że aplikacja została pomyślnie zaktualizowana, tworząc i uruchamiając go.

Podczas zmiany rozmiaru okna rysowania praca odbywa się tylko do rozmiaru końcowego okna. Wszystkie aktywne zadania rysowania również zostaną anulowane, kiedy niszczony jest okna.

[[Górnej](#top)]

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Aplikacje klasyczne MFC](../../mfc/mfc-desktop-applications.md)
