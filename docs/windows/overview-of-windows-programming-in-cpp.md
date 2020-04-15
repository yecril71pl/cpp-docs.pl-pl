---
title: Omówienie programowania w systemie Windows w języku C++
ms.date: 09/17/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 8ab7fbf7c955b1c828ef583aa639eda7409cf167
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359944"
---
# <a name="overview-of-windows-programming-in-c"></a>Omówienie programowania w systemie Windows w języku C++

Istnieje kilka szerokich kategorii aplikacji systemu Windows, które można utworzyć za pomocą języka C++. Każdy z nich ma swój własny model programowania i zestaw bibliotek specyficznych dla systemu Windows, ale biblioteki standardowe języka C++ i biblioteki C++ innych firm mogą być używane w dowolnym z nich.

W tej sekcji omówiono sposób tworzenia programów Windows za pomocą programu Visual Studio i bibliotek otoki MFC/ATL. Aby uzyskać dokumentację dotyczącą samej platformy Windows, zobacz [dokumentację systemu Windows](/windows/index).

## <a name="command-line-console-applications"></a>Aplikacje wiersza polecenia (konsoli)

Aplikacje konsoli języka C++ są uruchamiane z wiersza polecenia w oknie konsoli i mogą wyświetlać tylko dane wyjściowe tekstu. Aby uzyskać więcej informacji, zobacz [Tworzenie projektu aplikacji konsoli języka C++](../get-started/tutorial-console-cpp.md).

## <a name="native-desktop-client-applications"></a>Natywne aplikacje klienckie dla komputerów stacjonarn

*Natywna aplikacja kliencka pulpitu* jest C lub C++ okna aplikacji, która używa oryginalnych natywnych [interfejsów API systemu Windows C lub component Object Model (COM) interfejsów API,](/windows/win32/apiindex/windows-api-list) aby uzyskać dostęp do systemu operacyjnego. Te interfejsy API są napisane głównie w języku C. Istnieje więcej niż jeden sposób tworzenia natywnej aplikacji klasycznej: można programować bezpośrednio przy użyciu interfejsów API systemu Win32, używając pętli komunikatów w stylu C, która przetwarza zdarzenia systemu operacyjnego. Można też programować przy użyciu *microsoft foundation classes* (MFC), biblioteki C++ zorientowanej na obiekt, która otacza win32. Żadne z tych podejść nie jest uważane za "nowoczesne" w porównaniu do platformy uniwersalnej systemu Windows (UWP), ale oba są nadal w pełni obsługiwane i mają miliony linii kodu działających w dzisiejszym świecie. Aplikacja Win32, która działa w oknie wymaga dewelopera do jawnego pracy z komunikatami systemu Windows wewnątrz funkcji procedury systemu Windows. Pomimo nazwy, aplikacja Win32 może być skompilowana jako 32-bitowy (x86) lub 64-bitowy (x64) plik binarny. W środowiskach IDE programu Visual Studio terminy x86 i Win32 są synonimami.

Aby rozpocząć korzystanie z tradycyjnego programowania w systemie Windows C++, zobacz [Wprowadzenie do wersji Win32 i C++](/windows/win32/LearnWin32/learn-to-program-for-windows). Po uzyskaniu zrozumienia Win32, będzie łatwiej dowiedzieć się o [MFC Desktop Applications](../mfc/mfc-desktop-applications.md). Na przykład tradycyjnej aplikacji klasycznej C++, która używa zaawansowanej grafiki, zobacz [Hilo: Tworzenie aplikacji C++ dla systemu Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx).

### <a name="c-or-net"></a>C++ lub .NET?

Ogólnie rzecz biorąc programowanie .NET w języku C# jest mniej złożone, mniej podatne na błędy i ma bardziej nowoczesny interfejs API obiektowy niż Win32 lub MFC. W większości przypadków jego wydajność jest więcej niż odpowiednia. Program .NET zawiera program Windows Presentation Foundation (WPF) dla zaawansowanej grafiki i można korzystać zarówno z systemu Win32, jak i nowoczesnego interfejsu API środowiska wykonawczego systemu Windows. Zgodnie z ogólną zasadą zaleca się używanie języka C++ dla aplikacji klasycznych, gdy jest to wymagane:

- precyzyjna kontrola nad użyciem pamięci
- najwyższa ekonomia w zużyciu energii
- wykorzystanie GPU do przetwarzania ogólnego
- dostęp do DirectX
- intensywne korzystanie ze standardowych bibliotek języka C++

Możliwe jest również połączenie mocy i wydajności języka C++ z programowaniem .NET. Można utworzyć interfejs użytkownika w języku C# i użyć C++/CLI, aby umożliwić aplikacji korzystanie z natywnych bibliotek języka C++. Aby uzyskać więcej informacji, zobacz [.NET Programowanie z C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="com-components"></a>Komponenty COM

[Model obiektu komponentu (COM)](/windows/win32/com/the-component-object-model) to specyfikacja, która umożliwia programom napisanym w różnych językach komunikowanie się ze sobą. Wiele składników systemu Windows są implementowane jako obiekty COM i przestrzegać standardowych reguł COM do tworzenia obiektów, odnajdywania interfejsu i niszczenia obiektów.  Korzystanie z obiektów COM z aplikacji klasycznych C++ jest stosunkowo proste, ale pisanie własnego obiektu COM jest bardziej zaawansowane. [Biblioteka aktywnych szablonów (ATL)](../atl/atl-com-desktop-components.md) udostępnia makra i funkcje pomocnicze, które upraszczają programowanie com. Aby uzyskać więcej informacji, zobacz [składniki pulpitu ATL COM](../atl/atl-com-desktop-components.md).

## <a name="universal-windows-platform-apps"></a>Aplikacje platformy systemu Windows

Uniwersalna platforma systemu Windows (UWP) to nowoczesny interfejs API systemu Windows. Aplikacje platformy uniwersalnej systemu Windows działają na dowolnym urządzeniu z systemem Windows 10, używają języka XAML dla interfejsu użytkownika i są w pełni dotykowe. Aby uzyskać więcej informacji na temat platformy uniwersalnej systemu Windows, [Guide to Windows Universal Apps](/windows/uwp/get-started/universal-application-platform-guide)zobacz [Co to jest aplikacja uniwersalna platforma systemu Windows (UWP)?](/windows/uwp/get-started/whats-a-uwp)

Oryginalna obsługa języka C++ dla platformy uniwersalnej systemu Windows składała się z (1) języka C++/CX, dialektu języka C++ z rozszerzeniami składni lub (2) biblioteki wykonawczej systemu Windows (WRL), która jest oparta na standardowych językach C++ i COM. Nadal obsługiwane są zarówno C++/CX, jak i WRL. W przypadku nowych projektów zalecamy [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), który jest całkowicie oparty na standardowym języku C++ i zapewnia szybszą wydajność.

## <a name="desktop-bridge"></a>Mostek pulpitu

W systemie Windows 10 można spakować istniejącą aplikację klasyczną lub obiekt COM jako aplikację platformy uniwersalnej systemu Windows i dodać funkcje platformy uniwersalnej systemu Windows, takie jak dotyk, lub wywołać interfejsy API z nowoczesnego zestawu interfejsu API systemu Windows. Można również dodać aplikację platformy uniwersalnej systemu Windows do rozwiązania klasycznego w programie Visual Studio i spakować je razem w jednym pakiecie i używać interfejsów API systemu Windows do komunikowania się między nimi.

Program Visual Studio 2017 w wersji 15.4 i nowszych umożliwia utworzenie projektu pakietu aplikacji systemu Windows, aby znacznie uprościć pracę pakowania istniejącej aplikacji klasycznej. Kilka ograniczeń ma zastosowanie do wywołań rejestru lub interfejsów API, których może używać aplikacja komputerowa. Jednak w wielu przypadkach można utworzyć alternatywne ścieżki kodu, aby osiągnąć podobną funkcjonalność podczas uruchamiania w pakiecie aplikacji. Aby uzyskać więcej informacji, zobacz [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Gry

Gry DirectX można uruchamiać na komputerze PC lub Xbox. Aby uzyskać więcej informacji, zobacz [DirectX Graphics and Gaming](/windows/win32/directx).

## <a name="sql-server-database-clients"></a>Klienci bazy danych programu SQL Server

Aby uzyskać dostęp do baz danych programu SQL Server z kodu macierzystego, użyj odbc lub OLE DB. Aby uzyskać więcej informacji, zobacz [Klient macierzysty programu SQL Server](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Sterowniki urządzeń dla systemu Windows

Sterowniki są składnikami niskiego poziomu, które sprawiają, że dane z urządzeń sprzętowych są dostępne dla aplikacji i innych składników systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [Zestaw sterowników systemu Windows (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>Usługi systemu Windows

*Usługa* systemu Windows to program, który może działać w tle z niewielką lub żadną interakcją użytkownika. Programy te są nazywane *demonami* w systemach UNIX. Aby uzyskać więcej informacji, zobacz [Usługi](/windows/win32/services/services).

## <a name="sdks-libraries-and-header-files"></a>SDK, biblioteki i pliki nagłówkowe

Program Visual Studio zawiera bibliotekę środowiska wykonawczego języka C (CRT), standardową bibliotekę języka C++ i inne biblioteki specyficzne dla firmy Microsoft. Większość folderów zawierających pliki nagłówkowe dla tych bibliotek znajduje się w katalogu instalacyjnym programu Visual Studio w folderze \VC\. Pliki nagłówkowe systemu Windows i CRT znajdują się w folderze instalacyjnym zestawu Windows SDK.

[Menedżer pakietów Vcpkg](../build/vcpkg.md) umożliwia wygodne instalowanie setek bibliotek open source innych firm dla systemu Windows.

Biblioteki firmy Microsoft obejmują:

- Microsoft Foundation Classes (MFC): Zorientowana obiektowo platforma do tworzenia tradycyjnych programów systemu Windows — szczególnie aplikacji dla przedsiębiorstw — które cechuje bogaty interfejs użytkownika zawierający przyciski, pola listy, widoki drzewa i inne formanty. Aby uzyskać więcej informacji, zobacz [MFC Desktop Applications](../mfc/mfc-desktop-applications.md).

- Active Template Library (ATL): Zaawansowana biblioteka pomocnicza do tworzenia składników modelu COM. Aby uzyskać więcej informacji, zobacz [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).

- C++ Accelerated Massive Parallelism (C++ AMP): Biblioteka, która umożliwia wykonywanie wysokiej wydajności obliczeń ogólnego przeznaczenia na procesorach GPU. Aby uzyskać więcej informacji, zobacz [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Środowisko uruchomieniowe współbieżności: Biblioteka, która upraszcza pracę przy programowaniu współbieżnym i asynchronicznym dla urządzeń wielordzeniowych. Aby uzyskać więcej informacji, zobacz [Środowisko uruchomieniowe współbieżności](../parallel/concrt/concurrency-runtime.md).

Wiele scenariuszy programowania dla systemu Windows wymaga również Windows SDK, które zawiera pliki nagłówkowe umożliwiające dostęp do składników systemu operacyjnego Windows. Domyślnie program Visual Studio instaluje zestaw Windows SDK jako składnik obciążenia pulpitu W++, co umożliwia tworzenie uniwersalnych aplikacji systemu Windows. Do tworzenia aplikacji platformy uniwersalnej systemu Windows potrzebna jest wersja SDK systemu Windows dla systemu Windows dla systemu Windows 10. Aby uzyskać więcej informacji, zobacz [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk). (Aby uzyskać więcej informacji na temat windows SDK dla wcześniejszych wersji systemu Windows, zobacz [archiwum Windows SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**Programy Pliki (x86)\Zestawy windows to** domyślna lokalizacja dla wszystkich zainstalowanych wersji zestawu Windows SDK.

Inne platformy, takie jak Xbox i Azure, mają swoje własne zestawy SDK, które również można zainstalować. Aby uzyskać więcej informacji, zobacz Centrum deweloperów DirectX i Centrum deweloperów Azure.

## <a name="development-tools"></a>Narzędzia programistyczne

Środowisko Visual Studio zawiera zaawansowany debuger kodu natywnego, narzędzia do analizy statycznej, graficzne narzędzia do debugowania, profesjonalny edytor kodu, wsparcie dla testów jednostkowych i wiele innych narzędzi. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do tworzenia za pomocą programu Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)i [Omówienie programowania języka C++ w programie Visual Studio](../overview/overview-of-cpp-development.md).

## <a name="in-this-section"></a>W tej sekcji

|Tytuł|Opis|
|-----------|-----------------|
|[Przewodnik: Tworzenie standardowego programu Języka C++](walkthrough-creating-a-standard-cpp-program-cpp.md)| Tworzenie aplikacji konsoli systemu Windows.|
|[Przewodnik: tworzenie aplikacji klasycznych systemu Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Utwórz natywną aplikację klasyczną systemu Windows.|
|[Kreator pulpitu systemu Windows](windows-desktop-wizard.md)|Użyj kreatora, aby utworzyć nowe projekty systemu Windows.|
|[Biblioteka aktywnych szablonów (Active Template Library — ATL)](../atl/atl-com-desktop-components.md)|Użyj biblioteki ATL, aby utworzyć składniki COM w języku C++.|
|[Microsoft Foundation Classes (MFC)](../mfc/mfc-desktop-applications.md)|Tworzenie dużych lub małych aplikacji systemu Windows za pomocą okien dialogowych i kontrolek za pomocą mfc|
|[Wspólne klasy ATL i MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)|Użyj klas, takich jak CString, które są współużytkowane w ATL i MFC.|
|[Dostęp do danych](../data/data-access-in-cpp.md)| OLE DB i ODBC|
|[Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)|Różne typy ciągów w systemie Windows.|
|[Zasoby służące do tworzenia gier za pomocą programu DirectX](resources-for-creating-a-game-using-directx.md)
|[Instrukcje: używanie zestawu SDK systemu Windows 10 w aplikacji klasycznej systemu Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Zestaw SDK systemu Windows|
|[Praca z plikami zasobów](working-with-resource-files.md)|Jak dodać obrazy, ikony, tabele ciągów i inne zasoby do aplikacji klasycznej.|
|[Zasoby do tworzenia gry za pomocą directx (C++)](resources-for-creating-a-game-using-directx.md)|Linki do zawartości do tworzenia gier w języku C++.|
|[Instrukcje: używanie zestawu SDK systemu Windows 10 w aplikacji klasycznej systemu Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Zawiera kroki konfigurowania projektu do tworzenia przy użyciu systemu Windows 10 SDK.|
|[Wdrażanie natywnych aplikacji klasycznych](deploying-native-desktop-applications-visual-cpp.md)|Wdrażanie aplikacji natywnych w systemie Windows.|

## <a name="related-articles"></a>Powiązane artykuły

|Tytuł|Opis|
|-----------|-----------------|
|[C++ w programie Visual Studio](../overview/visual-cpp-in-visual-studio.md)|Temat nadrzędny dla zawartości dewelopera języka Visual C++.|
[Programowanie na platformie .NET w języku C++/w interfejsie wiersza polecenia](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Utwórz otoki dla natywnych bibliotek języka C++, które umożliwiają komunikację z aplikacjami i składnikami platformy .NET.|
|[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](../extensions/component-extensions-for-runtime-platforms.md)|Odwołanie do elementów składni współużytkowane przez C++/CX i C++/CLI.|
|[Aplikacje uniwersalne systemu Windows (C++)](../cppcx/universal-windows-apps-cpp.md)|Pisanie aplikacji platformy uniwersalnej systemu Windows przy użyciu biblioteki szablonów środowiska wykonawczego systemu Windows (WRL) języka C++/CX lub programu Windows.|
|[Atrybuty języka C++ dla modelu COM i platformy .NET](attributes/cpp-attributes-com-net.md)|Niestandardowe atrybuty programowania tylko dla systemu Windows przy użyciu platformy .NET lub COM.|
