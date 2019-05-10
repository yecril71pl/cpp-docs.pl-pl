---
title: 'Przewodnik: Tworzenie tradycyjnych aplikacji Windows Desktop (C++)'
ms.custom: get-started-article
ms.date: 04/23/2019
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: 0bc9ef82863fde361964234cca54f12aac1e2abe
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877387"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Przewodnik: Tworzenie tradycyjnych aplikacji Windows Desktop (C++)

W tym instruktażu przedstawiono sposób tworzenia tradycyjnych aplikacji pulpitu Windows w programie Visual Studio. Przykładowa aplikacja, którą utworzysz użyto interfejsu API Windows, aby wyświetlić "Hello, pulpitu Windows!" w oknie. Można użyć kodu, który tworzysz w tym przewodniku jako wzorca do tworzenia innych aplikacji pulpitu Windows.

Interfejs API Windows (znany także jako interfejsu API systemu Win32, Windows Desktop z interfejsu API i klasycznego interfejsu API Windows) jest opartych na języku C architektura służąca do tworzenia aplikacji Windows. Ona znajdowała się na istnienie od lat 1980 i został użyty do tworzenia aplikacji Windows używana od dziesięcioleci. Bardziej zaawansowane i łatwiejsze w programie struktur utworzone na podstawie interfejsu API Windows, takie jak MFC, ATL i platformy .NET. Nawet najbardziej nowoczesnego kodu dla aplikacji platformy uniwersalnej systemu Windows i Store napisanych w C++/WinRT za pomocą interfejsu Windows API poniżej. Aby uzyskać więcej informacji na temat interfejsu API Windows, zobacz [indeks interfejsów API Windows](/windows/desktop/apiindex/windows-api-list). Istnieje wiele sposobów, aby tworzyć aplikacje Windows, ale z powyższej procedury wdrożyła jako pierwsza.

> [!IMPORTANT]
> W celu skrócenia programu niektóre instrukcje kodu zostały pominięte w tekście. [Skompilować kod](#build-the-code) sekcji na końcu tego dokumentu zawiera kompletny kod.

## <a name="prerequisites"></a>Wymagania wstępne

- Komputer z systemem Microsoft Windows 7 lub nowszy. Zalecamy systemu Windows 10 dla najlepszego komfortu programowania.

- Kopię programu Visual Studio. Aby uzyskać informacje na temat sposobu pobierania i instalowania programu Visual Studio, zobacz [Zainstaluj program Visual Studio](/visualstudio/install/install-visual-studio). Po uruchomieniu Instalatora, upewnij się, że **programowanie aplikacji klasycznych w języku C++** zaznaczono obciążenia. Nie martw się, jeśli nie zainstalował tego obciążenia podczas instalowania programu Visual Studio. Można ponownie uruchom Instalatora i zainstaluj go teraz.

   ![Programowanie aplikacji klasycznych w języku C++](../build/media/desktop-development-with-cpp.png "programowanie aplikacji klasycznych w języku C++")

- Zrozumienie podstaw przy użyciu programu Visual Studio IDE. Jeśli używano aplikacje komputerowe Windows przed prawdopodobnie można zachować. Aby zapoznać się z wprowadzeniem, zobacz [Przewodnik po funkcjach programu Visual Studio IDE](/visualstudio/ide/visual-studio-ide).

- Po zrozumieniu wystarczającą ilość podstawy języka C++ z nich skorzystać. Nie martw się — firma Microsoft nie robią niczego zbyt skomplikowana.

## <a name="create-a-windows-desktop-project"></a>Utwórz projekt Windows desktop

Wykonaj następujące kroki, aby utworzyć swój pierwszy projekt pulpitu Windows, a następnie wprowadź kod dla działającej aplikacji pulpitu Windows. Upewnij się, że selektor wersji, w lewym górnym rogu tej strony jest ustawiona na poprawną wersję programu Visual Studio, którego używasz.

::: moniker range="vs-2019"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2019"></a>Aby utworzyć projekt pulpitu Windows w programie Visual Studio 2019 r.

1. W menu głównym wybierz **pliku** > **New** > **projektu** otworzyć **Utwórz nowy projekt** okna dialogowego pole.

1. W górnej części okna dialogowego, ustaw **języka** do **C++** ustaw **platformy** do **Windows**i ustaw **Typprojektu** do **pulpitu**. 

1. Wybierz z listy filtrowanej typów projektów, **kreatora pulpitu Windows** wybierz **dalej**. Na następnej stronie podaj nazwę dla projektu, a następnie określ lokalizację projektu, w razie potrzeby.

1. Wybierz **Utwórz** przycisk, aby utworzyć projekt.

1. **Projektu pulpitu Windows** pojawi się okno dialogowe. W obszarze **typ aplikacji**, wybierz opcję **aplikacja Windows (.exe)**. W obszarze **dodatkowe opcje**, wybierz opcję **pusty projekt**. Wybierz **OK** do tworzenia projektu.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DesktopApp** projektu, wybierz **Dodaj**, a następnie wybierz **nowy element**.

   ![Dodaj nowy element do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Dodaj nowy element do projektu DesktopApp")

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **plik C++ (.cpp)**. W **nazwa** wpisz nazwę pliku, na przykład *HelloWindowsDesktop.cpp*. Wybierz **Dodaj**.

   ![Dodaj plik .cpp do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "Dodaj plik .cpp do DesktopApp projektu")

Projekt został utworzony i pliku źródłowego jest otwarty w edytorze. Aby kontynuować, przejdź do sekcji [utworzyć kod](#create-the-code).

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017"></a>Aby utworzyć projekt pulpitu Windows w programie Visual Studio 2017

1. Na **pliku** menu, wybierz **New** , a następnie wybierz **projektu**.

1. W **nowy projekt** rozwiń w lewym okienku w oknie dialogowym **zainstalowane** > **Visual C++**, a następnie wybierz **pulpitu Windows**. W środkowym okienku wybierz **kreatora pulpitu Windows**.

   W **nazwa** wpisz nazwę projektu, na przykład *DesktopApp*. Wybierz **OK**.

   ![Nazwij projekt DesktopApp](../build/media/desktop-app-new-project-name-153.png "nazwij projekt DesktopApp")

1. W **projektu pulpitu Windows** okna dialogowego, w obszarze **typ aplikacji**, wybierz opcję **aplikacja Windows (.exe)**. W obszarze **dodatkowe opcje**, wybierz opcję **pusty projekt**. Wybierz **OK** do tworzenia projektu.

   ![Utwórz DesktopApp w Kreatorze projektu pulpitu Windows](../build/media/desktop-app-new-project-wizard-153.png "tworzenie DesktopApp w Kreatorze projektu pulpitu Windows")

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DesktopApp** projektu, wybierz **Dodaj**, a następnie wybierz **nowy element**.

   ![Dodaj nowy element do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Dodaj nowy element do projektu DesktopApp")

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **plik C++ (.cpp)**. W **nazwa** wpisz nazwę pliku, na przykład *HelloWindowsDesktop.cpp*. Wybierz **Dodaj**.

   ![Dodaj plik .cpp do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "Dodaj plik .cpp do DesktopApp projektu")

Projekt został utworzony i pliku źródłowego jest otwarty w edytorze. Aby kontynuować, przejdź do sekcji [utworzyć kod](#create-the-code).

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2015"></a>Aby utworzyć projekt pulpitu Windows w programie Visual Studio 2015

1. Na **pliku** menu, wybierz **New** , a następnie wybierz **projektu**.

1. W **nowy projekt** rozwiń w lewym okienku w oknie dialogowym **zainstalowane** > **szablony** > **Visual C++**, a następnie wybierz pozycję **Win32**. W środkowym okienku wybierz **projekt systemu Win32**.

   W **nazwa** wpisz nazwę projektu, na przykład *DesktopApp*. Wybierz **OK**.

   ![Nazwij projekt DesktopApp](../build/media/desktop-app-new-project-name-150.png "nazwij projekt DesktopApp")

1. Na **Przegląd** strony **Kreatora aplikacji Win32**, wybierz **dalej**.

   ![Tworzenie DesktopApp w Omówienie Kreatora aplikacji Win32](../build/media/desktop-app-win32-wizard-overview-150.png "tworzenie DesktopApp w Omówienie Kreatora aplikacji Win32")

1. Na **ustawienia aplikacji** w obszarze **typ aplikacji**, wybierz opcję **aplikacji Windows**. W obszarze **dodatkowe opcje**, wybierz opcję **pusty projekt**. Wybierz **Zakończ** do tworzenia projektu.

   ![Utwórz DesktopApp ustawienia kreatora aplikacji Win32](../build/media/desktop-app-win32-wizard-settings-150.png "tworzenie DesktopApp ustawienia kreatora aplikacji Win32")

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt DesktopApp, wybierz pozycję **Dodaj**, a następnie wybierz **nowy element**.

   ![Dodaj nowy element do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-150.gif "Dodaj nowy element do projektu DesktopApp")

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **plik C++ (.cpp)**. W **nazwa** wpisz nazwę pliku, na przykład *HelloWindowsDesktop.cpp*. Wybierz **Dodaj**.

   ![Dodaj plik .cpp do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-150.png "Dodaj plik .cpp do DesktopApp projektu")

Projekt został utworzony i pliku źródłowego jest otwarty w edytorze.

::: moniker-end

## <a name="create-the-code"></a>Tworzenie kodu

Następnie dowiesz się, jak utworzyć kod dla aplikacji klasycznych Windows w programie Visual Studio.

### <a name="to-start-a-windows-desktop-application"></a>Aby uruchomić aplikację pulpitu Windows

1. Podobnie jak każdy C aplikacji i aplikacja C++ muszą mieć `main` działać jako punkt początkowy, Windows, co aplikacja komputerowa musi mieć `WinMain` funkcji. `WinMain` ma następującą składnię.

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   Aby uzyskać informacje dotyczące parametrów i wartość zwracana przez tę funkcję, zobacz [punktu wejścia WinMain](/windows/desktop/api/winbase/nf-winbase-winmain).

   > [!NOTE]
   > Co to są wszystkich tych dodatkowych słów, takich jak `CALLBACK`, lub `HINSTANCE`, lub `_In_`? Tradycyjne interfejsu Windows API używa definicji typów i makra preprocesora często przeniesienia na poziom abstrakcji natychmiast niektórych szczegółów typów i specyficzne dla platformy kodu, np. Konwencje wywoływania, **__declspec** deklaracje i pragmy kompilatora. W programie Visual Studio, można użyć funkcji IntelliSense [Quick Info](/visualstudio/ide/using-intellisense#quick-info) funkcję, aby sprawdzić, co zdefiniować definicji typów i makra. Umieść kursor nad wyraz zainteresowania, lub wybierz ją i naciśnij klawisz **Ctrl**+**K**, **Ctrl**+**I** dla niewielkie okno podręczne, który zawiera definicję. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](/visualstudio/ide/using-intellisense). Parametry i zwracane typy często używają *adnotacji SAL* ułatwiające catch błędy programowania. Aby uzyskać więcej informacji, zobacz [przy użyciu adnotacji SAL w celu zmniejszenia defektów kodu C/C++](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

1. Programy pulpitu Windows wymagają &lt;windows.h >. &lt;tchar.h > definiuje `TCHAR` makra, która jest rozpoznawana jako ostatecznie do **wchar_t** Jeśli symboli UNICODE jest zdefiniowany w projekcie, w przeciwnym razie jest on rozpoznawany jako **char**.  Zawsze w przypadku tworzenia z użyciem standardu UNICODE włączone, nie potrzebujesz tchar — i może po prostu użyj **wchar_t** bezpośrednio.

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. Oprócz `WinMain` funkcji, co aplikacja pulpitu Windows również musi mieć funkcję procedury okna. Ta funkcja jest typowo nazwana `WndProc` , ale można określić nazwę wedle uznania. `WndProc` ma następującą składnię.

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hwnd,
      _In_ UINT   uMsg,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   W tej funkcji możesz pisać kod obsługujący *wiadomości* które aplikacja otrzyma od Windows po *zdarzenia* wystąpić. Na przykład, jeśli użytkownik wybierze przycisk OK w aplikacji, Windows wyśle do Ciebie wiadomość i można napisać kod wewnątrz swojej `WndProc` funkcję, która nie jest pracę. Jest on nazywany *obsługi* zdarzenie. Można obsługiwać zdarzenia, które są istotne dla twojej aplikacji.

   Aby uzyskać więcej informacji, zobacz [procedury okna](/windows/desktop/winmsg/window-procedures).

### <a name="to-add-functionality-to-the-winmain-function"></a>Aby dodać funkcje do funkcji WinMain

1. W `WinMain` funkcji, możesz wypełnić struktury typu [WNDCLASSEX](/windows/desktop/api/winuser/ns-winuser-tagwndclassexa). Struktura zawiera informacje dotyczące okna, przykładowo, ikony aplikacji, koloru tła okna, nazwę aby wyświetlić na pasku tytułu, a co ważniejsze, wskaźnik funkcji do odpowiedniej procedury okna. W poniższym przykładzie przedstawiono typowe `WNDCLASSEX` struktury.

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

   Aby uzyskać informacje o polach powyżej struktury, zobacz [WNDCLASSEX](/windows/desktop/api/winuser/ns-winuser-tagwndclassexa).

1. Zarejestruj `WNDCLASSEX` przy użyciu Windows, tak że zna okna i sposobie wysyłania komunikatów do niego. Użyj [RegisterClassEx](/windows/desktop/api/winuser/nf-winuser-registerclassexa) działać, a następnie przekazać strukturę klasy okna jako argument. `_T` Makro jest używane, ponieważ używamy `TCHAR` typu.

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

1. Teraz można utworzyć okna. Użyj [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) funkcji.

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

   Ta funkcja zwraca `HWND`, który jest uchwytem do okna. Dojście jest nieco jak wskaźnik, który Windows jest używane do śledzenia otwarte okna. Aby uzyskać więcej informacji, zobacz [typy danych Windows](/windows/desktop/WinProg/windows-data-types).

1. W tym momencie okna została utworzona, ale nadal należy przekazać do Windows, aby była widoczna. To znaczy, co robi ten kod:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   Otwarte okno nie ma dużo zawartości, ponieważ jeszcze nie została jeszcze zaimplementowana `WndProc` funkcji. Innymi słowy aplikacja nie jest jeszcze obsługi wiadomości, które Windows jest teraz wysyłanie do niej.

1. Do obsługi wiadomości, możemy najpierw Dodaj pętlę komunikatów do nasłuchiwania wiadomości, które wysyła Windows. Kiedy aplikacja otrzymuje komunikat, ta pętla wysyła go do Twojego `WndProc` funkcji, które mają być obsługiwane. Pętli komunikatów przypomina poniższy kod.

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   Aby uzyskać więcej informacji dotyczących struktur i funkcji w pętli komunikatów, zobacz [MSG](/windows/desktop/api/winuser/ns-winuser-msg), [GetMessage](/windows/desktop/api/winuser/nf-winuser-getmessage), [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage), i [DispatchMessage ](/windows/desktop/api/winuser/nf-winuser-dispatchmessage).

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

### <a name="to-add-functionality-to-the-wndproc-function"></a>Aby dodać funkcje do funkcji WndProc

1. Aby włączyć `WndProc` funkcji obsługi wiadomości otrzymywanych przez aplikację, Wdróż instrukcję przełącznika.

   Co ważne komunikat do obsłużenia to [WM_PAINT](/windows/desktop/gdi/wm-paint) wiadomości. Aplikacja otrzymuje `WM_PAINT` wiadomości, gdy jest to część jej wyświetlanego okna musi zostać zaktualizowany. Zdarzenie może wystąpić, gdy użytkownik przesuwa okno przed okna, a następnie przenosi ją natychmiast ponownie, a aplikacja nie wiadomo, kiedy te zdarzenia występują. Tylko Windows zna, więc powiadomi użytkownika o `WM_PAINT`. Po wyświetleniu okna należy zaktualizować wszystkie.

   Aby obsłużyć `WM_PAINT` komunikatu, pierwsze wywołanie [BeginPaint](/windows/desktop/api/winuser/nf-winuser-beginpaint), a następnie obsłuż całą logikę układu tekstu, przycisków i innych kontrolek w oknie, a następnie wywołaj [EndPaint](/windows/desktop/api/winuser/nf-winuser-endpaint). Dla aplikacji logika między wywołaniem rozpoczęcia z zakończenia jest wyświetlić napis "Hello, pulpitu Windows!" w oknie. W poniższym kodzie Zauważ, że [TextOut](/windows/desktop/api/wingdi/nf-wingdi-textouta) funkcja służy do wyświetlenia ciągu.

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

   `HDC` w kodzie jest uchwytem do kontekstu urządzenia, która jest strukturą danych, której Windows używa, aby umożliwić aplikacji do komunikowania się z podsystem grafiki. `BeginPaint` i `EndPaint` funkcje zachowują się jak jest "pełnoprawnym" w dobrej aplikacji i nie używa kontekstu urządzenia przez dłuższy czas, nie należy go. Funkcje pomocy wykonującego podsystem grafiki jest dostępny do użytku przez inne aplikacje.

1. Aplikacja zazwyczaj obsługuje wiele innych wiadomości, na przykład [WM_CREATE](/windows/desktop/winmsg/wm-create) podczas okna i [WM_DESTROY](/windows/desktop/winmsg/wm-destroy) po zamknięciu okna. Poniższy kod przedstawia podstawowe lecz ukończenia `WndProc` funkcji.

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

## <a name="build-the-code"></a>Skompiluj kod

Rzeczywiście, Oto kompletny kod dla działającą aplikację.

### <a name="to-build-this-example"></a>Aby skompilować ten przykład

1. Usunięcie wszelkiego kodu, które zostały wprowadzone w *HelloWindowsDesktop.cpp* w edytorze. Skopiuj ten przykładowy kod i wklej go do *HelloWindowsDesktop.cpp*:

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
      _In_ HINSTANCE hPrevInstance,
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

1. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**. Wyniki kompilacji powinien pojawić się w **dane wyjściowe** okna w programie Visual Studio.

   ![Skompiluj projekt DesktopApp](../build/media/desktop-app-project-build-150.gif "kompilowania projektu DesktopApp")

1. Aby uruchomić aplikację, naciśnij klawisz **F5**. Okno zawierające tekst "Hello, pulpitu Windows!" powinien pojawić się w lewym górnym rogu ekranu.

   ![Uruchom projekt DesktopApp](../build/media/desktop-app-project-run-157.png "Uruchom projekt DesktopApp")

Gratulacje! W tym przewodniku zakończeniu i wbudowane tradycyjnych aplikacji pulpitu Windows.

## <a name="see-also"></a>Zobacz także

[Aplikacje pulpitu Windows](../windows/windows-desktop-applications-cpp.md)