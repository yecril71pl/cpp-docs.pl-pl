---
title: "Wskazówki: Tworzenie tradycyjnych aplikacji pulpitu systemu Windows (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/09/2017
ms.reviewer: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.assetid: a247a9af-aff1-4899-9577-5f8104a0afbb
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8926e5e2432dea0e366698346df1d4b708517553
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Wskazówki: Tworzenie tradycyjnych aplikacji pulpitu systemu Windows (C++)

W tym przewodniku przedstawiono sposób tworzenia tradycyjnych aplikacji pulpitu systemu Windows w programie Visual Studio. Przykładowa aplikacja, którą utworzysz używa interfejsu API systemu Windows do wyświetlenia "Hello, pulpitu systemu Windows!" w oknie. Można użyć kodu, który opracowywania w tym przewodniku jako wzorzec do tworzenia innych aplikacji klasycznych systemu Windows.

Interfejs API systemu Windows (znanej także jako interfejs API Win32, interfejsu API z pulpitu systemu Windows i klasycznego interfejsu API systemu Windows) to platforma na podstawie języka C do tworzenia aplikacji systemu Windows. Go została istniejących od lat 1980 i została użyta do tworzenia aplikacji systemu Windows dla dekad. Bardziej zaawansowane i łatwiejsze do programów struktur zostały utworzone na podstawie tego interfejsu API, takich jak MFC i ATL, platformy .NET Framework. Nawet w przypadku najbardziej nowoczesnego kodu dla aplikacji platformy uniwersalnej systemu Windows, a także przechowywać napisany w języku C + +/ WinRT używa tego interfejsu API poniżej. Aby uzyskać więcej informacji na temat interfejsu API systemu Windows, zobacz [indeksu interfejsu API systemu Windows](https://msdn.microsoft.com/library/windows/desktop/ff818516.aspx). Istnieje wiele sposobów tworzenia aplikacji systemu Windows, ale było to pierwsze.

> [!IMPORTANT]
> W celu skrócenia niektórych instrukcje kodu zostały pominięte w tekście. [Kompilacji kodu](#build-the-code) sekcja na końcu tego dokumentu zawiera kompletny kod.

## <a name="prerequisites"></a>Wymagania wstępne

- Komputer z systemem Microsoft Windows 7 lub nowszy. Zalecamy systemu Windows 10 dla najlepsze środowisko programistyczne.

- Kopia programu Visual Studio 2017 r. Aby uzyskać informacje o tym, jak pobrać i zainstalować program Visual Studio, zobacz [zainstalować program Visual Studio 2017](/visualstudio/install/install-visual-studio). Po uruchomieniu Instalatora, upewnij się, że **tworzenia klasycznych aplikacji w języku C++** obciążenie jest zaznaczony. Nie martw się, należy zainstalować ten obciążenia podczas instalowania programu Visual Studio. Można ponownie uruchomić Instalatora i go teraz zainstalować.

   ![Tworzenie pulpitu za pomocą języka C++](../build/media/desktop-development-with-cpp.png "tworzenia klasycznych aplikacji w języku C++")

- Zrozumienie podstaw przy użyciu programu Visual Studio IDE. Jeśli używano aplikacji klasycznych systemu Windows przed, prawdopodobnie można zachować. Aby obejrzeć wprowadzenie, zobacz [samouczek funkcji programu Visual Studio IDE](/visualstudio/ide/visual-studio-ide).

- Opis wystarczającej podstawy języka C++ w odbiorze. Nie martw się, firma Microsoft nie wykonywać żadnych czynności, zbyt złożony.

## <a name="create-a-windows-desktop-project"></a>Tworzenie projektu pulpitu systemu Windows

Wykonaj następujące kroki, aby utworzyć pierwszy projekt pulpitu systemu Windows, a następnie wprowadź kod dla pracy aplikacji pulpitu systemu Windows. Jeśli używasz wersji programu Visual Studio starsze niż Visual Studio 2017 wersji 15 ustęp 3, przejdź do [do utworzenia projektu pulpitu systemu Windows w programie Visual Studio 2017 RTM](#create-in-vs2017-rtm).

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017-update-153-and-later"></a>Aby utworzyć projekt pulpitu systemu Windows w wersji Visual Studio 2017 aktualizacji 15 ustęp 3 i nowszych

1. Na **pliku** menu, wybierz **nowy** , a następnie wybierz **projektu**.

1. W **nowy projekt** okno dialogowe, w lewym okienku rozwiń **zainstalowana**, **Visual C++**, a następnie wybierz pozycję **Windows Desktop**. W środkowym okienku wybierz **kreatora pulpitu systemu Windows**.

   W **nazwa** wpisz nazwę projektu, na przykład *DesktopApp*. Wybierz **OK**.

   ![Nazwij projekt DesktopApp](../build/media/desktop-app-new-project-name-153.png "nazwij projekt DesktopApp")

1. W **projekt pulpitu systemu Windows** okna dialogowego, w obszarze **typu aplikacji**, wybierz pozycję **aplikacji systemu Windows (.exe)**. W obszarze **dodatkowe opcje**, wybierz pozycję **pusty projekt**. Wybierz **OK** Aby utworzyć projekt.

   ![Utwórz DesktopApp w Kreatorze projektu pulpitu systemu Windows](../build/media/desktop-app-new-project-wizard-153.png "utworzyć DesktopApp w Kreatorze projektu pulpitu systemu Windows")

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DesktopApp** projektu, wybierz **Dodaj**, a następnie wybierz pozycję **nowy element**.

   ![Dodaj nowy element do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Dodaj nowy element do projektu DesktopApp")

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **plik C++ (.cpp)**. W **nazwa** wpisz nazwę pliku, na przykład *HelloWindowsDesktop.cpp*. Wybierz **dodać**.

   ![Dodaj plik .cpp do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "pliku .cpp Dodaj do projektu DesktopApp")

Projekt został utworzony i pliku źródłowego jest otwarty w edytorze. Aby kontynuować, przejdź do [utworzyć kod](#create-the-code).

### <a id="create-in-vs2017-rtm"></a>Aby utworzyć projekt pulpitu systemu Windows w programie Visual Studio 2017 RTM

1. Na **pliku** menu, wybierz **nowy** , a następnie wybierz **projektu**.

1. W **nowy projekt** okno dialogowe, w lewym okienku rozwiń **zainstalowana**, **szablony**, **Visual C++**, a następnie wybierz **Win32**. W środkowym okienku wybierz **projektu Win32**.

   W **nazwa** wpisz nazwę projektu, na przykład *DesktopApp*. Wybierz **OK**.

   ![Nazwij projekt DesktopApp](../build/media/desktop-app-new-project-name-150.png "nazwij projekt DesktopApp")

1. Na **omówienie** strony **Kreator aplikacji Win32**, wybierz **dalej**.

   ![Utwórz DesktopApp w omówienie Kreator aplikacji Win32](../build/media/desktop-app-win32-wizard-overview-150.png "utworzyć DesktopApp w omówienie Kreator aplikacji Win32")

1. Na **ustawienia aplikacji** w obszarze **typu aplikacji**, wybierz pozycję **aplikacji systemu Windows**. W obszarze **dodatkowe opcje**, wybierz pozycję **pusty projekt**. Wybierz **Zakończ** Aby utworzyć projekt.

   ![Utwórz DesktopApp w ustawieniach Kreator aplikacji Win32](../build/media/desktop-app-win32-wizard-settings-150.png "utworzyć DesktopApp w ustawieniach Kreator aplikacji Win32")

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt DesktopApp, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **nowy element**.

   ![Dodaj nowy element do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-150.gif "Dodaj nowy element do projektu DesktopApp")

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **plik C++ (.cpp)**. W **nazwa** wpisz nazwę pliku, na przykład *HelloWindowsDesktop.cpp*. Wybierz **dodać**.

   ![Dodaj plik .cpp do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-150.png "pliku .cpp Dodaj do projektu DesktopApp")

Projekt został utworzony i pliku źródłowego jest otwarty w edytorze.

## <a name="create-the-code"></a>Utwórz kod

Następnie dowiesz się, jak utworzyć kodu dla aplikacji klasycznych systemu Windows w programie Visual Studio.

### <a name="to-start-a-windows-desktop-application"></a>Aby uruchomić aplikację pulpitu systemu Windows

1. Podobnie jak każdy C aplikacji i C++ musi mieć `main` działać jako punktu początkowego systemu Windows, co aplikacja musi mieć `WinMain` funkcji. `WinMain`ma następującą składnię.

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   Aby uzyskać informacje dotyczące parametrów i zwracanych wartości tej funkcji, zobacz [punktu wejścia WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559).

   > [!NOTE]
   > Co to są wszystkie dodatkowe słowa, takie jak **wywołania zwrotnego**, lub **wystąpienie HINSTANCE**, lub  **\_w\_**? Tradycyjnego interfejsu API systemu Windows używa definicje typów i makra preprocesora często do optymalizacji abstrakcyjnej niektóre szczegóły dotyczące platformy i typy kodu, takich jak wywoływanie Konwencji, **__declspec** deklaracje i pragmy kompilatora. W programie Visual Studio, można użyć funkcji IntelliSense [szybka podpowiedź](/visualstudio/ide/using-intellisense#quick-info) funkcję, aby sprawdzić, jakie zdefiniować te definicje typów i makra. Umieść kursor nad wyrazu zainteresowań, lub zaznacz go i naciśnij klawisze ctrl-K, ctrl-I-małe okno podręczne, który zawiera definicję. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](/visualstudio/ide/using-intellisense). Parametry i typy zwracane często używają *adnotacji SAL* ułatwiające catch błędy programowania. Aby uzyskać więcej informacji, zobacz [przy użyciu adnotacji SAL w celu zmniejszenia defektów kodu C/C++](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

1. Programy pulpitu systemu Windows wymagają &lt;windows.h >. &lt;tchar.h > definiuje `TCHAR` makra, który ostatecznie do `wchar_t` Jeśli UNICODE symbol jest zdefiniowany w projekcie, w przeciwnym razie rozpoznawany `char`.  Jeśli zawsze kompilacji z włączonym standardem UNICODE, nie ma potrzeby tchar — i wchar_t można użyć bezpośrednio.

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. Oprócz `WinMain` funkcji, każda aplikacja pulpitu systemu Windows musi mieć również funkcja procedurę okna. Zazwyczaj nosi nazwę tej funkcji `WndProc` , ale można określić nazwę dowolne. `WndProc`ma następującą składnię.

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hwnd,
      _In_ UINT   uMsg,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   W tej funkcji można napisać kod obsługujący *wiadomości* aplikacja odbierająca z systemu Windows po *zdarzenia* wystąpić. Na przykład, jeśli użytkownik wybierze przycisk OK w aplikacji, system Windows wyśle wiadomość do Ciebie i można napisać kod wewnątrz sieci `WndProc` funkcji, który wykonuje pracę jest odpowiedni. Ta metoda jest wywoływana *Obsługa* zdarzenia. Można obsługiwać zdarzenia, które są odpowiednie dla aplikacji.

   Aby uzyskać więcej informacji, zobacz [procedury okna](https://msdn.microsoft.com/library/windows/desktop/ms632593).

### <a name="to-add-functionality-to-the-winmain-function"></a>Dodawanie funkcji do funkcji WinMain

1. W `WinMain` funkcji, wypełnij struktura typu [WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577). Ta struktura zawiera informacje o oknie, na przykład ikona aplikacji, koloru tła okna nazwę do wyświetlania na pasku tytułu i bardzo ważne jest, wskaźnik funkcji do odpowiedniej procedury okna. W poniższym przykładzie przedstawiono typowe `WNDCLASSEX` struktury.

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

1. Należy zarejestrować `WNDCLASSEX` z systemem Windows, którego nie zna okna i jak należy wysyłać wiadomości do niej. Użyj [RegisterClassEx](https://msdn.microsoft.com/library/windows/desktop/ms633587) funkcji i przekazać w strukturze klas okno jako argument. `_T` Makro jest używane, ponieważ używamy `TCHAR` typu.

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

1. Teraz można utworzyć okna. Użyj [właściwości CreateWindow](https://msdn.microsoft.com/library/windows/desktop/ms632679) funkcji.

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

   Ta funkcja zwraca `HWND`, która jest dojścia do okna. Dojście jest w pewnym stopniu podobne do wskaźnika, używany do śledzenia okna w systemie Windows. Aby uzyskać więcej informacji, zobacz [typów danych systemu Windows](https://msdn.microsoft.com/library/windows/desktop/aa383751).

1. W tym momencie okna został utworzony, ale nadal trzeba widoczny w systemie Windows. To, czego ten kod:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   Wyświetlane okno nie ma dużo zawartości, ponieważ nie ma jeszcze zaimplementowane `WndProc` funkcji. Innymi słowy aplikacja nie obsługuje jeszcze wiadomości, które teraz system Windows wysyła do niego.

1. Do obsługi komunikatów, możemy najpierw dodać pętli komunikatów, aby odbierać komunikaty, które system Windows wysyła. Gdy aplikacja odbiera wiadomości, ta pętla wysyła go do Twojego `WndProc` funkcji, które mają być obsługiwane. Pętla wiadomości jest podobny do następującego kodu.

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   Aby uzyskać więcej informacji dotyczących struktury i funkcje w pętli komunikatów, zobacz [MSG](https://msdn.microsoft.com/library/windows/desktop/ms644958), [GetMessage](https://msdn.microsoft.com/library/windows/desktop/ms644936), [TranslateMessage](https://msdn.microsoft.com/library/windows/desktop/ms644955), i [DispatchMessage ](https://msdn.microsoft.com/library/windows/desktop/ms644934).

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

### <a name="to-add-functionality-to-the-wndproc-function"></a>Dodawanie funkcji do funkcji WndProc

1. Aby włączyć `WndProc` funkcji, aby obsługiwała komunikaty, które otrzymuje aplikacji, wdrożenie instrukcji switch.

   Co ważne komunikat do obsługi [WM_PAINT](https://msdn.microsoft.com/library/windows/desktop/dd145213) wiadomości. Po otrzymaniu tego komunikatu podczas części wyświetlane okna musi zostać zaktualizowany. To zdarzenie może wystąpić, gdy użytkownik przesuwa okno przed okna, a następnie przenosi je optymalizacji ponownie. Aplikacja nie może ustalić, kiedy wystąpiło zdarzenie takie; tylko Windows wie, powiadomi użytkownika o `WM_PAINT`. Po wyświetleniu okna należy zaktualizować wszystkie.

   Do obsługi `WM_PAINT` komunikatu, pierwsze wywołanie [BeginPaint](https://msdn.microsoft.com/library/windows/desktop/dd183362), następnie obsługi całą logikę do określania układu tekstu, przycisków i innych kontrolek w oknie, a następnie wywołać [EndPaint](https://msdn.microsoft.com/library/windows/desktop/dd162598). Dla tej aplikacji logiki między wywołania rozpoczęcia i zakończenia wywołania są wyświetlane ciąg "Hello, pulpitu systemu Windows!" w oknie. W poniższym kodzie, zwróć uwagę, że [TextOut](https://msdn.microsoft.com/library/windows/desktop/dd145133) funkcja służy do wyświetlania ciąg.

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

   `HDC`Ten kod jest dojścia do kontekstu urządzenia, który jest strukturą danych, która używa systemu Windows, aby umożliwić aplikacji do komunikowania się z podsystemem grafiki. `BeginPaint` i `EndPaint` funkcje upewnij się, że aplikacji zachowuje się jak dobrej obywateli i nie są używane przez dłuższy czas, niż jest wymagane do kontekstu urządzenia. Pomaga to zapewnić, że podsystem grafiki jest dostępny do użytku przez inne aplikacje.

1. Aplikacji zwykle obsługuje wiele innych komunikatów, na przykład [WM_CREATE](https://msdn.microsoft.com/library/windows/desktop/ms632619) podczas tworzenia okna i [WM_DESTROY](https://msdn.microsoft.com/library/windows/desktop/ms632620) po zamknięciu okna. Poniższy kod przedstawia podstawowy, ale ukończona `WndProc` funkcji.

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

Jak zapewnianą, w tym miejscu jest kompletny kod dla działającą aplikację.

### <a name="to-build-this-example"></a>Aby utworzyć w tym przykładzie

1. Usunięcie wszelkiego kodu, który został wprowadzony w HelloWindowsDesktop.cpp w edytorze. Skopiuj ten przykładowy kod i wklej go w HelloWindowsDesktop.cpp:

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

1. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**. Wyniki kompilacji powinna zostać wyświetlona w **dane wyjściowe** okna w programie Visual Studio.

   ![Skompiluj projekt DesktopApp](../build/media/desktop-app-project-build-150.gif "skompilować projekt DesktopApp")

1. Aby uruchomić aplikację, naciśnij klawisz **F5**. Okno zawierające tekst "Hello, pulpitu systemu Windows!" powinny być wyświetlane w lewym górnym rogu ekranu.

   ![Uruchom projekt DesktopApp](../build/media/desktop-app-project-run-150.gif "uruchomienia projektu DesktopApp")

Gratulacje! W tym przewodniku zakończeniu i wbudowane tradycyjnych aplikacji pulpitu systemu Windows.

## <a name="see-also"></a>Zobacz też

[Aplikacje systemu Windows](../windows/windows-desktop-applications-cpp.md)
