---
title: 'Przewodnik: Tworzenie tradycyjnej aplikacji pulpitu systemu Windows (C++)'
description: Jak utworzyć minimalną, tradycyjną aplikację pulpitu systemu Windows przy użyciu programu Visual Studio, języka C++ i interfejsu API usługi Win32
ms.custom: get-started-article
ms.date: 11/03/2019
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: da74778e79a08dd3ed2b5be0675981425264bdc0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351851"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Przewodnik: Tworzenie tradycyjnej aplikacji pulpitu systemu Windows (C++)

W tym przewodniku pokazano, jak utworzyć tradycyjną aplikację klasyczną systemu Windows w programie Visual Studio. Przykładowa aplikacja, którą utworzysz używa interfejsu API systemu Windows do wyświetlania "Hello, Windows desktop!" w oknie. Można użyć kodu, który można opracować w tym instruktażu jako wzorzec do tworzenia innych aplikacji klasycznych systemu Windows.

Interfejs API systemu Windows (znany również jako interfejs API systemu Win32, interfejs API pulpitu systemu Windows i klasyczny interfejs API systemu Windows) jest platformą opartą na języku C do tworzenia aplikacji systemu Windows. Istnieje od 1980 roku i był używany do tworzenia aplikacji Systemu Windows przez dziesięciolecia. Bardziej zaawansowane i łatwiejsze do programowania struktury zostały zbudowane na górze interfejsu API systemu Windows. Na przykład MFC, ATL, .NET frameworks. Nawet najnowocześniejszy kod środowiska wykonawczego systemu Windows dla aplikacji platformy uniwersalnej systemu Windows i Sklepu napisany w języku C++/WinRT używa interfejsu API systemu Windows pod spodem. Aby uzyskać więcej informacji na temat interfejsu API systemu Windows, zobacz [Indeks interfejsu API systemu Windows](/windows/win32/apiindex/windows-api-list). Istnieje wiele sposobów tworzenia aplikacji systemu Windows, ale powyższy proces był pierwszy.

> [!IMPORTANT]
> Ze względu na zwięzłość niektóre instrukcje kodu są pomijane w tekście. Sekcja [Build kod](#build-the-code) na końcu tego dokumentu pokazuje pełny kod.

## <a name="prerequisites"></a>Wymagania wstępne

- Komputer z systemem Microsoft Windows 7 lub nowszymi wersjami. Firma Microsoft zaleca system Windows 10 dla najlepszego środowiska programowania.

- Kopia programu Visual Studio. Aby uzyskać informacje dotyczące pobierania i instalowania programu Visual Studio, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio). Po uruchomieniu instalatora upewnij się, że **programowanie pulpitu z** obciążeniem języka C++ jest sprawdzane. Nie martw się, jeśli nie zainstalowano tego obciążenia podczas instalowania programu Visual Studio. Instalator można ponownie uruchomić i zainstalować go teraz.

   ![Tworzenie komputerów stacjonarnych w języku C++](../build/media/desktop-development-with-cpp.png "Programowanie aplikacji klasycznych w języku C++")

- Zrozumienie podstaw korzystania z ide programu Visual Studio. Jeśli wcześniej używałeś aplikacji klasycznych systemu Windows, prawdopodobnie możesz nadążyć. Aby uzyskać wprowadzenie, zobacz [Visual Studio IDE przewodnik funkcji.](/visualstudio/ide/visual-studio-ide)

- Zrozumienie wystarczającej ilości podstaw języka C++, aby podążać za nim. Nie martw się, nie robimy nic zbyt skomplikowanego.

## <a name="create-a-windows-desktop-project"></a>Tworzenie projektu pulpitu systemu Windows

Wykonaj następujące kroki, aby utworzyć pierwszy projekt pulpitu systemu Windows. W miarę jak idziesz, wprowadzisz kod działającej aplikacji klasycznej Windows. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj formantu selektor **wersji.** Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2019"></a>Aby utworzyć projekt pulpitu systemu Windows w programie Visual Studio 2019

1. Z menu głównego wybierz polecenie **Plik** > **nowego** > **projektu,** aby otworzyć okno **dialogowe Tworzenie nowego projektu.**

1. W górnej części okna dialogowego ustaw **język** na **C++,** ustaw **platformę** na **Windows**i ustaw **typ projektu** na **Pulpit**.

1. Z filtru listy typów projektów wybierz pozycję **Kreator pulpitu systemu Windows,** a następnie wybierz pozycję **Dalej**. Na następnej stronie wprowadź nazwę projektu, na przykład *DesktopApp*.

1. Wybierz przycisk **Utwórz,** aby utworzyć projekt.

1. Zostanie wyświetlone okno dialogowe **Projekt pulpitu systemu Windows.** W obszarze **Typ aplikacji**wybierz pozycję **Aplikacja klasyczna (exe)**. W obszarze **Dodatkowe opcje**wybierz pozycję **Pusty projekt**. Wybierz **przycisk OK,** aby utworzyć projekt.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **Aplikacji DesktopApp,** wybierz polecenie **Dodaj**, a następnie wybierz polecenie **Nowy element**.

   ![Dodawanie nowego elementu do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Dodawanie nowego elementu do projektu DesktopApp")

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik języka **C++ (cpp)**. W polu **Nazwa** wpisz nazwę pliku, na przykład *HelloWindowsDesktop.cpp*. Wybierz **pozycję Dodaj**.

   ![Dodawanie pliku cpp do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "Dodawanie pliku cpp do projektu DesktopApp")

Projekt zostanie utworzony, a plik źródłowy zostanie otwarty w edytorze. Aby kontynuować, przejdź do przodu, [aby utworzyć kod](#create-the-code).

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017"></a>Aby utworzyć projekt pulpitu systemu Windows w programie Visual Studio 2017

1. W menu **Plik** wybierz polecenie **Nowy,** a następnie wybierz polecenie **Projekt**.

1. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń pozycję **Zainstalowany** > **program Visual C++**( **Windows Desktop ).** W środkowym okienku wybierz pozycję **Kreator pulpitu systemu Windows**.

   W polu **Nazwa** wpisz nazwę projektu, na przykład *DesktopApp*. Wybierz pozycję **OK**.

   ![Nadawanie nazwy projektowi DesktopApp](../build/media/desktop-app-new-project-name-153.png "Nadawanie nazwy projektowi DesktopApp")

1. W oknie dialogowym **Projekt pulpitu systemu Windows** w obszarze Typ **aplikacji**wybierz pozycję Aplikacja systemu **Windows (exe)**. W obszarze **Dodatkowe opcje**wybierz pozycję **Pusty projekt**. Upewnij się, że **wstępnie skompilowany nagłówek** nie jest zaznaczony. Wybierz **przycisk OK,** aby utworzyć projekt.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **Aplikacji DesktopApp,** wybierz polecenie **Dodaj**, a następnie wybierz polecenie **Nowy element**.

   ![Dodawanie nowego elementu do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Dodawanie nowego elementu do projektu DesktopApp")

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik języka **C++ (cpp)**. W polu **Nazwa** wpisz nazwę pliku, na przykład *HelloWindowsDesktop.cpp*. Wybierz **pozycję Dodaj**.

   ![Dodawanie pliku cpp do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "Dodawanie pliku cpp do projektu DesktopApp")

Projekt zostanie utworzony, a plik źródłowy zostanie otwarty w edytorze. Aby kontynuować, przejdź do przodu, [aby utworzyć kod](#create-the-code).

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2015"></a>Aby utworzyć projekt pulpitu systemu Windows w programie Visual Studio 2015

1. W menu **Plik** wybierz polecenie **Nowy,** a następnie wybierz polecenie **Projekt**.

1. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń pozycję **Zainstalowane** > **szablony** > **Visual C++,** a następnie wybierz pozycję **Win32**. W środkowym okienku wybierz pozycję **Projekt Win32**.

   W polu **Nazwa** wpisz nazwę projektu, na przykład *DesktopApp*. Wybierz pozycję **OK**.

   ![Nadawanie nazwy projektowi DesktopApp](../build/media/desktop-app-new-project-name-150.png "Nadawanie nazwy projektowi DesktopApp")

1. Na stronie **Przegląd** **Kreatora aplikacji Win32**wybierz pozycję **Dalej**.

   ![Omówienie tworzenia aplikacji DesktopApp w aplikacji Win32](../build/media/desktop-app-win32-wizard-overview-150.png "Omówienie tworzenia aplikacji DesktopApp w aplikacji Win32")

1. Na stronie **Ustawienia aplikacji** w obszarze **Typ aplikacji**wybierz pozycję Aplikacja **systemu Windows**. W obszarze **Dodatkowe opcje**wyczyść pole wyboru **Wstępnie skompilowany nagłówek**, a następnie wybierz pozycję Pusty **projekt**. Wybierz **pozycję Zakończ,** aby utworzyć projekt.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt Aplikacji DesktopApp, wybierz polecenie **Dodaj**, a następnie wybierz polecenie **Nowy element**.

   ![Dodawanie nowego elementu do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-150.gif "Dodawanie nowego elementu do projektu DesktopApp")

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik języka **C++ (cpp)**. W polu **Nazwa** wpisz nazwę pliku, na przykład *HelloWindowsDesktop.cpp*. Wybierz **pozycję Dodaj**.

   ![Dodawanie pliku cpp do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-150.png "Dodawanie pliku cpp do projektu DesktopApp")

Projekt zostanie utworzony, a plik źródłowy zostanie otwarty w edytorze.

::: moniker-end

## <a name="create-the-code"></a>Tworzenie kodu

Następnie dowiesz się, jak utworzyć kod dla aplikacji klasycznej systemu Windows w programie Visual Studio.

### <a name="to-start-a-windows-desktop-application"></a>Aby uruchomić aplikację klasyczną systemu Windows

1. Podobnie jak każda aplikacja C i C++ aplikacja musi mieć `main` funkcję jako `WinMain` punkt wyjścia, każda aplikacja pulpitu systemu Windows musi mieć funkcję. `WinMain`ma następującą składnię.

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_opt_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   Aby uzyskać informacje o parametrach i wartości zwracanej tej funkcji, zobacz [Punkt wejścia WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

   > [!NOTE]
   > Jakie są te wszystkie dodatkowe `CALLBACK`słowa, takie jak , lub `HINSTANCE`, lub `_In_`? Tradycyjny interfejs API systemu Windows używa typedefs i preprocesor makra szeroko do abstrakcji od niektórych szczegółów typów i kodu specyficzne dla platformy, takich jak wywoływanie konwencji, **__declspec** deklaracji i pragmas kompilatora. W programie Visual Studio można użyć funkcji [Szybkiej informacji](/visualstudio/ide/using-intellisense#quick-info) IntelliSense, aby zobaczyć, co definiują te definicje te typedefs i makra. Umieść wskaźnik myszy na interesującym go słowie lub wybierz go i naciśnij **klawisze Ctrl**+**K**, **Ctrl**+**I,** aby uzyskać małe okno podręczne zawierające definicję. Aby uzyskać więcej informacji, zobacz [Korzystanie z programu IntelliSense](/visualstudio/ide/using-intellisense). Parametry i typy zwracane często używają *adnotacji SAL,* aby ułatwić wyłapywać błędy programowania. Aby uzyskać więcej informacji, zobacz [Zmniejszanie wad kodu C/C++ za pomocą adnotacji SAL](/cpp/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

1. Programy klasyczne &lt;systemu Windows wymagają> windows.h. &lt;tchar.h> definiuje `TCHAR` makro, które ostatecznie rozwiązuje **wchar_t,** jeśli symbol UNICODE jest zdefiniowany w projekcie, w przeciwnym razie jest rozpoznawany jako **char**.  Jeśli zawsze tworzysz z włączoną unicode, nie potrzebujesz TCHAR i możesz po prostu użyć **wchar_t** bezpośrednio.

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. Wraz z `WinMain` funkcją każda aplikacja klasyczna systemu Windows musi mieć również funkcję procedury okna. Ta funkcja jest `WndProc`zazwyczaj nazwany , ale można nazwać go, co chcesz. `WndProc`ma następującą składnię.

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hWnd,
      _In_ UINT   message,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   W tej funkcji można napisać kod do obsługi *wiadomości,* które aplikacja otrzymuje z systemu Windows, gdy *wystąpią zdarzenia.* Na przykład jeśli użytkownik wybierze przycisk OK w aplikacji, system Windows wyśle wiadomość do `WndProc` Ciebie i można napisać kod wewnątrz funkcji, która wykonuje wszystko, co działa jest odpowiednie. To się nazywa *obsługa* zdarzenia. Obsługiwane tylko zdarzenia, które są istotne dla aplikacji.

   Aby uzyskać więcej informacji, zobacz [Procedury okna](/windows/win32/winmsg/window-procedures).

### <a name="to-add-functionality-to-the-winmain-function"></a>Aby dodać funkcjonalność do funkcji WinMain

1. W `WinMain` funkcji można wypełnić strukturę typu [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw). Struktura zawiera informacje o oknie: ikona aplikacji, kolor tła okna, nazwę wyświetlaną na pasku tytułu, między innymi. Co ważne, zawiera wskaźnik funkcji do procedury okna. W poniższym przykładzie przedstawiono typową `WNDCLASSEX` strukturę.

   ```cpp
   WNDCLASSEX wcex;

   wcex.cbSize         = sizeof(WNDCLASSEX);
   wcex.style          = CS_HREDRAW | CS_VREDRAW;
   wcex.lpfnWndProc    = WndProc;
   wcex.cbClsExtra     = 0;
   wcex.cbWndExtra     = 0;
   wcex.hInstance      = hInstance;
   wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
   wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
   wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
   wcex.lpszMenuName   = NULL;
   wcex.lpszClassName  = szWindowClass;
   wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);
   ```

   Aby uzyskać informacje na temat powyższych pól konstrukcji, zobacz [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw).

1. Zarejestruj `WNDCLASSEX` się w systemie Windows, aby wiedział o swoim oknie i jak wysyłać do niego wiadomości. Użyj [RegisterClassEx](/windows/win32/api/winuser/nf-winuser-registerclassexw) funkcji i przekazać strukturę klasy okna jako argument. Makro `_T` jest używane, ponieważ `TCHAR` używamy typu.

   ```cpp
   if (!RegisterClassEx(&wcex))
   {
      MessageBox(NULL,
         _T("Call to RegisterClassEx failed!"),
         _T("Windows Desktop Guided Tour"),
         NULL);

      return 1;
   }
   ```

1. Teraz możesz utworzyć okno. Użyj funkcji [CreateWindow.](/windows/win32/api/winuser/nf-winuser-createwindoww)

   ```cpp
   static TCHAR szWindowClass[] = _T("DesktopApp");
   static TCHAR szTitle[] = _T("Windows Desktop Guided Tour Application");

   // The parameters to CreateWindow explained:
   // szWindowClass: the name of the application
   // szTitle: the text that appears in the title bar
   // WS_OVERLAPPEDWINDOW: the type of window to create
   // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
   // 500, 100: initial size (width, length)
   // NULL: the parent of this window
   // NULL: this application does not have a menu bar
   // hInstance: the first parameter from WinMain
   // NULL: not used in this application
   HWND hWnd = CreateWindow(
      szWindowClass,
      szTitle,
      WS_OVERLAPPEDWINDOW,
      CW_USEDEFAULT, CW_USEDEFAULT,
      500, 100,
      NULL,
      NULL,
      hInstance,
      NULL
   );
   if (!hWnd)
   {
      MessageBox(NULL,
         _T("Call to CreateWindow failed!"),
         _T("Windows Desktop Guided Tour"),
         NULL);

      return 1;
   }
   ```

   Ta funkcja `HWND`zwraca , który jest dojściem do okna. Uchwyt jest trochę jak wskaźnik używany przez system Windows do śledzenia otwartych okien. Aby uzyskać więcej informacji, zobacz [Typy danych systemu Windows](/windows/win32/WinProg/windows-data-types).

1. W tym momencie okno zostało utworzone, ale nadal musimy poinformować system Windows, aby był widoczny. To, co robi ten kod:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   Wyświetlane okno nie ma dużo zawartości, ponieważ nie zostały `WndProc` jeszcze zaimplementowane funkcji. Innymi słowy aplikacja nie obsługuje jeszcze wiadomości, które teraz wysyła do niej system Windows.

1. Aby obsłużyć wiadomości, najpierw dodajemy pętlę komunikatów, aby nasłuchiwać wiadomości wysyłane przez system Windows. Gdy aplikacja odbiera komunikat, ta pętla `WndProc` wywołuje go do funkcji do obsługi. Pętla komunikatów przypomina następujący kod.

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   Aby uzyskać więcej informacji na temat struktur i funkcji w pętli komunikatów, zobacz [MSG](/windows/win32/api/winuser/ns-winuser-msg), [GetMessage](/windows/win32/api/winuser/nf-winuser-getmessage), [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).

   W tym momencie `WinMain` funkcja powinna przypominać następujący kod.

   ```cpp
   int WINAPI WinMain(HINSTANCE hInstance,
                      HINSTANCE hPrevInstance,
                      LPSTR lpCmdLine,
                      int nCmdShow)
   {
      WNDCLASSEX wcex;

      wcex.cbSize = sizeof(WNDCLASSEX);
      wcex.style          = CS_HREDRAW | CS_VREDRAW;
      wcex.lpfnWndProc    = WndProc;
      wcex.cbClsExtra     = 0;
      wcex.cbWndExtra     = 0;
      wcex.hInstance      = hInstance;
      wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
      wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
      wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
      wcex.lpszMenuName   = NULL;
      wcex.lpszClassName  = szWindowClass;
      wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);

      if (!RegisterClassEx(&wcex))
      {
         MessageBox(NULL,
            _T("Call to RegisterClassEx failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // Store instance handle in our global variable
      hInst = hInstance;

      // The parameters to CreateWindow explained:
      // szWindowClass: the name of the application
      // szTitle: the text that appears in the title bar
      // WS_OVERLAPPEDWINDOW: the type of window to create
      // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
      // 500, 100: initial size (width, length)
      // NULL: the parent of this window
      // NULL: this application dows not have a menu bar
      // hInstance: the first parameter from WinMain
      // NULL: not used in this application
      HWND hWnd = CreateWindow(
         szWindowClass,
         szTitle,
         WS_OVERLAPPEDWINDOW,
         CW_USEDEFAULT, CW_USEDEFAULT,
         500, 100,
         NULL,
         NULL,
         hInstance,
         NULL
      );

      if (!hWnd)
      {
         MessageBox(NULL,
            _T("Call to CreateWindow failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // The parameters to ShowWindow explained:
      // hWnd: the value returned from CreateWindow
      // nCmdShow: the fourth parameter from WinMain
      ShowWindow(hWnd,
         nCmdShow);
      UpdateWindow(hWnd);

      // Main message loop:
      MSG msg;
      while (GetMessage(&msg, NULL, 0, 0))
      {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
      }

      return (int) msg.wParam;
   }
   ```

### <a name="to-add-functionality-to-the-wndproc-function"></a>Aby dodać funkcjonalność do funkcji WndProc

1. Aby włączyć `WndProc` funkcję do obsługi komunikatów, które aplikacja odbiera, należy zaimplementować switch instrukcji.

   Jedną z ważnych wiadomości do obsługi jest [komunikat WM_PAINT.](/windows/win32/gdi/wm-paint) Aplikacja odbiera `WM_PAINT` komunikat, gdy część wyświetlanego okna musi zostać zaktualizowana. Zdarzenie może wystąpić, gdy użytkownik przesuwa okno przed oknem, a następnie przenosi je ponownie. Aplikacja nie wie, kiedy wystąpią te zdarzenia. Tylko system Windows wie, więc powiadamia `WM_PAINT` aplikację z komunikatem. Gdy okno jest wyświetlane po raz pierwszy, wszystko musi zostać zaktualizowane.

   Aby obsłużyć `WM_PAINT` wiadomość, najpierw zadzwoń do [BeginPaint](/windows/win32/api/winuser/nf-winuser-beginpaint), a następnie obsłuż całą logikę, aby rozłożyć tekst, przyciski i inne kontrolki w oknie, a następnie zadzwoń do [EndPaint](/windows/win32/api/winuser/nf-winuser-endpaint). W przypadku aplikacji logika między wywołaniem początkowym a wywołaniem końcowym polega na wyświetlenie ciągu "Hello, Windows desktop!" w oknie. W poniższym kodzie należy zauważyć, że [funkcja TextOut](/windows/win32/api/wingdi/nf-wingdi-textoutw) jest używana do wyświetlania ciągu.

   ```cpp
   PAINTSTRUCT ps;
   HDC hdc;
   TCHAR greeting[] = _T("Hello, Windows desktop!");

   switch (message)
   {
   case WM_PAINT:
      hdc = BeginPaint(hWnd, &ps);

      // Here your application is laid out.
      // For this introduction, we just print out "Hello, Windows desktop!"
      // in the top left corner.
      TextOut(hdc,
         5, 5,
         greeting, _tcslen(greeting));
      // End application-specific layout section.

      EndPaint(hWnd, &ps);
      break;
   }
   ```

   `HDC`w kodzie jest dojście do kontekstu urządzenia, który jest strukturą danych, która jest używana przez system Windows, aby umożliwić aplikacji komunikowanie się z podsystemem graficznym. `BeginPaint` Funkcje `EndPaint` i sprawiają, że aplikacja zachowuje się jak dobry obywatel i nie używa kontekstu urządzenia dłużej niż musi. Funkcje ułatwiają udostępnienie podsystemu graficznego do użytku przez inne aplikacje.

1. Aplikacja zazwyczaj obsługuje wiele innych komunikatów. Na przykład [WM_CREATE,](/windows/win32/winmsg/wm-create) gdy okno jest tworzone po raz pierwszy i [WM_DESTROY,](/windows/win32/winmsg/wm-destroy) gdy okno jest zamknięte. Poniższy kod przedstawia podstawową, ale pełną `WndProc` funkcję.

   ```cpp
   LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
   {
      PAINTSTRUCT ps;
      HDC hdc;
      TCHAR greeting[] = _T("Hello, Windows desktop!");

      switch (message)
      {
      case WM_PAINT:
         hdc = BeginPaint(hWnd, &ps);

         // Here your application is laid out.
         // For this introduction, we just print out "Hello, Windows desktop!"
         // in the top left corner.
         TextOut(hdc,
            5, 5,
            greeting, _tcslen(greeting));
         // End application specific layout section.

         EndPaint(hWnd, &ps);
         break;
      case WM_DESTROY:
         PostQuitMessage(0);
         break;
      default:
         return DefWindowProc(hWnd, message, wParam, lParam);
         break;
      }

      return 0;
   }
   ```

## <a name="build-the-code"></a>Kompilowanie kod

Zgodnie z obietnicą, oto kompletny kod dla aplikacji pracy.

### <a name="to-build-this-example"></a>Aby utworzyć ten przykład

1. Usuń dowolny kod wprowadzony w *HelloWindowsDesktop.cpp* w edytorze. Skopiuj ten przykładowy kod, a następnie wklej go do *HelloWindowsDesktop.cpp:*

   ```cpp
   // HelloWindowsDesktop.cpp
   // compile with: /D_UNICODE /DUNICODE /DWIN32 /D_WINDOWS /c

   #include <windows.h>
   #include <stdlib.h>
   #include <string.h>
   #include <tchar.h>

   // Global variables

   // The main window class name.
   static TCHAR szWindowClass[] = _T("DesktopApp");

   // The string that appears in the application's title bar.
   static TCHAR szTitle[] = _T("Windows Desktop Guided Tour Application");

   HINSTANCE hInst;

   // Forward declarations of functions included in this code module:
   LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM);

   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_opt_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   )
   {
      WNDCLASSEX wcex;

      wcex.cbSize = sizeof(WNDCLASSEX);
      wcex.style          = CS_HREDRAW | CS_VREDRAW;
      wcex.lpfnWndProc    = WndProc;
      wcex.cbClsExtra     = 0;
      wcex.cbWndExtra     = 0;
      wcex.hInstance      = hInstance;
      wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
      wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
      wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
      wcex.lpszMenuName   = NULL;
      wcex.lpszClassName  = szWindowClass;
      wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);

      if (!RegisterClassEx(&wcex))
      {
         MessageBox(NULL,
            _T("Call to RegisterClassEx failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // Store instance handle in our global variable
      hInst = hInstance;

      // The parameters to CreateWindow explained:
      // szWindowClass: the name of the application
      // szTitle: the text that appears in the title bar
      // WS_OVERLAPPEDWINDOW: the type of window to create
      // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
      // 500, 100: initial size (width, length)
      // NULL: the parent of this window
      // NULL: this application does not have a menu bar
      // hInstance: the first parameter from WinMain
      // NULL: not used in this application
      HWND hWnd = CreateWindow(
         szWindowClass,
         szTitle,
         WS_OVERLAPPEDWINDOW,
         CW_USEDEFAULT, CW_USEDEFAULT,
         500, 100,
         NULL,
         NULL,
         hInstance,
         NULL
      );

      if (!hWnd)
      {
         MessageBox(NULL,
            _T("Call to CreateWindow failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // The parameters to ShowWindow explained:
      // hWnd: the value returned from CreateWindow
      // nCmdShow: the fourth parameter from WinMain
      ShowWindow(hWnd,
         nCmdShow);
      UpdateWindow(hWnd);

      // Main message loop:
      MSG msg;
      while (GetMessage(&msg, NULL, 0, 0))
      {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
      }

      return (int) msg.wParam;
   }

   //  FUNCTION: WndProc(HWND, UINT, WPARAM, LPARAM)
   //
   //  PURPOSE:  Processes messages for the main window.
   //
   //  WM_PAINT    - Paint the main window
   //  WM_DESTROY  - post a quit message and return
   LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
   {
      PAINTSTRUCT ps;
      HDC hdc;
      TCHAR greeting[] = _T("Hello, Windows desktop!");

      switch (message)
      {
      case WM_PAINT:
         hdc = BeginPaint(hWnd, &ps);

         // Here your application is laid out.
         // For this introduction, we just print out "Hello, Windows desktop!"
         // in the top left corner.
         TextOut(hdc,
            5, 5,
            greeting, _tcslen(greeting));
         // End application-specific layout section.

         EndPaint(hWnd, &ps);
         break;
      case WM_DESTROY:
         PostQuitMessage(0);
         break;
      default:
         return DefWindowProc(hWnd, message, wParam, lParam);
         break;
      }

      return 0;
   }
   ```

1. W menu **Kompilacja** wybierz polecenie **Build Solution**. Wyniki kompilacji powinny pojawić się w oknie **Dane wyjściowe** w programie Visual Studio.

   ![Tworzenie projektu DesktopApp](../build/media/desktop-app-project-build-150.gif "Tworzenie projektu DesktopApp")

1. Aby uruchomić aplikację, naciśnij klawisz **F5**. Okno zawierające tekst "Hello, Windows desktop!" powinien pojawić się w lewym górnym rogu wyświetlacza.

   ![Uruchamianie projektu DesktopApp](../build/media/desktop-app-project-run-157.PNG "Uruchamianie projektu DesktopApp")

Gratulacje! Ukończyłeś ten przewodnik i zbudowano tradycyjną aplikację klasyczną systemu Windows.

## <a name="see-also"></a>Zobacz też

[Aplikacje klasyczne systemu Windows](../windows/windows-desktop-applications-cpp.md)
