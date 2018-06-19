---
title: Omówienie programowania w języku systemu Windows w języku C++ | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 2096c36ec24c1ca7e20c789b8a1eb8c24589ccc1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881666"
---
# <a name="overview-of-windows-programming-in-c"></a>Omówienie programowania w systemie Windows w języku C++

Visual C++ można użyć do zapisania wiele rodzajów programy uruchamiane na komputerach z systemem Windows (x 86, x64 lub ARM), w systemie Windows server, w chmurze lub na konsoli Xbox. Programy dobrze napisane w języku C++ mają następujące cechy:
- efektywne w wymagania dotyczące pamięci
- ekonomiczny zużycie energii 
- można w pełni korzystać z urządzeń wielordzeniowych i wiele rdzeni
- możliwość ogólne obliczeniowych w jednostce przetwarzania grafiki (urządzenia GPGPU)   
- można korzystać z innych najnowsze funkcje sprzętu.

Istnieje kilka kategorii szerokie aplikacji systemu Windows, które można programować za pomocą programu Visual C++. Te kategorie mają różne modele programowania i modeli aplikacji, które zostały wprowadzone przez lata. Poszczególne modele używają różnych bibliotekami i interfejsami API zapewniają dostęp do platformy i Tworzenie interfejsów użytkownika, takie jak windows i oknach dialogowych. Standardowa biblioteka języka C++, a także innych firm biblioteki można w dowolnej z tych kategorii z kilku ograniczeń dla platformy uniwersalnej systemu Windows.

- [Uniwersalnych aplikacji systemu Windows](#BK_WindowsUniversal). Trzeci kategorii aplikacji systemu Windows wprowadzono w systemie Windows 8 i kontynuuje obsługę tej kategorii aplikacji w systemie Windows 10. Te aplikacje są często określane jako "aplikacji systemu Windows" i zawierają wersje desktop i mobile apps, przeznaczonych do szerokiej gamy urządzeń. Można zapisać tych aplikacji w języku C + +/ CX, dialekt C++ z obsługą rozwoju środowiska wykonawczego systemu Windows lub w standardu C++ w modelu COM za pomocą biblioteki środowiska uruchomieniowego systemu Windows (WRL). Te aplikacje pierwotnie są przeznaczone do uruchamiania pełnego ekranu, mimo że w systemie Windows 10 użytkownicy mają możliwość uruchamiania ich w oknie pulpitu. Te aplikacje są ukierunkowane touch, ale ułatwia działać, jeśli preferowane użytkowników lub nie ma ekranu dotykowego za pomocą myszy. Te aplikacje są dystrybuowane za pomocą Microsoft Store faktów, które doprowadziło do nich wywoływana aplikacji "Store".

Aplikacje platformy uniwersalnej systemu Windows są można uruchamiać na wszystkich urządzeniach z systemem Windows 10, takich jak tablety i telefony komórkowe, a także na pulpicie. Na pulpicie, są w stanie uruchomić okna pulpitu, zamiast zawsze uruchomiona w trybie pełnoekranowym. Te aplikacje można również uruchomić na konsoli Xbox i na urządzeniach w przyszłości.  Uruchamianie aplikacji platformy uniwersalnej systemu Windows na środowiska wykonawczego systemu Windows, który zawiera elementy interfejsu użytkownika, usługami i interfejs do różnych urządzeń, które są obsługiwane w systemie Windows.  

Pisania aplikacji platformy uniwersalnej systemu Windows w języku C + +/ CX, dialekt C++, można użyć [C + +/ biblioteki WinRT](https://moderncpp.com/)w niektórych scenariuszach. Aplikacji platformy uniwersalnej systemu Windows skompiluj do kodu natywnego i masz interfejsu użytkownika XAML lub użyj programu DirectX. Składniki środowiska uruchomieniowego systemu Windows, które są zapisywane w kodzie natywnym, czy można korzystać z aplikacji platformy uniwersalnej systemu Windows napisanych w innych językach. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji platformy uniwersalnej systemu Windows w języku C++](http://go.microsoft.com/fwlink/?LinkID=534976), [Utwórz pierwszy gry platformy uniwersalnej systemu Windows za pomocą programu DirectX](http://go.microsoft.com/fwlink/p/?LinkId=244656), i [składniki tworzenia środowiska wykonawczego systemu Windows w języku C++](http://go.microsoft.com/fwlink/p/?LinkId=244658).

   Ta kategoria zawiera również podstawowe składniki i obliczeniową kod w kontekście programowanie chmury i serwera przy użyciu języka C++. Czasami kodu wydajności intensywnie stanowiącej podstawę serwera lub aplikacji w chmurze są zapisywane w języku C++ w celu zwiększenia wydajności. Można skompilować taki kod do biblioteki DLL i używać go z języka C# lub Visual Basic.

- **Aplikacji programu .NET framework**. Większość aplikacji .NET Framework są napisane w języku C# lub Visual Basic, ale można też C + +/ CLI (/ CLR — opcja kompilatora języka Visual C++). Firma Microsoft zaleca używanie języka C + +/ CLI dla minimalnego warstwa międzyoperacyjności w większej aplikacji, która zawiera kodu zarządzanego i natywnego.

##  <a name="BK_WindowsUniversal"></a> Uniwersalnych aplikacji systemu Windows

Z systemem Windows 10 aplikacje są można uruchamiać na wszystkich urządzeniach z systemem Windows 10, takich jak tablety i telefony komórkowe, a także na pulpicie. Na pulpicie, są w stanie uruchomić okna pulpitu, zamiast zawsze uruchomiona w trybie pełnoekranowym. Te aplikacje można również uruchomić na konsoli Xbox i na urządzeniach w przyszłości.  Model programowania do dwa typy aplikacji różni się od aplikacji klasycznych systemu Win32. Te aplikacje systemu Windows uruchomić środowiska uruchomieniowego systemu Windows, który zawiera elementy interfejsu użytkownika, najważniejsze usługi te aplikacje i zapewnia, i interfejs do różnych urządzeń, które są obsługiwane. Te aplikacje skompiluj do kodu natywnego i masz interfejsu użytkownika XAML lub użyj programu DirectX. Można również napisać składników środowiska wykonawczego systemu Windows w kodzie natywnym, które mogą korzystać z innych aplikacji systemu Windows — te obejmują aplikacje, które są napisane w języku C#, Visual Basic lub JavaScript. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji platformy uniwersalnej systemu Windows "Hello world" w języku C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp), [Tworzenie prostego gry platformy uniwersalnej systemu Windows z DirectX](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game), i [składniki tworzenia środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

> [!TIP]
> Dla systemu Windows 10 można konwertera aplikacji pulpitu pakietu istniejącej aplikacji klasycznych dla wdrożenia za pomocą Microsoft Store. Aby uzyskać więcej informacji, zobacz [przy użyciu środowiska uruchomieniowego Visual C++ w projekcie Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) i [przełączyć aplikację pulpitu do systemu Windows platformy Uniwersalnej z Mostek pulpitu](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root).

Dla przykładów dla platformy uniwersalnej systemu Windows, temacie [próbki uniwersalnych systemu Windows w witrynie GitHub](https://github.com/Microsoft/Windows-universal-samples)

Jeśli masz istniejący projekt Windows 8.1, aby port go do systemu Windows 10, zobacz [przenoszenie na platformę Windows Universal](../porting/porting-to-the-universal-windows-platform-cpp.md). Jeśli korzystasz z istniejących klasycznej Win32 bibliotek pulpitu i kod, który chcesz zintegrować z aplikacji platformy uniwersalnej systemu Windows, zobacz [porady: użycie istniejącego kodu C++ w aplikacji platformy uniwersalnej systemu Windows](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).

Aby uzyskać więcej informacji na temat platformy uniwersalnej systemu Windows ogólnie rzecz biorąc, zobacz [co to jest aplikacja systemu Windows platformy Uniwersalnej?](/windows/uwp/get-started/whats-a-uwp).

Aby uzyskać więcej informacji na temat wszystkich tych pojęć, zobacz [przewodnik uniwersalnych aplikacji systemu Windows](http://go.microsoft.com/fwlink/p/?linkid=534605).

##  <a name="BK_Native"></a> Stacjonarnych i serwerów aplikacji

Aby uzyskać podstawowe informacje dotyczące pisania aplikacji klienta systemu Windows dla komputerów osobistych, zobacz [opracowywanie aplikacji systemu Windows w języku C++](http://msdn.microsoft.com/vstudio//hh304489) i [wprowadzenie do programowania w języku systemu Windows w języku C++](http://msdn.microsoft.com/library/windows/desktop/ff381398\(v=vs.85\).aspx).

W systemie Windows 10 Visual C++ służy do tworzenia wielu rodzajów programy klasyczne:

- Aplikacje i narzędzia wiersza polecenia. Aby uzyskać więcej informacji, zobacz [aplikacji konsoli](../windows/console-applications-in-visual-cpp.md).

- Aplikacje użytkownika, które mają zaawansowany interfejs graficzny użytkownika. Aby uzyskać więcej informacji, zobacz [Hilo: opracowywanie aplikacji dla Windows w języku C++](http://go.microsoft.com/fwlink/p/?LinkId=256417)

- Enterprise i biznesowych z aplikacji uruchamianych w programie .NET Framework. Większość aplikacji .NET Framework są napisane w języku C# lub Visual Basic. Można użyć C + +/ CLI, aby utworzyć międzyoperacyjnego warstwy, które umożliwiają kodu platformy .NET do korzystania z natywnej biblioteki języka C++. Aby uzyskać więcej informacji, zobacz [.NET Programowanie w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

- Klienty baz danych SQL, które działają w kodzie natywnym. Aby uzyskać więcej informacji, zobacz [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

- Dodatki dla aplikacji pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [tworzenia dodatku C++ dla programu Outlook 2010](http://go.microsoft.com/fwlink/p/?LinkId=256420)

- Sterowniki urządzeń. Aby uzyskać więcej informacji, zobacz [zestaw sterowników systemu Windows (WDK)](http://go.microsoft.com/fwlink/p/?LinkId=256421)

- Usługi systemu Windows. Aby uzyskać więcej informacji, zobacz [wprowadzenie do aplikacji usług systemu Windows](/dotnet/framework/windows-services/introduction-to-windows-service-applications).

Można używać Visual C++, aby zapakować prawie każdy rodzaj niestandardowej funkcjonalności o wysokiej wydajności do bibliotek Win32 DLL lub bibliotek DLL modelu COM, które mogą być wykorzystywane przez aplikacje napisane w języku C++ lub innym — na przykład C# lub Visual Basic. Aby uzyskać więcej informacji na temat biblioteki DLL systemu WIn32, zobacz [biblioteki dll w programie Visual C++](../build/dlls-in-visual-cpp.md). Aby uzyskać więcej informacji na temat programowanie COM, zobacz [składnik modelu COM](https://msdn.microsoft.com/library/windows/desktop/ms680573).

## <a name="games"></a>gry

Gry DirectX można uruchomić na komputerze lub usłudze Xbox. Aby uzyskać więcej informacji, zobacz [Centrum deweloperów DirectX](http://go.microsoft.com/fwlink/p/?LinkId=256418).

## <a name="sdks-libraries-and-header-files"></a>Zestawy SDK, biblioteki i pliki nagłówkowe

Visual C++ obejmuje C Runtime Library (CRT), standardowa biblioteka C++ i innych bibliotek specyficzne dla firmy Microsoft. Uwzględnianie folderów zawierających pliki nagłówkowe dla bibliotek znajdują się na albo w katalogu instalacyjnym programu Visual Studio w folderze \VC\ lub w przypadku CRT, w folderze instalacji zestawu Windows SDK.   

Można użyć [Menedżera pakietów Vcpkg](../vcpkg.md) chce zainstalować setki bibliotekach open source innych firm dla systemu Windows.

Biblioteki Microsoft obejmują:

- Microsoft Foundation Classes (MFC): Zorientowana obiektowo platforma do tworzenia tradycyjnych programów systemu Windows — szczególnie aplikacji dla przedsiębiorstw — które cechuje bogaty interfejs użytkownika zawierający przyciski, pola listy, widoki drzewa i inne formanty. Aby uzyskać więcej informacji, zobacz [aplikacji pulpitu MFC](../mfc/mfc-desktop-applications.md).

- Active Template Library (ATL): Zaawansowana biblioteka pomocnicza do tworzenia składników modelu COM. Aby uzyskać więcej informacji, zobacz [ATL COM — składniki pulpitu](../atl/atl-com-desktop-components.md).

- C++ Accelerated Massive Parallelism (C++ AMP): Biblioteka, która umożliwia wykonywanie wysokiej wydajności obliczeń ogólnego przeznaczenia na procesorach GPU. Aby uzyskać więcej informacji, zobacz [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Środowisko uruchomieniowe współbieżności: Biblioteka, która upraszcza pracę przy programowaniu współbieżnym i asynchronicznym dla urządzeń wielordzeniowych. Aby uzyskać więcej informacji, zobacz [współbieżność środowiska wykonawczego](../parallel/concrt/concurrency-runtime.md).

Wiele scenariuszy programowania dla systemu Windows wymaga również Windows SDK, które zawiera pliki nagłówkowe umożliwiające dostęp do składników systemu operacyjnego Windows. Domyślnie program Visual Studio instaluje zestaw Windows SDK jako część obciążenia C++ pulpitu, co umożliwia projektowanie aplikacji uniwersalnych systemu Windows. Utworzenie aplikacji platformy uniwersalnej systemu Windows, należy zestawu SDK systemu Windows w wersji systemu Windows 10. Aby uzyskać informacje, zobacz [zestawu Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk). (Aby uzyskać więcej informacji na temat zestawy Windows SDK dla wcześniejszych wersji systemu Windows, zobacz [archiwum zestaw Windows SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)). 

**Program \Windows pliki (x86) Kit** jest domyślną lokalizacją dla wszystkich wersji zestawu Windows SDK, który został zainstalowany.

Inne platformy, takie jak Xbox i Azure, mają swoje własne zestawy SDK, które również można zainstalować. Aby uzyskać więcej informacji, zobacz Centrum deweloperów DirectX i Centrum deweloperów Azure.

## <a name="development-tools"></a>Narzędzia programistyczne

Środowisko Visual Studio zawiera zaawansowany debuger kodu natywnego, narzędzia do analizy statycznej, graficzne narzędzia do debugowania, profesjonalny edytor kodu, wsparcie dla testów jednostkowych i wiele innych narzędzi. Aby uzyskać więcej informacji, zobacz [rozpocząć wdrażanie z programem Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio), i [IDE i narzędzia deweloperskie](../ide/ide-and-tools-for-visual-cpp-development.md).

## <a name="related-articles"></a>Powiązane artykuły

|Tytuł|Opis|
|-----------|-----------------|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Temat nadrzędny zawartości dewelopera Visual C++.|
