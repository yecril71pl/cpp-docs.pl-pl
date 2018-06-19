---
title: 'Wskazówki: Usuwanie pracy z wątku interfejsu użytkownika | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0502ce728c35b08d927cea48ee5b82756980aec5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694290"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Wskazówki: usuwanie pracy z wątku interfejs użytkownika
Ten dokument przedstawiono sposób korzystania ze współbieżności środowiska wykonawczego można przenieść pracy, które jest przeprowadzane przez wątek interfejsu użytkownika (UI) w aplikacji Microsoft Foundation Classes (MFC) do wątku roboczego. Ten dokument również pokazano, jak poprawić wydajność długotrwałej operacji rysowania.  
  
 Usuwanie pracy z wątku interfejsu użytkownika, przenosząc blokowania operacje, na przykład rysunek wątków roboczych może zwiększyć szybkość reakcji aplikacji. W tym przewodniku zastosowano rysowania procedury, które generuje fraktalowy Mandelbrot, aby zademonstrować długotrwałej operacji blokowania. Generowanie fraktalowy Mandelbrot jest również dobrym kandydatem do paralelizacja, ponieważ obliczenia każdego piksela jest niezależna od wszystkich pozostałych obliczeń.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przed skorzystaniem z tego przewodnika, przeczytaj następujące tematy:  
  
-   [Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
-   [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)  
  
-   [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)  
  
-   [Anulowanie w PPL](cancellation-in-the-ppl.md)  
  
 Zalecamy również że rozumiesz podstawowe informacje dotyczące tworzenia aplikacji MFC i [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] przed skorzystaniem z tego przewodnika. Aby uzyskać więcej informacji na temat MFC, zobacz [aplikacji pulpitu MFC](../../mfc/mfc-desktop-applications.md). Aby uzyskać więcej informacji na temat [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)], zobacz [GDI +](https://msdn.microsoft.com/en-us/library/windows/desktop/ms533798).  
  
##  <a name="top"></a> Sekcje  
 Ten przewodnik zawiera następujące sekcje:  
  
-   [Tworzenie aplikacji MFC](#application)  
  
-   [Implementowanie Serial wersji aplikacji Mandelbrot](#serial)  
  
-   [Usuwanie pracy z wątku interfejsu użytkownika](#removing-work)  
  
-   [Poprawianie wydajności rysowania](#performance)  
  
-   [Dodawanie obsługi anulowania](#cancellation)  
  
##  <a name="application"></a> Tworzenie aplikacji MFC  
 W tej sekcji opisano sposób tworzenia podstawowej aplikacji MFC.  
  
### <a name="to-create-a-visual-c-mfc-application"></a>Aby utworzyć aplikację Visual C++ MFC  
  
1.  Na **pliku** menu, kliknij przycisk **nowy**, a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** okna dialogowego, **zainstalowane szablony** okienku wybierz **Visual C++**, a następnie w **szablony** okienku, wybierz opcję **Aplikacji MFC**. Wpisz nazwę projektu, na przykład `Mandelbrot`, a następnie kliknij przycisk **OK** do wyświetlenia **Kreator aplikacji MFC**.  
  
3.  W **typu aplikacji** okienku wybierz **pojedynczego dokumentu**. Upewnij się, że **wsparcie dla architektury dokument/widok** pole wyboru jest wyczyszczone.  
  
4.  Kliknij przycisk **Zakończ** do tworzenia projektu i zamknąć **Kreator aplikacji MFC**.  
  
     Sprawdź, czy aplikacja została pomyślnie utworzona tworzenia i uruchamiania go. Do skompilowania aplikacji, na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Jeśli aplikacja tworzy się pomyślnie, uruchom aplikację, klikając **Rozpocznij debugowanie** na **debugowania** menu.  
  
##  <a name="serial"></a> Implementowanie Serial wersji aplikacji Mandelbrot  
 W tej sekcji opisano sposób rysowania fraktalowy Mandelbrot. Ta wersja rysuje fraktalowy Mandelbrot do [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] [mapy bitowej](https://msdn.microsoft.com/library/ms534420.aspx) obiekt, a następnie kopiuje zawartość tej mapy bitowej do okna klienta.  
  
#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>Aby zaimplementować serial wersji aplikacji Mandelbrot  
  
1.  W pliku stdafx.h, Dodaj następujący `#include` dyrektywy:  
  
     [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]  
  
2.  W ChildView.h po `pragma` dyrektywy, zdefiniuj `BitmapPtr` typu. `BitmapPtr` Typ umożliwia wskaźnik do `Bitmap` obiektu być współużytkowane przez kilka składników. `Bitmap` Usunąć obiektu, gdy nie jest już przywoływany przez dowolny składnik.  
  
     [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]  
  
3.  W ChildView.h, Dodaj następujący kod, aby `protected` sekcji `CChildView` klasy:  
  
     [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]  
  
4.  W ChildView.cpp komentarz lub usuń następujące linie.  
  
     [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]  
  
     W kompilacjach do debugowania tego kroku uniemożliwia aplikacji przy użyciu `DEBUG_NEW` przydzielania, który jest niezgodny z [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)].  
  
5.  W ChildView.cpp, Dodaj `using` dyrektywy do `Gdiplus` przestrzeni nazw.  
  
     [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]  
  
6.  Dodaj następujący kod do Konstruktor i destruktor `CChildView` klasę, aby zainicjować i zamknąć [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)].  
  
     [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]  
  
7.  Implementowanie `CChildView::DrawMandelbrot` metody. Ta metoda pobiera fraktalowy Mandelbrot do określonego `Bitmap` obiektu.  
  
     [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]  
  
8.  Implementowanie `CChildView::OnPaint` metody. Ta metoda wywołuje `CChildView::DrawMandelbrot` , a następnie kopiuje zawartość `Bitmap` obiektu do okna.  
  
     [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]  
  
9. Sprawdź, czy aplikacja została pomyślnie zaktualizowana, kompilowania i uruchamiając go.  
  
 Na poniższej ilustracji przedstawiono wyniki Mandelbrot aplikacji.  
  
 ![Aplikacja Mandelbrot](../../parallel/concrt/media/mandelbrot.png "mandelbrot")  
  
 Ponieważ obliczenia dla każdego piksela jest kosztowne w praktyce, wątku interfejsu użytkownika nie może przetworzyć dodatkowych komunikatów zakończenie obliczenia ogólnej. Może to zmniejszyć czas odpowiedzi aplikacji. Można jednak zwolnić ten problem, usuwając pracy z wątku interfejsu użytkownika.  
  
 [[Górnej](#top)]  
  
##  <a name="removing-work"></a> Usuwanie pracy z wątku interfejsu użytkownika  
 W tej sekcji pokazano, jak usunąć rysowania pracy z wątku interfejsu użytkownika w aplikacji Mandelbrot. Przenosząc na rysunku pracy z wątku interfejsu użytkownika do wątku roboczego wątku interfejsu użytkownika można przetwarzania komunikatów wątku roboczego generuje obraz w tle.  
  
 Współbieżność środowiska wykonawczego zapewnia trzy sposoby uruchamiania zadań: [zadań grup](../../parallel/concrt/task-parallelism-concurrency-runtime.md), [agentów asynchronicznych](../../parallel/concrt/asynchronous-agents.md), i [zadań lekkich](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Chociaż jeden z tych mechanizmów umożliwia usuwanie pracy z wątku interfejsu użytkownika, w tym przykładzie użyto [concurrency::task_group](reference/task-group-class.md) obiektu, ponieważ grupy zadań obsługuje anulowania. W tym przewodniku zastosowano anulowania później, aby zmniejszyć ilość pracy, które jest przeprowadzane, gdy zmieniany jest rozmiar okna klienta, a do wykonania oczyszczania, gdy okno zostanie zniszczone.  
  
 W tym przykładzie również używane [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) obiekt, aby włączyć wątku interfejsu użytkownika i wątku roboczego do komunikowania się ze sobą. Po wątku roboczego tworzy obraz, wysyła wskaźnik do `Bitmap` do obiektu `unbounded_buffer` obiektów i następnie przesyła komunikat paint do wątku interfejsu użytkownika. Wątku interfejsu użytkownika otrzyma z `unbounded_buffer` obiektu `Bitmap` obiektu i go rysuje w oknie klienta.  
  
#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Aby usunąć rysowania pracy z wątku interfejsu użytkownika  
  
1.  W pliku stdafx.h, Dodaj następujący `#include` dyrektywy:  
  
     [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]  
  
2.  W ChildView.h, Dodaj `task_group` i `unbounded_buffer` zmienne Członkowskie, aby `protected` sekcji `CChildView` klasy. `task_group` Obiekt zawiera zadania, które wykonywać Rysowanie; `unbounded_buffer` obiekt zawiera obraz Mandelbrot ukończone.  
  
     [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]  
  
3.  W ChildView.cpp, Dodaj `using` dyrektywy do `concurrency` przestrzeni nazw.  
  
     [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]  
  

4.  W `CChildView::DrawMandelbrot` po wywołaniu metody `Bitmap::UnlockBits`, wywołaj [concurrency::send](reference/concurrency-namespace-functions.md#send) funkcji, aby przekazać `Bitmap` obiekt do wątku interfejsu użytkownika. Następnie wysłać wiadomość malowania w wątku interfejsu użytkownika i unieważnić obszaru klienckiego.  

  
     [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]  
  
5.  Aktualizacja `CChildView::OnPaint` metodę, aby odbierać zaktualizowane `Bitmap` obiektu i rysowania obrazu do okna klienta.  
  
     [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]  
  
     `CChildView::OnPaint` Metoda tworzy zadanie do generowania obrazu Mandelbrot, jeśli jeszcze nie istnieje w buforze wiadomości. Bufor komunikatów nie będą zawierać `Bitmap` obiektu w przypadkach, takich jak wiadomości paint początkowej i inne okno zostanie przeniesiony na początku okna klienta.  
  
6.  Sprawdź, czy aplikacja została pomyślnie zaktualizowana, kompilowania i uruchamiając go.  
  
 Interfejs użytkownika jest teraz bardziej elastyczny rysowania praca jest wykonywana w tle.  
  
 [[Górnej](#top)]  
  
##  <a name="performance"></a> Poprawianie wydajności rysowania  

 Generowanie fraktalowy Mandelbrot są odpowiednimi kandydatami do paralelizacja, ponieważ obliczenia każdego piksela jest niezależna od wszystkich pozostałych obliczeń. Aby parallelize procedury rysunku, przekonwertować zewnętrznego `for` pętli w `CChildView::DrawMandelbrot` metody do wywołania [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytmu w następujący sposób.  

  
 [!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]  
  
 Obliczenia każdy element mapy bitowej są niezależne, nie trzeba synchronizacja operacji rysowania, które uzyskują dostęp do pamięci mapy bitowej. Dzięki temu wydajność, aby skalować jako liczba dostępnych procesorów wzrasta.  
  
 [[Górnej](#top)]  
  
##  <a name="cancellation"></a> Dodawanie obsługi anulowania  
 W tej sekcji opisano sposób obsługi zmianę rozmiaru okna i anulować wszystkie aktywne zadania rysunku, gdy okno zostanie zniszczone.  
  
 Dokument [anulowanie w PPL](cancellation-in-the-ppl.md) wyjaśniono sposób anulowania działania w czasie wykonywania. Anulowanie jest współpraca; w związku z tym nie występuje od razu. Aby zatrzymać anulowanych zadań, środowisko uruchomieniowe zgłasza wyjątek wewnętrzny podczas wywołania kolejne zadania w czasie wykonywania. Poprzedniej sekcji przedstawia sposób użycia `parallel_for` algorytmu, aby poprawić wydajność rysowania zadań. Wywołanie `parallel_for` środowisko uruchomieniowe można zatrzymać zadania i w związku z tym umożliwia anulowanie do pracy.  
  
### <a name="cancelling-active-tasks"></a>Anulowanie aktywnych zadań  
 Aplikacja Mandelbrot tworzy `Bitmap` obiektów, których wymiarów zgodny z rozmiarem okna klienta. Za każdym razem, gdy zmiany rozmiaru okna klienta, aplikacja tworzy dodatkowe zadania do generowania obrazu nowy rozmiar okna. Aplikacja nie wymaga tych obrazów pośredniego; wymaga on tylko obraz dla rozmiaru okna końcowego. Aby uniknąć wykonywania dodatkowej pracy aplikacji, możesz anulować wszystkie aktywne zadania rysowania w obsługi komunikatów dla `WM_SIZE` i `WM_SIZING` wiadomości, a następnie ponowne rysunku działać po zmieni się rozmiar okna.  
  
 Aby anulować aktywne zadania rysunku, gdy zmieniany jest rozmiar okna, aplikacja wywołuje [concurrency::task_group::cancel](reference/task-group-class.md#cancel) w programy obsługi dla metody `WM_SIZING` i `WM_SIZE` wiadomości. Program obsługi dla `WM_SIZE` wiadomości również wywołania [concurrency::task_group::wait](reference/task-group-class.md#wait) metody oczekiwania dla wszystkich aktywnych zadań do wykonania i zmienia harmonogram rysowania zadań dla rozmiaru okna zaktualizowane.  
  
 Gdy zostanie zniszczony okna klienta, jest dobrym rozwiązaniem, aby anulować wszystkie aktywne zadania rysowania. Anuluje wszystkie aktywne zadania rysowania upewnia się, że wątków roboczych nie publikowanie wiadomości w wątku interfejsu użytkownika po oknie klienta zostanie zniszczony. Aplikacja anuluje wszystkie aktywne zadania rysowania programu obsługi dla `WM_DESTROY` wiadomości.  
  
### <a name="responding-to-cancellation"></a>Odpowiada na żądania anulowania  
 `CChildView::DrawMandelbrot` Metodę, która wykonuje zadanie rysunku, musi odpowiadać na anulowanie. Ponieważ środowisko uruchomieniowe używa obsługi wyjątków, aby anulować zadania, `CChildView::DrawMandelbrot` — metoda musi używać mechanizmu wyjątek bezpieczeństwa, aby zagwarantować, że wszystkie zasoby są poprawnie oczyszczony. W tym przykładzie użyto *inicjowania jest nabywania zasobów* (RAII) wzorzec do gwarantuje, że mapa bitowa są odblokowane, gdy zadanie zostało anulowane.  
  
##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Aby dodać obsługę anulowania w aplikacji Mandelbrot  
  
1.  W ChildView.h w `protected` sekcji `CChildView` klasy, Dodaj deklaracje dla `OnSize`, `OnSizing`, i `OnDestroy` funkcje mapy komunikatów.  
  
     [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]  
  
2.  ChildView.cpp, zmodyfikuj mapy wiadomości zawiera obsługę `WM_SIZE`, `WM_SIZING`, i `WM_DESTROY` wiadomości.  
  
     [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]  
  
3.  Implementowanie `CChildView::OnSizing` metody. Ta metoda anuluje wszystkie istniejące zadania rysowania.  
  
     [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]  
  
4.  Implementowanie `CChildView::OnSize` metody. Ta metoda anuluje wszystkie istniejące zadania rysowania i utworzenie nowego zadania rysowania dla rozmiaru okna zaktualizowanego klienta.  
  
     [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]  
  
5.  Implementowanie `CChildView::OnDestroy` metody. Ta metoda anuluje wszystkie istniejące zadania rysowania.  
  
     [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]  
  
6.  W ChildView.cpp, zdefiniuj `scope_guard` klasy, która implementuje wzorzec RAII.  
  
     [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]  
  
7.  Dodaj następujący kod do `CChildView::DrawMandelbrot` metody po wywołaniu `Bitmap::LockBits`:  
  
     [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]  
  
     Ten kod obsługuje anulowania, tworząc `scope_guard` obiektu. Obiekt pozostawia zakresu, umożliwia odblokowanie mapa bitowa.  
  
8.  Modyfikowanie koniec `CChildView::DrawMandelbrot` metodę, aby odrzucić `scope_guard` obiektu po bitów mapy bitowej jest odblokowany, ale przed komunikaty są wysyłane do wątku interfejsu użytkownika. Dzięki temu wątku interfejsu użytkownika nie jest aktualizowana przed mapa bitowa są odblokowane.  
  
     [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]  
  
9. Sprawdź, czy aplikacja została pomyślnie zaktualizowana, kompilowania i uruchamiając go.  
  
 Podczas zmiany rozmiaru okna rysowania praca odbywa się tylko do rozmiaru końcowego okna. Wszystkie aktywne zadania rysowania są również anulowany, gdy okno zostanie zniszczone.  
  
 [[Górnej](#top)]  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność środowiska wykonawczego — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)   
 [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)   
 [Anulowanie w PPL](cancellation-in-the-ppl.md)   
 [Aplikacje klasyczne MFC](../../mfc/mfc-desktop-applications.md)
