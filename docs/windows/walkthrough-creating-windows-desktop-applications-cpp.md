---
title: 'Przewodnik: Tworzenie tradycyjnych aplikacji Windows Desktop (C++) | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 06/12/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 724772c0057d5defc8bfa3e2207df85d3a207f31
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590297"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Przewodnik: Tworzenie tradycyjnych aplikacji Windows Desktop (C++)

W tym instruktażu przedstawiono sposób tworzenia tradycyjnych aplikacji pulpitu Windows w programie Visual Studio. Przykładowa aplikacja, którą utworzysz użyto interfejsu API Windows, aby wyświetlić "Hello, pulpitu Windows!" w oknie. Można użyć kodu, który tworzysz w tym przewodniku jako wzorca do tworzenia innych aplikacji pulpitu Windows.

Interfejs API Windows (znany także jako interfejsu API systemu Win32, Windows Desktop z interfejsu API i klasycznego interfejsu API Windows) jest na podstawie języka C umożliwiająca tworzenie aplikacji Windows. Ona znajdowała się na istnienie od lat 1980 i został użyty do tworzenia aplikacji Windows używana od dziesięcioleci. Bardziej zaawansowane i łatwiejsze w programie struktur utworzone na podstawie tego interfejsu API, takie jak MFC, ATL i platformy .NET. Nawet najbardziej nowoczesnego kodu dla aplikacji platformy uniwersalnej systemu Windows i Store napisanych w języku C + +/ WinRT używa tego interfejsu API poniżej. Aby uzyskać więcej informacji na temat interfejsu API Windows, zobacz [indeks interfejsów API Windows](/windows/desktop/apiindex/windows-api-list). Istnieje wiele sposobów, aby tworzyć aplikacje Windows, ale jest to pierwszy.

> [!IMPORTANT]
> W celu skrócenia programu niektóre instrukcje kodu zostały pominięte w tekście. [Skompilować kod](#build-the-code) sekcji na końcu tego dokumentu zawiera kompletny kod.

## <a name="prerequisites"></a>Wymagania wstępne

- Komputer z systemem Microsoft Windows 7 lub nowszy. Zalecamy systemu Windows 10 dla najlepszego komfortu programowania.

- Kopia programu Visual Studio 2017. Aby uzyskać informacje na temat sposobu pobierania i instalowania programu Visual Studio, zobacz [Zainstaluj program Visual Studio](/visualstudio/install/install-visual-studio). Po uruchomieniu Instalatora, upewnij się, że **programowanie aplikacji klasycznych w języku C++** zaznaczono obciążenia. Nie martw się, jeśli nie zainstalował tego obciążenia podczas instalowania programu Visual Studio. Można ponownie uruchom Instalatora i zainstaluj go teraz.

   ![Programowanie aplikacji klasycznych w języku C++](../build/media/desktop-development-with-cpp.png "programowanie aplikacji klasycznych w języku C++")

- Zrozumienie podstaw przy użyciu programu Visual Studio IDE. Jeśli używano aplikacje komputerowe Windows przed prawdopodobnie można zachować. Aby zapoznać się z wprowadzeniem, zobacz [Przewodnik po funkcjach programu Visual Studio IDE](/visualstudio/ide/visual-studio-ide).

- Po zrozumieniu wystarczającą ilość podstawy języka C++ z nich skorzystać. Nie martw się — firma Microsoft nie robią niczego zbyt skomplikowana.

## <a name="create-a-windows-desktop-project"></a>Utwórz projekt Windows desktop

Wykonaj następujące kroki, aby utworzyć swój pierwszy projekt pulpitu Windows, a następnie wprowadź kod dla działającej aplikacji pulpitu Windows. Jeśli używasz wersji programu Visual Studio starszych niż program Visual Studio 2017 w wersji 15.3, przejdź do sekcji [do utworzenia projektu pulpitu Windows w programie Visual Studio 2017 RTM](#create-in-vs2017-rtm).

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017-update-153-and-later"></a>Aby utworzyć projekt pulpitu Windows w programie Visual Studio 2017 Update 15.3 i nowszych

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

### <a id="create-in-vs2017-rtm"></a> Aby utworzyć projekt pulpitu Windows w programie Visual Studio 2017 RTM

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

   Aby uzyskać informacje dotyczące parametrów i wartość zwracana przez tę funkcję, zobacz [punktu wejścia WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559).

   > [!NOTE]
   > Co to są wszystkich tych dodatkowych słów, takich jak `CALLBACK`, lub `HINSTANCE`, lub `_In_`? Tradycyjne interfejsu Windows API używa definicji typów i makra preprocesora często przeniesienia na poziom abstrakcji natychmiast niektórych szczegółów typów i specyficzne dla platformy kodu, np. Konwencje wywoływania, **__declspec** deklaracje i pragmy kompilatora. W programie Visual Studio, można użyć funkcji IntelliSense [Quick Info](/visualstudio/ide/using-intellisense#quick-info) funkcję, aby sprawdzić, co zdefiniować definicji typów i makra. Umieść kursor nad wyraz zainteresowaniach, aplikację lub wybierz ją i naciśnij klawisze ctrl-K, ctrl-I-niewielkie okno podręczne, który zawiera definicję. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](/visualstudio/ide/using-intellisense). Parametry i zwracane typy często używają *adnotacji SAL* ułatwiające catch błędy programowania. Aby uzyskać więcej informacji, zobacz [przy użyciu adnotacji SAL w celu zmniejszenia defektów kodu C/C++](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

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

   W tej funkcji możesz pisać kod obsługujący *wiadomości* które aplikacja otrzyma od Windows po *zdarzenia* wystąpić. Na przykład, jeśli użytkownik wybierze przycisk OK w aplikacji, Windows wyśle do Ciebie wiadomość i można napisać kod wewnątrz swojej `WndProc` funkcję, która nie jest pracę. Jest to nazywane *obsługi* zdarzenie. Można obsługiwać zdarzenia, które są istotne dla twojej aplikacji.

   Aby uzyskać więcej informacji, zobacz [procedury okna](https://msdn.microsoft.com/library/windows/desktop/ms632593).

### <a name="to-add-functionality-to-the-winmain-function"></a>Aby dodać funkcje do funkcji WinMain

1. W `WinMain` funkcji, możesz wypełnić struktury typu [WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577). Ta struktura zawiera informacje dotyczące okna, przykładowo, ikony aplikacji, koloru tła okna, nazwę aby wyświetlić na pasku tytułu i bardzo ważne, wskaźnik funkcji do odpowiedniej procedury okna. W poniższym przykładzie przedstawiono typowe `WNDCLASSEX` struktury.

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

   Aby uzyskać informacje o polach tej struktury, zobacz [WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577).

1. Musisz się zarejestrować, `WNDCLASSEX` przy użyciu Windows, tak że zna okna i sposobie wysyłania komunikatów do niego. Użyj [RegisterClassEx](https://msdn.microsoft.com/library/windows/desktop/ms633587) działać, a następnie przekazać strukturę klasy okna jako argument. `_T` Makro jest używane, ponieważ używamy `TCHAR` typu.

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

1. Teraz można utworzyć okna. Użyj [CreateWindow](https://msdn.microsoft.com/library/windows/desktop/ms632679) funkcji.

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

   Ta funkcja zwraca `HWND`, który jest uchwytem do okna. Dojście jest nieco jak wskaźnik, który Windows jest używane do śledzenia otwarte okna. Aby uzyskać więcej informacji, zobacz [typy danych Windows](https://msdn.microsoft.com/library/windows/desktop/aa383751).

1. W tym momencie okna została utworzona, ale nadal należy przekazać do Windows, aby była widoczna. To znaczy, co robi ten kod:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   Otwarte okno nie ma dużo zawartości, ponieważ nie zostało jeszcze zaimplementowane `WndProc` funkcji. Innymi słowy aplikacja nie obsługuje jeszcze wiadomości, które Windows jest teraz wysyłanie do niej.

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

   Aby uzyskać więcej informacji dotyczących struktur i funkcji w pętli komunikatów, zobacz [MSG](https://msdn.microsoft.com/library/windows/desktop/ms644958), [GetMessage](https://msdn.microsoft.com/library/windows/desktop/ms644936), [TranslateMessage](https://msdn.microsoft.com/library/windows/desktop/ms644955), i [DispatchMessage ](https://msdn.microsoft.com/library/windows/desktop/ms644934).

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

   Co ważne komunikat do obsłużenia to [WM_PAINT](https://msdn.microsoft.com/library/windows/desktop/dd145213) wiadomości. Aplikacja otrzymuje tę wiadomość, gdy część jej wyświetlanego okna musi zostać zaktualizowany. To zdarzenie może wystąpić, gdy użytkownik przesuwa okno przed okna, a następnie przenosi ją natychmiast ponownie. Aplikacja nie wie, po wystąpieniu zdarzenia następująco; tylko Windows zna, więc powiadomi użytkownika o `WM_PAINT`. Po wyświetleniu okna należy zaktualizować wszystkie.

   Aby obsłużyć `WM_PAINT` komunikatu, pierwsze wywołanie [BeginPaint](https://msdn.microsoft.com/library/windows/desktop/dd183362), a następnie obsłuż całą logikę układu tekstu, przycisków i innych kontrolek w oknie, a następnie wywołaj [EndPaint](https://msdn.microsoft.com/library/windows/desktop/dd162598). Dla tej aplikacji logika między wywołaniem rozpoczęcia z zakończenia jest wyświetlić napis "Hello, pulpitu Windows!" w oknie. W poniższym kodzie Zauważ, że [TextOut](https://msdn.microsoft.com/library/windows/desktop/dd145133) funkcja służy do wyświetlenia ciągu.

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

   `HDC` w tym kodzie jest uchwytem do kontekstu urządzenia, która jest strukturą danych, której Windows używa, aby umożliwić aplikacji do komunikowania się z podsystem grafiki. `BeginPaint` i `EndPaint` funkcji upewnij się, że aplikacja zachowuje się jak jest "pełnoprawnym" w dobrej i nie używa kontekstu urządzenia przez dłuższy czas, nie należy go. Pozwala to zagwarantować, że podsystem grafiki jest dostępny do użytku przez inne aplikacje.

1. Aplikacja zazwyczaj obsługuje wiele innych wiadomości, na przykład [WM_CREATE](https://msdn.microsoft.com/library/windows/desktop/ms632619) podczas okna i [WM_DESTROY](https://msdn.microsoft.com/library/windows/desktop/ms632620) po zamknięciu okna. Poniższy kod przedstawia podstawowe lecz ukończenia `WndProc` funkcji.

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

## <a name="see-also"></a>Zobacz też

[Aplikacje pulpitu Windows](../windows/windows-desktop-applications-cpp.md)