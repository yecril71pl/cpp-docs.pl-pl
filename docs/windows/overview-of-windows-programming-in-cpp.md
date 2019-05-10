---
title: Omówienie programowania w systemie Windows w języku C++
ms.date: 05/06/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 40028794a6df30db619965181f2e31d7c9a2745c
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221322"
---
# <a name="overview-of-windows-programming-in-c"></a>Omówienie programowania w systemie Windows w języku C++

Istnieje kilka szerokie kategorie aplikacji Windows, które można utworzyć przy użyciu języka C++. Każda ma swój własny model programowania oraz zestaw biblioteki charakterystyczne dla Windows, ale standardowej biblioteki języka C++, jak również innych bibliotek C++, które mogą być używane w żadnej z nich. 

## <a name="command-line-console-applications"></a>Aplikacje wiersza polecenia (Konsola)

Aplikacji konsoli w języku C++ uruchomić z wiersza polecenia w oknie konsoli i wyświetlić tekst wyjściowy. Aby uzyskać więcej informacji, zobacz [aplikacji konsoli](console-applications-in-visual-cpp.md).
 
## <a name="native-desktop-client-applications"></a>Natywne pulpitu aplikacje klienckie

Termin *aplikacji macierzystych klienta stacjonarnego* odwołuje się do C lub C++ okna aplikacji, która używa oryginalnej native [interfejsów API języka C Windows i/lub interfejsów API modelu COM](/windows/desktop/apiindex/windows-api-list) dostęp do tego systemu operacyjnego. Te interfejsy API są same napisany głównie w C. Podczas tworzenia tego rodzaju aplikacji, masz do wyboru, programowanie bezpośrednio w odniesieniu do pętli komunikatów stylu C, która przetwarza zdarzenia systemu operacyjnego lub przy użyciu *Microsoft Foundation Classes* (MFC), biblioteka języka C++, który otacza Win32 w sposób, który jest nieco zorientowane obiektowo. Nie jest uznawany za "nowoczesnych typów" w porównaniu do uniwersalnej platformy Windows (patrz poniżej), ale obie są nadal obsługiwane całkowicie i dysponują milionami wierszy kodu uruchamianego w świecie już dziś. Aplikacja Win32, który działa w oknie wymaga deweloperowi jawnie pracować Windows komunikaty wewnątrz funkcji procedury Windows. Niezależnie od nazwy jest aplikacją systemu Win32 może być kompilowane jako (x86) 32-bitowy lub 64-bitowych (x64) binarny. W programie Visual Studio IDE to samo warunków x86 i Win32.

Aby rozpocząć pracę z tradycyjnego programowania C++ Windows, zobacz [wprowadzenie Win32 i C++](/windows/desktop/LearnWin32/learn-to-program-for-windows). Po uzyskaniu niektóre wiedzę na temat Win32, będzie można łatwiej Dowiedz się więcej o [aplikacji pulpitu MFC](../mfc/mfc-desktop-applications.md). Na przykład tradycyjnych C++ aplikacja komputerowa, która korzysta z zaawansowanych grafiki zobacz [Hilo: Projektowanie aplikacji C++ dla Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx).

### <a name="c-or-net"></a>C++ lub .NET? 

Scenariusze aplikacji najbardziej pulpitu (innymi słowy, nie określania wartości docelowej platformy uniwersalnej systemu Windows), rozważ użycie C# do tworzenia interfejsu użytkownika. Jest to spowodowane programowania .NET jest zazwyczaj mniej skomplikowany, mniej podatne na błędy i ma bardziej nowoczesnego API zorientowane obiektowo niż MFC lub Win32. W większości przypadków jego wydajność jest większe niż odpowiednie. Windows Presentation Foundation (WPF) do grafiki zaawansowanych usług .NET features i będzie można korzystać, Win32, a także Windows nowoczesnego interfejsu API środowiska uruchomieniowego (zobacz poniżej platformy uniwersalnej systemu Windows). Zgodnie z ogólną zasadą zaleca się przy użyciu języka C++ dla aplikacji klasycznych, gdy potrzebujesz:

- precyzyjną kontrolę nad tym użycie pamięci
- priorytetowe gospodarki zużycie energii
- użycie procesora GPU do ogólnego przetwarzania danych
- dostęp do technologii DirectX
- duże użycie standardowych bibliotek języka C++

Można utworzyć interfejs użytkownika w C# i użyj C++sposób niezamierzony umożliwia aplikacji korzystanie z natywnych C++ bibliotek. Aby uzyskać więcej informacji, zobacz [.NET, programowanie za pomocą C++sposób niezamierzony](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="com-components"></a>Składniki COM

[Component Object Model (COM)](/windows/desktop/com/the-component-object-model) jest specyfikacja, która umożliwia programom napisane w różnych językach, aby komunikować się ze sobą. Windows wiele składników są implementowane jako obiekty COM i postępuj zgodnie z standardowe zasady modelu COM do tworzenia obiektów interfejsu zniszczenie odnajdywania i obiektu.  Obiekty COM z aplikacji klasycznych w języku C++ jest stosunkowo prosta, ale zapisywania obiektu COM jest bardziej zaawansowane. [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) zawiera makra i funkcje pomocnicze, które upraszczają programowanie COM. Aby uzyskać więcej informacji, zobacz [ATL COM pulpitu składniki](../atl/atl-com-desktop-components.md).

## <a name="windows-universal-apps"></a>Windows Universal Apps

Platforma Universal Windows (UWP) jest nowoczesnego interfejsu Windows API. Aplikacje platformy uniwersalnej systemu Windows uruchamianie na dowolnym urządzeniu z systemem Windows 10, użyj XAML dla interfejsu użytkownika i są w pełni dotykowej. Aby uzyskać więcej informacji na temat platformy uniwersalnej systemu Windows, zobacz [co to jest aplikacja Windows platformy Uniwersalnej?](/windows/uwp/get-started/whats-a-uwp) i [Przewodnik po aplikacjach uniwersalnych Windows](/windows/uwp/get-started/universal-application-platform-guide).

Oryginalny C++ pomoc techniczna dla platformy uniwersalnej systemu Windows składa się (1) C++/CX, dialekt C++ za pomocą składni rozszerzenia lub (2 Windows Runtime Library (WRL), który jest oparty na standardzie C++ i modelu COM. Zarówno C++/CX i WRL są nadal obsługiwane. Dla nowych projektów zaleca się [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) która jest całkowicie oparty na standardzie C++ oraz zapewnia lepszą wydajność. 

## <a name="desktop-bridge"></a>Desktop Bridge

W systemie Windows 10 można pakietu istniejących aplikacji pulpitu lub obiektu COM jako aplikację platformy uniwersalnej systemu Windows i Dodaj funkcje platformy uniwersalnej systemu Windows, takie jak touch lub wywoływać interfejsy API z nowoczesnych zestawu Windows API. Aplikacja platformy uniwersalnej systemu Windows można również dodać do pulpitu rozwiązania w programie Visual Studio i pakiet je razem w jednym pakietu i komunikować się między nimi za pomocą interfejsów API Windows.

W Visual Studio 2017 w wersji 15.4 lub nowszy można utworzyć projekt pakietu aplikacji Windows, do znacznego uproszczenia pracy pakowania swoją istniejącą aplikację pulpitu. Kilka ograniczenia mają zastosowanie w odniesieniu do rejestru, które wywołuje lub korzysta z interfejsów API aplikacji pulpitu, ale w wielu przypadkach można utworzyć ścieżki alternatywnej kodu do osiągnięcia podobne funkcje podczas uruchamiania w pakiecie aplikacji. Aby uzyskać więcej informacji, zobacz [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Gry

Gry DirectX można uruchomić na komputerach PC lub konsoli Xbox. Aby uzyskać więcej informacji, zobacz [DirectX Graphics i gry](/windows/desktop/directx).

## <a name="sql-server-database-clients"></a>Klienty baz danych programu SQL Server

Dostęp do bazy danych programu SQL Server z kodu natywnego, użyj ODBC lub OLE DB. Aby uzyskać więcej informacji, zobacz [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Sterowniki urządzeń dla systemu Windows

Sterowniki są składniki niskiego poziomu, które udostępnić dane z urządzeń sprzętowych dla aplikacji i inne składniki systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [Windows Driver Kit (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>usługi systemu Windows

Windows *usługi* to program, który można uruchomić w tle mało lub nie interwencji użytkownika. W systemie UNIX nazywa się *demonów*. Aby uzyskać więcej informacji, zobacz [usług](/windows/desktop/services/services).

## <a name="sdks-libraries-and-header-files"></a>Zestawy SDK, biblioteki i pliki nagłówkowe

Visual Studio zawiera bibliotekę środowiska uruchomieniowego C (CRT), standardowej biblioteki języka C++ i inne biblioteki charakterystyczne dla Microsoft. Uwzględnianie folderów, które zawierają pliki nagłówkowe dla tych bibliotek znajdują się w katalogu instalacyjnym Visual Studio, w folderze \VC\ lub w przypadku CRT, w folderze instalacji zestawu Windows SDK.

Możesz użyć [Menedżera pakietów Vcpkg](../build/vcpkg.md) wygodny sposób instalowania kilkuset bibliotek typu open-source innych firm dla Windows.

Biblioteki firmy Microsoft obejmują:

- Microsoft Foundation Classes (MFC) Zorientowana obiektowo platforma do tworzenia tradycyjnych programów Windows — szczególnie aplikacji dla przedsiębiorstw — które cechuje bogaty interfejs użytkownika zawierający przyciski, pola listy, widoki drzewa i inne kontrolki. Aby uzyskać więcej informacji, zobacz [aplikacji pulpitu MFC](../mfc/mfc-desktop-applications.md).

- Biblioteka Active Template Library (ATL): Zaawansowana Biblioteka pomocnicza do tworzenia składników COM. Aby uzyskać więcej informacji, zobacz [ATL COM pulpitu składniki](../atl/atl-com-desktop-components.md).

- C++ AMP (C++ Accelerated Massive Parallelism): Biblioteka, która umożliwia ogólne pracę obliczeniową o wysokiej wydajności na procesorze GPU. Aby uzyskać więcej informacji, zobacz [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Środowisko uruchomieniowe współbieżności: Biblioteka, która upraszcza pracę Programowanie równoległe i asynchroniczne dla urządzeń wielordzeniowych i wielordzeniowych. Aby uzyskać więcej informacji, zobacz [współbieżność środowiska wykonawczego](../parallel/concrt/concurrency-runtime.md).

Wiele scenariuszy programowania dla systemu Windows wymaga również Windows SDK, które zawiera pliki nagłówkowe umożliwiające dostęp do składników systemu operacyjnego Windows. Domyślnie program Visual Studio instaluje zestaw Windows SDK jako część obciążenia pulpitu C++ umożliwia tworzenie aplikacji Windows Universal apps. Do tworzenia aplikacji platformy uniwersalnej systemu Windows, należy do zestawu Windows SDK w wersji systemu Windows 10. Aby uzyskać informacje, zobacz [zestawu Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk). (Aby uzyskać więcej informacji na temat zestawów Windows SDK dla wcześniejszych wersji systemu Windows, zobacz [archiwum zestaw Windows SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**Program \Windows pliki (x86) zestawy** jest domyślną lokalizacją dla wszystkich wersji zestawu Windows SDK, który został zainstalowany.

Inne platformy, takie jak Xbox i Azure, mają swoje własne zestawy SDK, które również można zainstalować. Aby uzyskać więcej informacji, zobacz Centrum deweloperów DirectX i Centrum deweloperów Azure.

## <a name="development-tools"></a>Narzędzia programistyczne

Środowisko Visual Studio zawiera zaawansowany debuger kodu natywnego, narzędzia do analizy statycznej, graficzne narzędzia do debugowania, profesjonalny edytor kodu, wsparcie dla testów jednostkowych i wiele innych narzędzi. Aby uzyskać więcej informacji, zobacz [Rozpocznij tworzenie aplikacji za pomocą programu Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio), i [programowanie omówienie języka C++ w Visual Studio](../overview/overview-of-cpp-development.md).

## <a name="in-this-section"></a>W tej sekcji
|Tytuł|Opis|
|-----------|-----------------|
|[Przewodnik: tworzenie standardowego programu C++](walkthrough-creating-a-standard-cpp-program-cpp.md)| Utwórz aplikację konsolową Windows.|
|[Przewodnik: tworzenie aplikacji klasycznych systemu Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Utwórz prostą aplikację pulpitu Windows.|
|[Kreator aplikacji klasycznej systemu Windows](windows-desktop-wizard.md)|Użyj kreatora, aby tworzyć nowe projekty Windows.|
|[Biblioteka aktywnych szablonów (Active Template Library — ATL)](../atl/TOC.md)|Biblioteka ATL służy do tworzenia składników modelu COM w języku C++.|
|[Microsoft Foundation Classes (MFC)](../mfc/TOC.md)|Używać klasy MFC do tworzenia aplikacji Windows duże lub małe za pomocą okien dialogowych i formantów|
|[Wspólne klasy ATL i MFC](../atl-mfc-shared/TOC.md)|Użyj klas, takich jak CString, które są udostępniane w ATL i MFC.|
|[Dostęp do danych](../data/data-access-in-cpp.md)| OLE DB i ODBC|
|[Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)|Różne typy parametrów na Windows.|
|[Zasoby służące do tworzenia gier za pomocą programu DirectX](resources-for-creating-a-game-using-directx.md)
|[Instrukcje: używanie zestawu SDK systemu Windows 10 w aplikacji klasycznej systemu Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[Praca z plikami zasobów](working-with-resource-files.md)|Jak dodać obrazy, ikony, tabele ciągów i innych zasobów do aplikacji klasycznej.|
|[Zasoby służące do tworzenia gier za pomocą programu DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Zawiera łącza do zawartości do tworzenia gier w języku C++.|
|[Instrukcje: używanie zestawu SDK systemu Windows 10 w aplikacji klasycznej systemu Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Zawiera instrukcje dotyczące konfigurowania projektu kompilować przy użyciu zestawu SDK systemu Windows 10.|
|[Wdrażanie natywnych aplikacji klasycznych](deploying-native-desktop-applications-visual-cpp.md)|Wdrażanie aplikacji natywnych na Windows.|


## <a name="related-articles"></a>Powiązane artykuły

|Tytuł|Opis|
|-----------|-----------------|
|[Visual C++](../overview/visual-cpp-in-visual-studio.md)|Temat nadrzędny dla zawartości dla deweloperów Visual C++.|
[Programowanie na platformie .NET w języku C++/w interfejsie wiersza polecenia](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Tworzenie otok dla natywnych bibliotek C++, które umożliwiają go do komunikacji z aplikacji platformy .NET i składników.|
|[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](../extensions/component-extensions-for-runtime-platforms.md)|Dokumentacja dotycząca elementy składni współużytkowane przez C++/CX i C++sposób niezamierzony.|
|[Aplikacje uniwersalne systemu Windows (C++)](universal-windows-apps-cpp.md)|Tworzenie aplikacji platformy uniwersalnej systemu Windows przy użyciu C++/CX lub Windows Runtime szablon biblioteki (WRL).|
|[Atrybuty języka C++ dla modelu COM i platformy .NET](attributes/cpp-attributes-com-net.md)|Niestandardowe atrybuty tylko do Windows programowania przy użyciu platformy .NET lub model COM.|

