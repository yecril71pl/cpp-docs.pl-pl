---
title: Omówienie programowania w systemie Windows w języku C++
ms.date: 11/15/2018
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 6338b390b11c58f3ebac2af1bb568ea3c3470cd1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810448"
---
# <a name="overview-of-windows-programming-in-c"></a>Omówienie programowania w systemie Windows w języku C++

Istnieje kilka szerokie kategorie aplikacji Windows, które można utworzyć przy użyciu języka C++. Każda ma swój własny model programowania oraz zestaw biblioteki charakterystyczne dla Windows, ale standardowej biblioteki języka C++, jak również innych bibliotek C++, które mogą być używane w żadnej z nich. 

## <a name="command-line-console-applications"></a>Aplikacje wiersza polecenia (Konsola)

Aplikacji konsoli w języku C++ uruchomić z wiersza polecenia w oknie konsoli i wyświetlić tekst wyjściowy. Aby uzyskać więcej informacji, zobacz [aplikacji konsoli](console-applications-in-visual-cpp.md).
 
## <a name="native-desktop-client-applications"></a>Natywne pulpitu aplikacje klienckie

Termin *aplikacji macierzystych klienta stacjonarnego* odwołuje się do języka C lub C++ okna aplikacji, która używa oryginalnych interfejsów API systemu Win32 Windows dostęp do tego systemu operacyjnego. Te interfejsy API są same napisany głównie w C. Podczas tworzenia tego rodzaju aplikacji, masz do wyboru, programowanie bezpośrednio w odniesieniu do pętli komunikatów stylu C, która przetwarza zdarzenia systemu operacyjnego lub przy użyciu *Microsoft Foundation Classes* (MFC), biblioteka języka C++, który otacza Win32 w sposób, który jest nieco zorientowane obiektowo. Nie jest uznawany za "nowoczesnych typów" w porównaniu do uniwersalnej platformy Windows (patrz poniżej), ale obie są nadal obsługiwane całkowicie i dysponują milionami wierszy kodu uruchamianego w świecie już dziś.

Aby rozpocząć pracę z tradycyjnego programowania C++ Windows, zobacz [wprowadzenie Win32 i C++](/windows/desktop/LearnWin32/learn-to-program-for-windows). Po uzyskaniu niektóre wiedzę na temat Win32, będzie można łatwiej Dowiedz się więcej o [aplikacji pulpitu MFC](/mfc/mfc-desktop-applications). Na przykład tradycyjnych C++ aplikacja komputerowa, która korzysta z zaawansowanych grafiki zobacz [Hilo: Projektowanie aplikacji C++ dla Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx).

### <a name="c-or-net"></a>C++ lub .NET? 

Scenariusze aplikacji najbardziej pulpitu (innymi słowy, nie określania wartości docelowej platformy uniwersalnej systemu Windows), rozważ użycie C# i .NET. Jest to spowodowane programowania .NET jest zazwyczaj mniej skomplikowany, mniej podatne na błędy i ma bardziej nowoczesnego API zorientowane obiektowo niż MFC lub Win32. W większości przypadków jego wydajność jest większe niż odpowiednie. Windows Presentation Foundation (WPF) do grafiki zaawansowanych usług .NET features i będzie można korzystać, Win32, a także Windows nowoczesnego interfejsu API środowiska uruchomieniowego (zobacz poniżej platformy uniwersalnej systemu Windows). Zgodnie z ogólną zasadą zaleca się przy użyciu języka C++ dla aplikacji klasycznych, gdy potrzebujesz:

- precyzyjną kontrolę nad tym użycie pamięci
- priorytetowe gospodarki zużycie energii
- użycie procesora GPU do ogólnego przetwarzania danych
- dostęp do technologii DirectX
- duże użycie standardowych bibliotek języka C++

## <a name="com-components"></a>Składniki COM

Wiele części systemu operacyjnego Windows są oparte na Component Object Model (COM) definiujący binarne standardu, który włącza składnik do użycia z aplikacje klienckie pisane w dowolnym języku komputera. W języku C++ można użyć Active Template Library (ATL), można uproszczenie pracy tworzenia składników modelu COM. Aby uzyskać więcej informacji, zobacz [Component Object Model (COM)](/windows/desktop/com/component-object-model--com--portal) i [ATL COM pulpitu składniki](../atl/atl-com-desktop-components.md).

## <a name="windows-universal-apps"></a>Windows Universal Apps

Platforma Universal Windows (UWP) jest nowoczesnego interfejsu Windows API. Aplikacje platformy uniwersalnej systemu Windows uruchamianie na dowolnym urządzeniu z systemem Windows 10, użyj XAML dla interfejsu użytkownika i są w pełni dotykowej. Aby uzyskać więcej informacji na temat platformy uniwersalnej systemu Windows, zobacz [co to jest aplikacja Windows platformy Uniwersalnej?](/windows/uwp/get-started/whats-a-uwp) i [Przewodnik po aplikacjach uniwersalnych Windows](/windows/uwp/get-started/universal-application-platform-guide).

Oryginalny Obsługa języka C++ platformy uniwersalnej systemu Windows składa się z (1) C + +/ CX, dialekt języka C++, za pomocą składni rozszerzenia lub (2 Windows Runtime Library (WRL) opartym na standard C++ i modelu COM. Zarówno C + +/ CX i WRL są nadal obsługiwane. Dla nowych projektów zaleca się [C + +/ WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) który całkowicie zależy od standardowego języka C++ i zapewnia lepszą wydajność. 

W systemie Windows 10 można spakować istniejących aplikacji klasycznych języka C++ jako — dotyczy wdrożenia przez Microsoft Store. Aby uzyskać więcej informacji, zobacz [pakietu aplikacji komputerowych (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Gry

Gry DirectX można uruchomić na komputerach PC lub konsoli Xbox. Aby uzyskać więcej informacji, zobacz [DirectX Graphics i gry](/windows/desktop/directx).

## <a name="net-wrappers-for-c-libraries"></a>.NET otoki biblioteki języka C++

Można użyć C + +/ interfejsu wiersza polecenia, aby utworzyć warstwa międzyoperacyjności, umożliwiająca kodu platformy .NET korzystać z natywnych bibliotek C++. Aby uzyskać więcej informacji, zobacz [programowania .NET w języku C + +/ CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="sql-server-database-clients"></a>Klienty baz danych programu SQL Server

Dostęp do bazy danych programu SQL Server z kodu natywnego, użyj ODBC lub OLE DB. Aby uzyskać więcej informacji, zobacz [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Sterowniki urządzeń dla systemu Windows

Sterowniki są składniki niskiego poziomu, które udostępnić dane z urządzeń sprzętowych dla aplikacji i inne składniki systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [Windows Driver Kit (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>usługi systemu Windows

Windows *usługi* to program, który można uruchomić w tle mało lub nie interwencji użytkownika. W systemie UNIX nazywa się *demonów*. Aby uzyskać więcej informacji, zobacz [usług](/windows/desktop/services/services).

## <a name="sdks-libraries-and-header-files"></a>Zestawy SDK, biblioteki i pliki nagłówkowe

Visual Studio zawiera bibliotekę środowiska uruchomieniowego C (CRT), standardowej biblioteki języka C++ i inne biblioteki charakterystyczne dla Microsoft. Uwzględnianie folderów, które zawierają pliki nagłówkowe dla tych bibliotek znajdują się w katalogu instalacyjnym Visual Studio, w folderze \VC\ lub w przypadku CRT, w folderze instalacji zestawu Windows SDK.

Możesz użyć [Menedżera pakietów Vcpkg](../vcpkg.md) wygodny sposób instalowania kilkuset bibliotek typu open-source innych firm dla Windows.

Biblioteki firmy Microsoft obejmują:

- Microsoft Foundation Classes (MFC) Zorientowana obiektowo platforma do tworzenia tradycyjnych programów Windows — szczególnie aplikacji dla przedsiębiorstw — które cechuje bogaty interfejs użytkownika zawierający przyciski, pola listy, widoki drzewa i inne kontrolki. Aby uzyskać więcej informacji, zobacz [aplikacji pulpitu MFC](../mfc/mfc-desktop-applications.md).

- Biblioteka Active Template Library (ATL): Zaawansowana Biblioteka pomocnicza do tworzenia składników COM. Aby uzyskać więcej informacji, zobacz [ATL COM pulpitu składniki](../atl/atl-com-desktop-components.md).

- C++ AMP (C++ Accelerated Massive Parallelism): Biblioteka, która umożliwia ogólne pracę obliczeniową o wysokiej wydajności na procesorze GPU. Aby uzyskać więcej informacji, zobacz [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Środowisko uruchomieniowe współbieżności: Biblioteka, która upraszcza pracę Programowanie równoległe i asynchroniczne dla urządzeń wielordzeniowych i wielordzeniowych. Aby uzyskać więcej informacji, zobacz [współbieżność środowiska wykonawczego](../parallel/concrt/concurrency-runtime.md).

Wiele scenariuszy programowania dla systemu Windows wymaga również Windows SDK, które zawiera pliki nagłówkowe umożliwiające dostęp do składników systemu operacyjnego Windows. Domyślnie program Visual Studio instaluje zestaw Windows SDK jako część obciążenia pulpitu C++ umożliwia tworzenie aplikacji Windows Universal apps. Do tworzenia aplikacji platformy uniwersalnej systemu Windows, należy do zestawu Windows SDK w wersji systemu Windows 10. Aby uzyskać informacje, zobacz [zestawu Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk). (Aby uzyskać więcej informacji na temat zestawów Windows SDK dla wcześniejszych wersji systemu Windows, zobacz [archiwum zestaw Windows SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**Program \Windows pliki (x86) zestawy** jest domyślną lokalizacją dla wszystkich wersji zestawu Windows SDK, który został zainstalowany.

Inne platformy, takie jak Xbox i Azure, mają swoje własne zestawy SDK, które również można zainstalować. Aby uzyskać więcej informacji, zobacz Centrum deweloperów DirectX i Centrum deweloperów Azure.

## <a name="development-tools"></a>Narzędzia programistyczne

Środowisko Visual Studio zawiera zaawansowany debuger kodu natywnego, narzędzia do analizy statycznej, graficzne narzędzia do debugowania, profesjonalny edytor kodu, wsparcie dla testów jednostkowych i wiele innych narzędzi. Aby uzyskać więcej informacji, zobacz [Rozpocznij tworzenie aplikacji za pomocą programu Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio), i [programowanie omówienie języka C++ w Visual Studio](../overview-of-cpp-development.md).

## <a name="in-this-section"></a>W tej sekcji
|Tytuł|Opis|
|-----------|-----------------|
|[Aplikacje klasyczne systemu Windows w języku C++](desktop-applications-visual-cpp.md)| Jak utworzyć tradycyjne aplikacje komputerowe.|
|[Biblioteka aktywnych szablonów (Active Template Library — ATL)](../atl/TOC.md)|Biblioteka ATL służy do tworzenia składników modelu COM w języku C++.|
|[Microsoft Foundation Classes (MFC)](../mfc/TOC.md)|Używać klasy MFC do tworzenia aplikacji Windows duże lub małe za pomocą okien dialogowych i formantów|
|[Wspólne klasy ATL i MFC](../atl-mfc-shared/TOC.md)|Użyj klas, takich jak CString, które są udostępniane w ATL i MFC.|
|[Programowanie na platformie .NET w języku C++/w interfejsie wiersza polecenia](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Tworzenie otok dla natywnych bibliotek C++, które umożliwiają go do komunikacji z aplikacji platformy .NET i składników.|
|[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)|Dokumentacja dotycząca elementy składni udostępniane przez C + +/ CX i C + +/ interfejsu wiersza polecenia.|
|[Aplikacje uniwersalne systemu Windows (C++)](universal-windows-apps-cpp.md)|Tworzenie aplikacji platformy uniwersalnej systemu Windows za pomocą C + +/ CX lub Windows Runtime szablon biblioteki (WRL).|
|[Atrybuty języka C++ dla modelu COM i platformy .NET](attributes/cpp-attributes-com-net.md)|Niestandardowe atrybuty tylko do Windows programowania przy użyciu platformy .NET lub model COM.|

## <a name="related-articles"></a>Powiązane artykuły

|Tytuł|Opis|
|-----------|-----------------|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Temat nadrzędny dla zawartości dla deweloperów Visual C++.|
