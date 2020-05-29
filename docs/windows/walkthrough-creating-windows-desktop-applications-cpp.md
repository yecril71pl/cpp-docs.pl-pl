---
title: 'Przewodnik: Tworzenie tradycyjnej aplikacji klasycznej systemu Windows (C++)'
description: Jak utworzyć minimalną, tradycyjną aplikację klasyczną systemu Windows przy użyciu programu Visual Studio, C++ i Win32 API
ms.custom: get-started-article
ms.date: 05/28/2020
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: ac141c6ce9e4cce37b72808de488df7f94d116f7
ms.sourcegitcommit: 426e327c9f7c3a3b02300e3f924f9786d62958e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84206209"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Przewodnik: Tworzenie tradycyjnej aplikacji klasycznej systemu Windows (C++)

W tym instruktażu pokazano, jak utworzyć tradycyjną aplikację klasyczną systemu Windows w programie Visual Studio. Przykładowa aplikacja, którą utworzysz, używa interfejsu API systemu Windows do wyświetlania "Hello, Windows Desktop!" w oknie. Kod, który tworzysz w tym instruktażu, można użyć jako wzorca, aby utworzyć inne aplikacje klasyczne systemu Windows.

Interfejs API systemu Windows (znany również jako Win32 API, Windows Desktop API i Windows klasyczny interfejs API) to struktura oparta na języku C do tworzenia aplikacji systemu Windows. Jest ona istniena od 1980s i została użyta do tworzenia aplikacji systemu Windows dla dekad. Bardziej zaawansowane i prostsze struktury zostały utworzone w oparciu o interfejs API systemu Windows. Na przykład MFC, ATL, .NET Frameworks. Nawet najbardziej nowoczesny kod środowisko wykonawcze systemu Windows dla aplikacji platformy UWP i ze sklepu, które zostały zapisane w języku C++/WinRT, korzysta z interfejsu API systemu Windows poniżej. Aby uzyskać więcej informacji na temat interfejsu API systemu Windows, zobacz [indeks interfejsu API systemu Windows](/windows/win32/apiindex/windows-api-list). Istnieje wiele sposobów tworzenia aplikacji systemu Windows, ale powyższy proces jest pierwszy.

> [!IMPORTANT]
> W celu zwięzłości niektóre instrukcje kodu są pomijane w tekście. Sekcja [Build kodu](#build-the-code) na końcu tego dokumentu pokazuje kompletny kod.

## <a name="prerequisites"></a>Wymagania wstępne

- Komputer z systemem Microsoft Windows 7 lub nowszym. Zalecamy użycie systemu Windows 10 w celu uzyskania najlepszego środowiska programistycznego.

- Kopia programu Visual Studio. Aby uzyskać informacje na temat pobierania i instalowania programu Visual Studio, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio). Po uruchomieniu Instalatora upewnij się, że jest zaznaczone pole **Programowanie aplikacji klasycznych w języku C++** . Nie martw się, jeśli to obciążenie nie zostało zainstalowane podczas instalacji programu Visual Studio. Możesz ponownie uruchomić Instalatora i zainstalować go teraz.

   ![Programowanie aplikacji klasycznych w języku C++](../build/media/desktop-development-with-cpp.png "Programowanie aplikacji klasycznych w języku C++")

- Zrozumienie podstaw korzystania ze środowiska IDE programu Visual Studio. Jeśli wcześniej używasz aplikacji klasycznych systemu Windows, prawdopodobnie Zadbaj o to. Aby zapoznać się z wprowadzeniem, zobacz [Przewodnik po funkcji środowiska IDE programu Visual Studio](/visualstudio/ide/visual-studio-ide).

- Zrozumienie wystarczającej podstawy języka C++ do wykonania. Nie martw się, nie wykonujemy żadnych zbyt skomplikowane.

## <a name="create-a-windows-desktop-project"></a>Tworzenie projektu pulpitu systemu Windows

Wykonaj następujące kroki, aby utworzyć pierwszy projekt pulpitu systemu Windows. Po przejściu wprowadzisz kod dla działającej aplikacji klasycznej systemu Windows. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj kontrolki selektora **wersji** . Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2019"></a>Aby utworzyć projekt pulpitu systemu Windows w programie Visual Studio 2019

1. Z menu głównego wybierz pozycję **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Tworzenie nowego projektu** .

1. W górnej części okna dialogowego Ustaw **Język** na **C++**, ustaw **platformę** na **Windows**, a następnie ustaw **Typ projektu** na **Desktop**.

1. Z listy filtrowane typy projektów wybierz pozycję **Kreator pulpitu systemu Windows** , a następnie wybierz przycisk **dalej**. Na następnej stronie Wprowadź nazwę projektu, na przykład *DesktopApp*.

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt.

1. Zostanie wyświetlone okno dialogowe **projekt pulpitu systemu Windows** . W obszarze **Typ aplikacji**wybierz pozycję **aplikacja klasyczna (. exe)**. W obszarze **Opcje dodatkowe**wybierz pozycję **pusty projekt**. Wybierz **przycisk OK** , aby utworzyć projekt.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **DesktopApp** , wybierz polecenie **Dodaj**, a następnie wybierz polecenie **nowy element**.

   ![Dodaj nowy element do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Dodaj nowy element do projektu DesktopApp")

1. W oknie dialogowym **Dodaj nowy element** wybierz opcję **plik C++ (. cpp)**. W polu **Nazwa** wpisz nazwę pliku, na przykład *HelloWindowsDesktop. cpp*. Wybierz pozycję **Dodaj**.

   ![Dodaj plik CPP do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "Dodaj plik CPP do projektu DesktopApp")

Projekt jest teraz tworzony i plik źródłowy zostanie otwarty w edytorze. Aby kontynuować, przejdź do, aby [utworzyć kod](#create-the-code).

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017"></a>Aby utworzyć projekt pulpitu systemu Windows w programie Visual Studio 2017

1. W menu **plik** wybierz polecenie **Nowy** , a następnie wybierz **projekt**.

1. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń węzeł **zainstalowane**  >  **Visual C++**, a następnie wybierz pozycję **Windows Desktop**. W środkowym okienku wybierz pozycję **Kreator pulpitu systemu Windows**.

   W polu **Nazwa** wpisz nazwę projektu, na przykład *DesktopApp*. Wybierz przycisk **OK**.

   ![Nazwij projekt DesktopApp](../build/media/desktop-app-new-project-name-153.png "Nazwij projekt DesktopApp")

1. W oknie dialogowym **projekt pulpitu systemu Windows** w obszarze **Typ aplikacji**wybierz pozycję **aplikacja systemu Windows (exe)**. W obszarze **Opcje dodatkowe**wybierz pozycję **pusty projekt**. Upewnij się, że nie wybrano **prekompilowanego nagłówka** . Wybierz **przycisk OK** , aby utworzyć projekt.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **DesktopApp** , wybierz polecenie **Dodaj**, a następnie wybierz polecenie **nowy element**.

   ![Dodaj nowy element do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Dodaj nowy element do projektu DesktopApp")

1. W oknie dialogowym **Dodaj nowy element** wybierz opcję **plik C++ (. cpp)**. W polu **Nazwa** wpisz nazwę pliku, na przykład *HelloWindowsDesktop. cpp*. Wybierz pozycję **Dodaj**.

   ![Dodaj plik CPP do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "Dodaj plik CPP do projektu DesktopApp")

Projekt jest teraz tworzony i plik źródłowy zostanie otwarty w edytorze. Aby kontynuować, przejdź do, aby [utworzyć kod](#create-the-code).

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2015"></a>Aby utworzyć projekt pulpitu systemu Windows w programie Visual Studio 2015

1. W menu **plik** wybierz polecenie **Nowy** , a następnie wybierz **projekt**.

1. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń węzeł **zainstalowane**  >  **Szablony**  >  **Visual C++** a następnie wybierz opcję **Win32**. W środkowym okienku wybierz pozycję **projekt Win32**.

   W polu **Nazwa** wpisz nazwę projektu, na przykład *DesktopApp*. Wybierz przycisk **OK**.

   ![Nazwij projekt DesktopApp](../build/media/desktop-app-new-project-name-150.png "Nazwij projekt DesktopApp")

1. Na stronie **Przegląd** **Kreatora aplikacji Win32**wybierz pozycję **dalej**.

   ![Tworzenie DesktopApp w Kreatorze aplikacji Win32 — Omówienie](../build/media/desktop-app-win32-wizard-overview-150.png "Tworzenie DesktopApp w Kreatorze aplikacji Win32 — Omówienie")

1. Na stronie **Ustawienia aplikacji** w obszarze **Typ aplikacji**wybierz pozycję **aplikacja systemu Windows**. W obszarze **Opcje dodatkowe**Usuń zaznaczenie pola **prekompilowany nagłówek**, a następnie wybierz pozycję **pusty projekt**. Wybierz pozycję **Zakończ** , aby utworzyć projekt.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt DesktopApp, wybierz polecenie **Dodaj**, a następnie wybierz polecenie **nowy element**.

   ![Dodaj nowy element do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-150.gif "Dodaj nowy element do projektu DesktopApp")

1. W oknie dialogowym **Dodaj nowy element** wybierz opcję **plik C++ (. cpp)**. W polu **Nazwa** wpisz nazwę pliku, na przykład *HelloWindowsDesktop. cpp*. Wybierz pozycję **Dodaj**.

   ![Dodaj plik CPP do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-150.png "Dodaj plik CPP do projektu DesktopApp")

Projekt jest teraz tworzony i plik źródłowy zostanie otwarty w edytorze.

::: moniker-end

## <a name="create-the-code"></a>Utwórz kod

Następnie dowiesz się, jak utworzyć kod dla aplikacji klasycznych systemu Windows w programie Visual Studio.

### <a name="to-start-a-windows-desktop-application"></a>Aby uruchomić aplikację klasyczną systemu Windows

1. Tak jak w przypadku każdej aplikacji C i języka C++ musi istnieć `main` Funkcja jako punkt początkowy, każda aplikacja klasyczna systemu Windows musi mieć `WinMain` funkcję. `WinMain`ma następującą składnię.

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_opt_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   Aby uzyskać informacje na temat parametrów i wartości zwracanej przez tę funkcję, zobacz [WinMain Entry Point](/windows/win32/api/winbase/nf-winbase-winmain).

   > [!NOTE]
   > Jakie dodatkowe słowa są takie same, jak `CALLBACK` , lub `HINSTANCE` `_In_` ? Tradycyjny interfejs API systemu Windows używa wstępnie zdefiniowanych w tym samym makr elementów typedef i preprocesora w celu poszerzenia niektórych szczegółów typów i kodu specyficznego dla platformy, takich jak Konwencje wywoływania, deklaracje **__declspec** i dyrektywy pragma kompilatora. W programie Visual Studio można użyć funkcji IntelliSense [Quick info](/visualstudio/ide/using-intellisense#quick-info) , aby zobaczyć, co definiuje te definicje typów i makr. Umieść wskaźnik myszy nad wyrazem zainteresowania lub wybierz go, a następnie naciśnij klawisze **Ctrl** + **K**, **Ctrl** + **i** dla małego okna podręcznego, które zawiera definicję. Aby uzyskać więcej informacji, zobacz [Korzystanie z funkcji IntelliSense](/visualstudio/ide/using-intellisense). Parametry i typy zwracane często używają *adnotacji sal* , aby ułatwić przechwytywanie błędów programistycznych. Aby uzyskać więcej informacji, zobacz [Używanie adnotacji sal w celu zmniejszenia wad kodu C/C++](/cpp/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

1. Programy klasyczne systemu Windows wymagają &lt; systemu Windows. h>. &lt;Używanie TCHAR. h> definiuje `TCHAR` makro, które w końcu jest rozpoznawane jako **wchar_t** , jeśli symbol Unicode jest zdefiniowany w projekcie, w przeciwnym razie jest rozpoznawany jako **char**.  Jeśli zawsze kompilujesz przy użyciu standardu UNICODE, nie potrzebujesz używanie TCHAR i możesz bezpośrednio używać **wchar_t** .

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. Wraz z `WinMain` funkcją, każda aplikacja klasyczna systemu Windows musi mieć również funkcję okna. Ta funkcja jest zazwyczaj nazwana `WndProc` , ale można ją nazwać w dowolny sposób. `WndProc`ma następującą składnię.

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hWnd,
      _In_ UINT   message,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   W tej funkcji napiszesz kod obsługujący *komunikaty* odbierane przez aplikację od systemu Windows, gdy wystąpią *zdarzenia* . Na przykład, jeśli użytkownik wybierze przycisk OK w aplikacji, system Windows wyśle do Ciebie komunikat i będzie można napisać kod wewnątrz `WndProc` funkcji, która jest odpowiednia dla każdej pracy. Nazywa się to *obsługą* zdarzenia. Obsługiwane są tylko zdarzenia odpowiednie dla aplikacji.

   Aby uzyskać więcej informacji, zobacz sekcję [procedury okna](/windows/win32/winmsg/window-procedures).

### <a name="to-add-functionality-to-the-winmain-function"></a>Aby dodać funkcje do funkcji WinMain

1. W `WinMain` funkcji należy wypełnić strukturę typu [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw). Struktura zawiera informacje o oknie: ikona aplikacji, kolor tła okna, nazwa wyświetlana na pasku tytułu, między innymi. Co ważne, zawiera wskaźnik funkcji do procedury okna. W poniższym przykładzie przedstawiono typową `WNDCLASSEX` strukturę.

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

   Aby uzyskać informacje o polach struktury powyżej, zobacz [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw).

1. Zarejestruj się `WNDCLASSEX` w systemie Windows, aby wiedzieć o Twoim oknie i sposobach wysyłania do niego komunikatów. Użyj funkcji [RegisterClassEx](/windows/win32/api/winuser/nf-winuser-registerclassexw) i przekaż strukturę klasy okna jako argument. `_T`Makro jest używane, ponieważ korzystamy z tego `TCHAR` typu.

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

1. Teraz można utworzyć okno. Użyj funkcji [onwindow](/windows/win32/api/winuser/nf-winuser-createwindoww) .

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

   Ta funkcja zwraca `HWND` , który jest dojściem do okna. Dojście jest nieco podobne do wskaźnika używanego przez system Windows do śledzenia otwartych okien. Aby uzyskać więcej informacji, zobacz [typy danych systemu Windows](/windows/win32/WinProg/windows-data-types).

1. W tym momencie okno zostało utworzone, ale nadal musimy poinformować system Windows, aby był widoczny. Ten kod wykonuje następujące czynności:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   Wyświetlane okno nie ma dużo zawartości, ponieważ funkcja nie została jeszcze zaimplementowana `WndProc` . Innymi słowy, aplikacja nie obsługuje jeszcze komunikatów wysyłanych przez system Windows.

1. Aby obsłużyć komunikaty, najpierw dodamy pętlę komunikatów w celu nasłuchiwania komunikatów wysyłanych przez system Windows. Gdy aplikacja odbiera komunikat, ta pętla wysyła ją do `WndProc` funkcji, która ma być obsługiwana. Pętla komunikatów jest podobna do poniższego kodu.

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

   W tym momencie `WinMain` funkcja powinna wyglądać podobnie do poniższego kodu.

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

### <a name="to-add-functionality-to-the-wndproc-function"></a>Aby dodać funkcje do funkcji WndProc

1. Aby włączyć `WndProc` funkcję do obsługi komunikatów odbieranych przez aplikację, zaimplementuj instrukcję Switch.

   Jedną z ważnych komunikatów do obsłużenia jest komunikat [WM_PAINT](/windows/win32/gdi/wm-paint) . Aplikacja otrzymuje komunikat, `WM_PAINT` gdy należy zaktualizować część wyświetlonego okna. Zdarzenie może wystąpić, gdy użytkownik przenosi okno przed oknem, a następnie przenosi je ponownie. Aplikacja nie wie, kiedy wystąpią te zdarzenia. Tylko system Windows wie, że powiadamia on aplikację za pomocą `WM_PAINT` komunikatu. Po pierwszym wyświetleniu okna należy zaktualizować jego wszystkie.

   Aby obsłużyć `WM_PAINT` komunikat, najpierw Wywołaj [BeginPaint](/windows/win32/api/winuser/nf-winuser-beginpaint), a następnie obsłuż całą logikę w celu określenia układu tekstu, przycisków i innych kontrolek w oknie, a następnie Wywołaj [EndPaint](/windows/win32/api/winuser/nf-winuser-endpaint). W przypadku aplikacji logika między początkową wywołaniem a końcowym wywołaniem wyświetla ciąg "Hello, Windows Desktop!" w oknie. W poniższym kodzie funkcja [TextOut](/windows/win32/api/wingdi/nf-wingdi-textoutw) jest używana do wyświetlania ciągu.

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

   `HDC`kod jest uchwytem do kontekstu urządzenia, który jest używany do rysowania w obszarze klienta okna. Użyj `BeginPaint` funkcji i, `EndPaint` Aby przygotować się do i zakończyć rysowanie w obszarze klienta. `BeginPaint`zwraca dojście do kontekstu urządzenia wyświetlania używanego do rysowania w obszarze klienta. `EndPaint`zamyka żądanie malowania i zwalnia kontekst urządzenia.
   
1. Aplikacja zwykle obsługuje wiele innych komunikatów. Na przykład [WM_CREATE](/windows/win32/winmsg/wm-create) podczas pierwszego tworzenia okna i [WM_DESTROY](/windows/win32/winmsg/wm-destroy) po zamknięciu okna. Poniższy kod przedstawia podstawową funkcję, ale kompletną `WndProc` .

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

Zgodnie z oczekiwaniami, Oto pełen kod dla aplikacji działającej.

### <a name="to-build-this-example"></a>Aby skompilować ten przykład

1. Usuń kod wprowadzony w *HelloWindowsDesktop. cpp* w edytorze. Skopiuj ten przykładowy kod, a następnie wklej go do *HelloWindowsDesktop. cpp*:

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

1. W menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**. Wyniki kompilacji powinny pojawić się w oknie **danych wyjściowych** w programie Visual Studio.

   ![Kompilowanie projektu DesktopApp](../build/media/desktop-app-project-build-150.gif "Kompilowanie projektu DesktopApp")

1. Aby uruchomić aplikację, naciśnij klawisz **F5**. Okno zawierające tekst "Hello, Windows Desktop!" powinien pojawić się w lewym górnym rogu ekranu.

   ![Uruchamianie projektu DesktopApp](../build/media/desktop-app-project-run-157.PNG "Uruchamianie projektu DesktopApp")

Gratulacje! Ten Instruktaż został ukończony i opracowano tradycyjną aplikację klasyczną systemu Windows.

## <a name="see-also"></a>Zobacz także

[Aplikacje klasyczne systemu Windows](../windows/windows-desktop-applications-cpp.md)
