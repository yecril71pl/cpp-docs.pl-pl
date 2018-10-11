---
title: Omówienie programowania Windows w języku C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b2870aa742806671e39728c3b73604dcf4e810e9
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083089"
---
# <a name="overview-of-windows-programming-in-c"></a>Omówienie programowania w systemie Windows w języku C++

Visual C++ można użyć do zapisywania wielu rodzajów programów korzystających z komputera z systemem Windows (x 86, x64 lub ARM) na serwerze Windows w chmurze lub na konsoli Xbox. Dobrze napisane programy ++ mają następujące cechy:
- efektywne w wymagania dotyczące pamięci
- oszczędne w zużyciu energii 
- możliwość umożliwiają pełne wykorzystywanie zalet urządzeń wielordzeniowych i wielordzeniowe
- możliwość wykonywania obliczeń ogólnego na jednostka przetwarzania grafiki (urządzenia GPGPU)  
- można skorzystać z innych najnowsze funkcje w sprzętu.

Istnieje kilka szerokie kategorie aplikacji Windows, które można tworzyć przy użyciu języka Visual C++. Kategorie te mają różne modele programowania i modeli aplikacji, które zostały wprowadzone przez lata. Poszczególne modele używają różnych bibliotek i interfejsów API zapewniają dostęp do platformy i twórz interfejsy użytkownika, takich jak windows i oknach dialogowych. Standardowej biblioteki języka C++, a także bibliotek innych firm może służyć w dowolnym z tych kategorii, z kilkoma ograniczeniami dla platformy uniwersalnej systemu Windows.

- [Windows Universal apps](#BK_WindowsUniversal). Trzecia kategoria aplikacje Windows wprowadzono w systemie Windows 8 i pomocy technicznej dla tej kategorii aplikacji odbywa się w systemie Windows 10. Te aplikacje są często określane jako "Windows aplikacje" i obejmują one aplikacje komputerowe i mobilne, przeznaczonych dla różnych urządzeń. Te aplikacje można napisać w języku C + +/ CX, dialekt języka C++, która obejmuje obsługę dla rozwoju Windows Runtime lub w standardzie języka C++ z modelem COM za pomocą biblioteki środowiska uruchomieniowego Windows (WRL). Te aplikacje zostały pierwotnie zaprojektowany do uruchamiania na pełnym ekranie, mimo że w systemie Windows 10 użytkownicy mają możliwość uruchamiania ich w oknie pulpitu. Aplikacje te są zorientowanych na dotyk, ale można łatwo działać, jeśli użytkownicy preferują lub po ekranie dotykowym nie jest dostępny za pomocą myszy. Te aplikacje są dystrybuowane za pomocą usługi Microsoft Store, co prowadziło do ich wywoływana aplikacji "Store".

Aplikacje platformy uniwersalnej systemu Windows będą mogli uruchamiać na wszystkich urządzeniach z systemem Windows 10, takich jak tablety i telefony komórkowe, a także na pulpicie. Na komputerze stacjonarnym, są one mogą być uruchamiane jako okien pulpitu, zamiast zawsze uruchomiona w trybie pełnoekranowym. Te aplikacje można również uruchomić na konsoli Xbox i na urządzeniach w przyszłości.  Aplikacje platformy uniwersalnej systemu Windows są uruchamiane od środowiska uruchomieniowego Windows, który zawiera elementy interfejsu użytkownika, usługami i interfejs do różnych urządzeń, które są obsługiwane w programie Windows.

Można napisać aplikacji platformy UWP w języku C + +/ CX, dialekt języka c++, można użyć [C + +/ biblioteki WinRT](https://moderncpp.com/)w niektórych scenariuszach. Aplikacje platformy uniwersalnej systemu Windows skompiluj do kodu natywnego i ma interfejsu użytkownika XAML lub używają DirectX. Składniki środowiska wykonawczego Windows, które są zapisywane w kodzie natywnym, że można korzystać z aplikacji platformy uniwersalnej systemu Windows napisanych w innych językach. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji platformy uniwersalnej Windows w języku C++](http://go.microsoft.com/fwlink/?LinkID=534976), [tworzenie pierwszej gry platformy uniwersalnej systemu Windows za pomocą programu DirectX](http://go.microsoft.com/fwlink/p/?LinkId=244656), i [składniki tworzenia środowiska wykonawczego Windows w języku C++](http://go.microsoft.com/fwlink/p/?LinkId=244658).

   Ta kategoria zawiera również podstawowe składniki i obliczeniową kod w kontekście serwera i programowania w chmurze przy użyciu języka C++. Czasami kod intensywnie w samym sercu serwera lub aplikacji w chmurze są zapisywane w języku C++ w celu zmaksymalizowania wydajności. Można skompilować takiego kodu do biblioteki DLL i używać jej z C# lub Visual Basic.

- **Aplikacje programu .NET framework**. Większość aplikacji .NET Framework jest napisana w języku C# lub Visual Basic, ale możesz też C + +/ interfejsu wiersza polecenia ( `/clr` — opcja kompilatora w programie Visual C++). Firma Microsoft zaleca używanie języka C + +/ interfejsu wiersza polecenia dla minimalnej warstwa międzyoperacyjności w większej aplikacji, która zawiera kodu zarządzanego i natywnego.

##  <a name="BK_WindowsUniversal"></a> Windows Universal Apps

W systemie Windows 10 aplikacji będą mogli uruchamiać na wszystkich urządzeniach z systemem Windows 10, takich jak tablety i telefony komórkowe, a także na pulpicie. Na komputerze stacjonarnym, są one mogą być uruchamiane jako okien pulpitu, zamiast zawsze uruchomiona w trybie pełnoekranowym. Te aplikacje można również uruchomić na konsoli Xbox i na urządzeniach w przyszłości.  Model programowania dla dwóch typów aplikacji różni się od aplikacji pulpitu Win32. Te aplikacje Windows działają na środowiska wykonawczego Windows, który zawiera elementy interfejsu użytkownika, podstawowe usługi w przypadku tych aplikacji i zapewnia, a interfejsem do różnych urządzeń, które są obsługiwane. Te aplikacje skompiluj do kodu macierzystego i ma interfejsu użytkownika XAML lub używają DirectX. Możesz również zapisywać dane w kodzie natywnym, który może zużywać inne aplikacje Windows składników środowiska wykonawczego Windows — uwzględnia to aplikacje, które zostały napisane w języku C#, Visual Basic lub JavaScript. Aby uzyskać więcej informacji, zobacz [Utwórz aplikację "Hello world" platformy uniwersalnej systemu Windows w języku C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp), [Tworzenie prostej grze platformy uniwersalnej systemu Windows przy użyciu technologii DirectX](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game), i [składniki tworzenia środowiska wykonawczego Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

> [!TIP]
> W systemie Windows 10 Desktop App Converter służy również do pakietu istniejącej aplikacji klasycznych dla wdrożenia przez Microsoft Store. Aby uzyskać więcej informacji, zobacz [przy użyciu środowiska uruchomieniowego Visual C++ w projekcie Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) i [przenieść swoją aplikację do uniwersalnej platformy Windows (UWP) przy użyciu Desktop Bridge](https://msdn.microsoft.com/windows/uwp/porting/desktop-to-uwp-root).

Aby uzyskać przykłady Universal Windows Platform, zobacz [Windows Universal przykłady w witrynie GitHub](https://github.com/Microsoft/Windows-universal-samples)

Jeśli masz istniejący projekt Windows 8.1 i chcesz przenieść go do systemu Windows 10, zobacz [przenoszenie na platformę Windows Universal](../porting/porting-to-the-universal-windows-platform-cpp.md). Jeśli masz istniejące klasyczne biblioteki pulpitu Win32 i kod, który chcesz zintegrować z aplikacją platformy uniwersalnej systemu Windows, zobacz [porady: użycie istniejącego kodu C++ w aplikacji platformy uniwersalnej Windows](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).

Aby uzyskać więcej informacji na temat platformy uniwersalnej systemu Windows, zobacz [co to jest aplikacja Windows platformy Uniwersalnej?](/windows/uwp/get-started/whats-a-uwp).

Aby uzyskać więcej informacji na temat wszystkich tych pojęć, zobacz [Przewodnik po aplikacjach uniwersalnych Windows](http://go.microsoft.com/fwlink/p/?linkid=534605).

##  <a name="BK_Native"></a> Aplikacje pulpitu i serwera

Aby uzyskać podstawowe informacje o pisaniu aplikacji klienckich Windows dla komputerów, zobacz [projektowanie aplikacji Windows w języku C++](https://msdn.microsoft.com/vstudio//hh304489) i [wprowadzenie do Windows programowania w języku C++](https://msdn.microsoft.com/library/windows/desktop/ff381398).

W systemie Windows 10 można użyć Visual C++ do tworzenia wielu rodzajów programów pulpitu:

- Aplikacje i narzędzia wiersza polecenia. Aby uzyskać więcej informacji, zobacz [aplikacji konsoli](../windows/console-applications-in-visual-cpp.md).

- Aplikacje użytkownika, które mają zaawansowany interfejs graficzny użytkownika. Aby uzyskać więcej informacji, zobacz [Hilo: opracowywanie aplikacji C++ dla Windows](http://go.microsoft.com/fwlink/p/?LinkId=256417)

- W przypadku aplikacji przedsiębiorstwa i line-of-business, działających w .NET Framework. Większość aplikacji .NET Framework jest napisana w języku C# lub Visual Basic. Można użyć C + +/ interfejsu wiersza polecenia, aby utworzyć warstwy międzyoperacyjnych, umożliwiające kodu platformy .NET korzystać z natywnych bibliotek C++. Aby uzyskać więcej informacji, zobacz [programowania .NET w języku C + +/ interfejsu wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

- Klienty baz danych SQL, które działają w kodzie natywnym. Aby uzyskać więcej informacji, zobacz [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

- Dodatki dla aplikacji pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [Tworzenie dodatku C++ dla programu Outlook 2010](http://go.microsoft.com/fwlink/p/?LinkId=256420)

- Sterowniki urządzeń. Aby uzyskać więcej informacji, zobacz [Windows Driver Kit (WDK)](http://go.microsoft.com/fwlink/p/?LinkId=256421)

- Usługi systemu Windows. Aby uzyskać więcej informacji, zobacz [wprowadzenie do aplikacji usług Windows](/dotnet/framework/windows-services/introduction-to-windows-service-applications).

Można używać Visual C++, aby zapakować prawie każdy rodzaj niestandardowej funkcjonalności o wysokiej wydajności do bibliotek Win32 DLL lub bibliotek DLL modelu COM, które mogą być wykorzystywane przez aplikacje napisane w języku C++ lub innym — na przykład C# lub Visual Basic. Aby uzyskać więcej informacji dotyczących bibliotek WIn32 dll, zobacz [biblioteki dll w programie Visual C++](../build/dlls-in-visual-cpp.md). Aby uzyskać więcej informacji na temat programowanie COM, zobacz [składnik modelu COM](/windows/desktop/com/component-object-model--com--portal).

## <a name="games"></a>Gry

Gry DirectX można uruchomić na komputerach PC lub konsoli Xbox. Aby uzyskać więcej informacji, zobacz [Centrum deweloperów DirectX](http://go.microsoft.com/fwlink/p/?LinkId=256418).

## <a name="sdks-libraries-and-header-files"></a>Zestawy SDK, biblioteki i pliki nagłówkowe

Visual C++ zawiera biblioteki środowiska uruchomieniowego C (CRT), standardowej biblioteki języka C++ i inne biblioteki charakterystyczne dla Microsoft. Uwzględnianie folderów, które zawierają pliki nagłówkowe dla tych bibliotek znajdują się w katalogu instalacyjnym Visual Studio, w folderze \VC\ lub w przypadku CRT, w folderze instalacji zestawu Windows SDK.

Możesz użyć [Menedżera pakietów Vcpkg](../vcpkg.md) wygodny sposób instalowania kilkuset bibliotek typu open-source innych firm dla Windows.

Biblioteki firmy Microsoft obejmują:

- Microsoft Foundation Classes (MFC): Zorientowana obiektowo platforma do tworzenia tradycyjnych programów systemu Windows — szczególnie aplikacji dla przedsiębiorstw — które cechuje bogaty interfejs użytkownika zawierający przyciski, pola listy, widoki drzewa i inne formanty. Aby uzyskać więcej informacji, zobacz [aplikacji pulpitu MFC](../mfc/mfc-desktop-applications.md).

- Active Template Library (ATL): Zaawansowana biblioteka pomocnicza do tworzenia składników modelu COM. Aby uzyskać więcej informacji, zobacz [ATL COM pulpitu składniki](../atl/atl-com-desktop-components.md).

- C++ Accelerated Massive Parallelism (C++ AMP): Biblioteka, która umożliwia wykonywanie wysokiej wydajności obliczeń ogólnego przeznaczenia na procesorach GPU. Aby uzyskać więcej informacji, zobacz [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Środowisko uruchomieniowe współbieżności: Biblioteka, która upraszcza pracę przy programowaniu współbieżnym i asynchronicznym dla urządzeń wielordzeniowych. Aby uzyskać więcej informacji, zobacz [współbieżność środowiska wykonawczego](../parallel/concrt/concurrency-runtime.md).

Wiele scenariuszy programowania dla systemu Windows wymaga również Windows SDK, które zawiera pliki nagłówkowe umożliwiające dostęp do składników systemu operacyjnego Windows. Domyślnie program Visual Studio instaluje zestaw Windows SDK jako część obciążenia pulpitu C++ umożliwia tworzenie aplikacji Windows Universal apps. Do tworzenia aplikacji platformy uniwersalnej systemu Windows, należy do zestawu Windows SDK w wersji systemu Windows 10. Aby uzyskać informacje, zobacz [zestawu Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk). (Aby uzyskać więcej informacji na temat zestawów Windows SDK dla wcześniejszych wersji systemu Windows, zobacz [archiwum zestaw Windows SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)). 

**Program \Windows pliki (x86) zestawy** jest domyślną lokalizacją dla wszystkich wersji zestawu Windows SDK, który został zainstalowany.

Inne platformy, takie jak Xbox i Azure, mają swoje własne zestawy SDK, które również można zainstalować. Aby uzyskać więcej informacji, zobacz Centrum deweloperów DirectX i Centrum deweloperów Azure.

## <a name="development-tools"></a>Narzędzia programistyczne

Środowisko Visual Studio zawiera zaawansowany debuger kodu natywnego, narzędzia do analizy statycznej, graficzne narzędzia do debugowania, profesjonalny edytor kodu, wsparcie dla testów jednostkowych i wiele innych narzędzi. Aby uzyskać więcej informacji, zobacz [Rozpocznij tworzenie aplikacji za pomocą programu Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio), i [IDE i narzędzia programistyczne](../ide/ide-and-tools-for-visual-cpp-development.md).

## <a name="related-articles"></a>Powiązane artykuły

|Tytuł|Opis|
|-----------|-----------------|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Temat nadrzędny dla zawartości dla deweloperów Visual C++.|