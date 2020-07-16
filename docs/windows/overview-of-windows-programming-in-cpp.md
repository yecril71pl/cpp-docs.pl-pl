---
title: Omówienie programowania w systemie Windows w języku C++
ms.date: 09/17/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 0aa667168f88f48458ae3a9b3541d4944f7530cc
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404990"
---
# <a name="overview-of-windows-programming-in-c"></a>Omówienie programowania w systemie Windows w języku C++

Istnieje kilka szerokich kategorii aplikacji systemu Windows, które można utworzyć przy użyciu języka C++. Każdy z nich ma własny model programowania i zestaw bibliotek specyficznych dla systemu Windows, ale biblioteki standardowej języka C++ i biblioteki C++ innych firm mogą być używane w dowolnym z nich.

W tej sekcji omówiono, jak używać programu Visual Studio i bibliotek otoki MFC/ATL do tworzenia programów systemu Windows. Aby uzyskać dokumentację dotyczącą platformy Windows, zobacz [dokumentację systemu Windows](/windows/index).

## <a name="command-line-console-applications"></a>Aplikacje wiersza polecenia (konsoli)

Aplikacje konsolowe języka C++ są uruchamiane z wiersza polecenia w oknie konsoli i mogą wyświetlać tylko dane wyjściowe. Aby uzyskać więcej informacji, zobacz [Tworzenie kalkulatora konsoli w języku C++](../get-started/tutorial-console-cpp.md).

## <a name="native-desktop-client-applications"></a>Natywne aplikacje klienckie dla komputerów stacjonarnych

*Natywna aplikacja kliencka* jest aplikacją z okienkiem c lub C++, która używa oryginalnych [interfejsów API Windows C lub Component Object Model (com)](/windows/win32/apiindex/windows-api-list) do uzyskania dostępu do systemu operacyjnego. Te interfejsy API są napisywane głównie w języku C. Istnieje więcej niż jeden sposób tworzenia natywnej aplikacji klasycznej: można programować bezpośrednio przy użyciu interfejsów API Win32 przy użyciu pętli komunikatów w stylu języka C, która przetwarza zdarzenia systemu operacyjnego. Lub można programować za pomocą *Microsoft Foundation Classes* (MFC), zorientowanej obiektowo biblioteki języka C++, która otacza system Win32. Żadna metoda nie jest uważana za "nowoczesny" w porównaniu do platforma uniwersalna systemu Windows (platformy UWP), ale obie są nadal w pełni obsługiwane i mają miliony wierszy kodu uruchomionego na świecie już dziś. Aplikacja Win32 uruchamiana w oknie wymaga, aby deweloper działał jawnie z komunikatami systemu Windows w ramach funkcji procedury systemu Windows. Pomimo nazwy, aplikacja Win32 może być skompilowana jako plik binarny 32-bitowy (x86) lub 64-bitowy (x64). W środowisku IDE programu Visual Studio warunki x86 i Win32 są synonimami.

Aby rozpocząć pracę z tradycyjnym programowaniem systemu Windows C++, zobacz Wprowadzenie [do systemu Win32 i C++](/windows/win32/LearnWin32/learn-to-program-for-windows). Po uzyskaniu pewnych informacji dotyczących systemu Win32 będzie łatwiej poznać [aplikacje klasyczne MFC](../mfc/mfc-desktop-applications.md). Przykład tradycyjnej aplikacji klasycznej C++, która używa zaawansowanej grafiki, zobacz [Hilo: Programowanie aplikacji C++ dla systemu Windows](/previous-versions/msdn10/ff708696(v=msdn.10)).

### <a name="c-or-net"></a>C++ lub .NET?

Ogólnie rzecz biorąc, programowanie .NET w języku C# jest mniej skomplikowane, mniej podatne na błędy i ma bardziej nowoczesny interfejs API zorientowany obiektowo niż Win32 lub MFC. W większości przypadków jego wydajność jest większa niż odpowiednia. Program .NET oferuje Windows Presentation Foundation (WPF) dla zaawansowanej grafiki, a także może korzystać z Win32 i nowoczesnego interfejsu API środowisko wykonawcze systemu Windows. Zgodnie z ogólną regułą zaleca się używanie języka C++ dla aplikacji klasycznych, gdy jest to wymagane:

- precyzyjne sterowanie użyciem pamięci
- najwyższą ekonomię w zużyciu mocy
- Użycie procesora GPU do obliczeń ogólnych
- dostęp do programu DirectX
- duże użycie standardowych bibliotek C++

Istnieje również możliwość łączenia mocy i wydajności języka C++ z programowaniem .NET. Interfejs użytkownika można utworzyć w języku C# i użyć języka C++/CLI, aby umożliwić aplikacji korzystanie z natywnych bibliotek C++. Aby uzyskać więcej informacji, zobacz [programowanie .NET przy użyciu języka C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="com-components"></a>Składniki COM

[Component Object Model (com)](/windows/win32/com/the-component-object-model) to specyfikacja, która umożliwia programom w różnych językach komunikowanie się ze sobą. Wiele składników systemu Windows jest implementowanych jako obiekty COM i są zgodne ze standardowymi regułami COM na potrzeby tworzenia obiektów, odnajdywania interfejsów i niszczenia obiektów.  Korzystanie z obiektów COM z aplikacji klasycznych C++ jest stosunkowo proste, ale pisanie własnego obiektu COM jest bardziej zaawansowane. [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) zawiera makra i funkcje pomocnika, które upraszczają programowanie com. Aby uzyskać więcej informacji, zobacz [składniki komputera ATL com](../atl/atl-com-desktop-components.md).

## <a name="universal-windows-platform-apps"></a>Aplikacje platforma uniwersalna systemu Windows

Platforma uniwersalna systemu Windows (platformy UWP) to nowoczesny interfejs API systemu Windows. Aplikacje platformy UWP działają na dowolnym urządzeniu z systemem Windows 10, używaj języka XAML dla interfejsu użytkownika i są w pełni dostępne. Aby uzyskać więcej informacji na temat platformy UWP, zobacz [co to jest aplikacja platforma uniwersalna systemu Windows (platformy UWP)?](/windows/uwp/get-started/whats-a-uwp) i [Przewodnik po aplikacjach uniwersalnych systemu Windows](/windows/uwp/get-started/universal-application-platform-guide).

Oryginalna obsługa języka C++ dla platformy UWP obejmowała (1) C++/CX, dialekt języka C++ z rozszerzeniami składni lub (2) Biblioteka środowisko wykonawcze systemu Windows (WRL), która jest oparta na standardach C++ i COM. Zarówno C++/CX, jak i WRL są nadal obsługiwane. W przypadku nowych projektów zalecamy użycie [języka c++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), który jest całkowicie oparty na standardzie c++ i zapewnia lepszą wydajność.

## <a name="desktop-bridge"></a>Mostek Desktop

W systemie Windows 10 można spakować istniejącą aplikację klasyczną lub obiekt COM jako aplikację platformy UWP oraz dodać funkcje platformy UWP, takie jak Touch, lub wywołać interfejsy API z nowoczesnego zestawu interfejsów API systemu Windows. Możesz również dodać aplikację platformy UWP do rozwiązania pulpitu w programie Visual Studio i spakować je razem w jednym pakiecie i używać interfejsów API systemu Windows do komunikacji między nimi.

Program Visual Studio 2017 w wersji 15,4 i nowszej umożliwia utworzenie projektu pakietu aplikacji systemu Windows w celu znacznego uproszczenia pracy pakowania istniejącej aplikacji klasycznej. Istnieją pewne ograniczenia dotyczące wywołań rejestru lub interfejsów API, które mogą być używane przez aplikację klasyczną. Jednak w wielu przypadkach można utworzyć alternatywne ścieżki kodu, aby osiągnąć podobną funkcjonalność podczas działania w pakiecie aplikacji. Aby uzyskać więcej informacji, zobacz [mostek Desktop](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Gry

Gry DirectX można uruchamiać na komputerze lub w konsoli Xbox. Aby uzyskać więcej informacji, zobacz [grafika i gry DirectX](/windows/win32/directx).

## <a name="sql-server-database-clients"></a>Klienci bazy danych SQL Server

Aby uzyskać dostęp do SQL Server baz danych z kodu natywnego, użyj ODBC lub OLE DB. Aby uzyskać więcej informacji, zobacz [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Sterowniki urządzeń dla systemu Windows

Sterowniki to składniki niskiego poziomu, które tworzą dane z urządzeń sprzętowych, które są dostępne dla aplikacji i innych składników systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [zestaw sterowników systemu Windows (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>Usługi systemu Windows

*Usługa* systemu Windows to program, który można uruchomić w tle z małą lub bez interakcji z użytkownikiem. Te programy są nazywane *demonami* w systemach UNIX. Aby uzyskać więcej informacji, zobacz [usługi](/windows/win32/services/services).

## <a name="sdks-libraries-and-header-files"></a>Zestawy SDK, biblioteki i pliki nagłówkowe

Program Visual Studio zawiera bibliotekę środowiska uruchomieniowego języka C (CRT), standardową bibliotekę C++ i inne biblioteki specyficzne dla firmy Microsoft. Większość folderów include zawierających pliki nagłówkowe dla tych bibliotek znajduje się w katalogu instalacyjnym programu Visual Studio w folderze \VC\. Pliki nagłówkowe systemu Windows i CRT znajdują się w folderze instalacji Windows SDK.

[Menedżer pakietów Vcpkg](../build/vcpkg.md) umożliwia wygodną instalację setek bibliotek typu open-source innych firm dla systemu Windows.

Biblioteki firmy Microsoft obejmują:

- Microsoft Foundation Classes (MFC): Zorientowana obiektowo platforma do tworzenia tradycyjnych programów systemu Windows — szczególnie aplikacji dla przedsiębiorstw — które cechuje bogaty interfejs użytkownika zawierający przyciski, pola listy, widoki drzewa i inne formanty. Aby uzyskać więcej informacji, zobacz [aplikacje klasyczne MFC](../mfc/mfc-desktop-applications.md).

- Active Template Library (ATL): Zaawansowana biblioteka pomocnicza do tworzenia składników modelu COM. Aby uzyskać więcej informacji, zobacz [składniki komputera ATL com](../atl/atl-com-desktop-components.md).

- C++ Accelerated Massive Parallelism (C++ AMP): Biblioteka, która umożliwia wykonywanie wysokiej wydajności obliczeń ogólnego przeznaczenia na procesorach GPU. Aby uzyskać więcej informacji, zobacz [C++ amp (C++ Accelerated Massive parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Środowisko uruchomieniowe współbieżności: Biblioteka, która upraszcza pracę przy programowaniu współbieżnym i asynchronicznym dla urządzeń wielordzeniowych. Aby uzyskać więcej informacji, zobacz [środowisko uruchomieniowe współbieżności](../parallel/concrt/concurrency-runtime.md).

Wiele scenariuszy programowania dla systemu Windows wymaga również Windows SDK, które zawiera pliki nagłówkowe umożliwiające dostęp do składników systemu operacyjnego Windows. Domyślnie program Visual Studio instaluje Windows SDK jako składnik obciążeń klasycznych w języku C++, co umożliwia programowanie aplikacji uniwersalnych systemu Windows. Do tworzenia aplikacji platformy UWP wymagana jest wersja systemu Windows 10 dla Windows SDK. Aby uzyskać więcej informacji, zobacz [zestaw SDK systemu Windows 10](https://dev.windows.com/downloads/windows-10-sdk). (Aby uzyskać więcej informacji na temat zestawów SDK systemu Windows dla wcześniejszych wersji systemu Windows, zobacz [archiwum Windows SDK](https://developer.microsoft.com/windows/downloads/sdk-archive).

**Program Files (x86) \Windows Kit** jest domyślną lokalizacją dla wszystkich wersji Windows SDK, które zostały zainstalowane.

Inne platformy, takie jak Xbox i Azure, mają swoje własne zestawy SDK, które również można zainstalować. Aby uzyskać więcej informacji, zobacz Centrum deweloperów DirectX i Centrum deweloperów Azure.

## <a name="development-tools"></a>Narzędzia programistyczne

Środowisko Visual Studio zawiera zaawansowany debuger kodu natywnego, narzędzia do analizy statycznej, graficzne narzędzia do debugowania, profesjonalny edytor kodu, wsparcie dla testów jednostkowych i wiele innych narzędzi. Aby uzyskać więcej informacji, zobacz Wprowadzenie do programowania [w programie Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)i [Omówienie programowania w języku C++ w programie Visual Studio](../overview/overview-of-cpp-development.md).

## <a name="in-this-section"></a>W tej sekcji

|Tytuł|Opis|
|-----------|-----------------|
|[Przewodnik: Tworzenie standardowego programu C++](walkthrough-creating-a-standard-cpp-program-cpp.md)| Utwórz aplikację konsolową systemu Windows.|
|[Przewodnik: tworzenie aplikacji klasycznych systemu Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Utwórz natywną aplikację klasyczną systemu Windows.|
|[Kreator pulpitu systemu Windows](windows-desktop-wizard.md)|Użyj kreatora, aby utworzyć nowe projekty systemu Windows.|
|[Biblioteka aktywnych szablonów (Active Template Library — ATL)](../atl/atl-com-desktop-components.md)|Użyj biblioteki ATL do tworzenia składników modelu COM w języku C++.|
|[Microsoft Foundation Classes (MFC)](../mfc/mfc-desktop-applications.md)|Używanie MFC do tworzenia dużych lub małych aplikacji systemu Windows przy użyciu okien dialogowych i kontrolek|
|[Biblioteki ATL i klasy udostępnione MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)|Używaj klas, takich jak CString, które są współużytkowane w ATL i MFC.|
|[Dostęp do danych](../data/data-access-in-cpp.md)| OLE DB i ODBC|
|[Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)|Różne typy ciągów w systemie Windows.|
|[Zasoby służące do tworzenia gier za pomocą programu DirectX](resources-for-creating-a-game-using-directx.md)
|[Instrukcje: korzystanie z zestawu SDK systemu Windows 10 w aplikacji klasycznej systemu Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Zestaw SDK systemu Windows|
|[Praca z plikami zasobów](working-with-resource-files.md)|Jak dodać obrazy, ikony, tabele ciągów i inne zasoby do aplikacji klasycznej.|
|[Zasoby służące do tworzenia gier za pomocą programu DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Linki do zawartości na potrzeby tworzenia gier w języku C++.|
|[Instrukcje: korzystanie z zestawu SDK systemu Windows 10 w aplikacji klasycznej systemu Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Zawiera kroki konfigurowania projektu do kompilowania przy użyciu zestawu SDK systemu Windows 10.|
|[Wdrażanie natywnych aplikacji klasycznych](deploying-native-desktop-applications-visual-cpp.md)|Wdrażaj aplikacje natywne w systemie Windows.|

## <a name="related-articles"></a>Powiązane artykuły

|Tytuł|Opis|
|-----------|-----------------|
|[Język C++ w programie Visual Studio](../overview/visual-cpp-in-visual-studio.md)|Temat nadrzędny dla Visual C++ zawartości dla deweloperów.|
[Programowanie na platformie .NET przy użyciu języka C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Tworzenie otok dla natywnych bibliotek języka C++, które umożliwiają komunikację z aplikacjami i składnikami platformy .NET.|
|[Rozszerzenia składników dla platform .NET i platformy UWP](../extensions/component-extensions-for-runtime-platforms.md)|Dokumentacja elementów składni udostępnionych przez C++/CX i C++/CLI.|
|[Aplikacje uniwersalne systemu Windows (C++)](../cppcx/universal-windows-apps-cpp.md)|Zapisuj aplikacje platformy UWP przy użyciu języka C++/CX lub biblioteki szablonów środowisko wykonawcze systemu Windows (WRL).|
|[Atrybuty języka C++ dla modelu COM i platformy .NET](attributes/cpp-attributes-com-net.md)|Atrybuty niestandardowe dla programowania wyłącznie dla systemu Windows przy użyciu platformy .NET lub modelu COM.|
