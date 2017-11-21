---
title: "Omówienie programowania w języku systemu Windows w języku C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 30a5138c4ec95b2d57f56b5cc4b5731c1be073ad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="overview-of-windows-programming-in-c"></a>Omówienie programowania w systemie Windows w języku C++
Możesz używać Visual C++ do pisania szerokiej gamy programów, które działają na komputerach PC z zainstalowanym systemem Windows (x86, x64 lub ARM), na serwerach z systemem Windows, w chmurze lub na konsoli Xbox. Dobrze napisane programy w języku C++ są szybkie, wydajne, oszczędne w zużyciu energii i są w stanie w pełni wykorzystać urządzenia wielordzeniowe, wykonywanie obliczeń ogólnego przeznaczenia na procesorach graficznych (GPGPU) i inne najnowsze osiągnięcia w dziedzinie sprzętu.  
  
 Istnieje kilka kategorii szerokie aplikacji systemu Windows, które można programować za pomocą programu Visual C++. Kategorie te mają różne modele programowania i modeli aplikacji, co oznacza, że używają one różne biblioteki i interfejsów API, które umożliwiają dostęp do platformy i udostępniają interfejs użytkownika.  
  
-   [Uniwersalnych aplikacji systemu Windows](#BK_WindowsUniversal). Trzeci kategorii aplikacji systemu Windows wprowadzono w systemie Windows 8 i kontynuuje obsługę tej kategorii aplikacji w systemie Windows 10. Te aplikacje są często określane jako "aplikacji systemu Windows" i zawierają wersje desktop i mobile apps, przeznaczonych do szerokiej gamy urządzeń. Można zapisać tych aplikacji w języku C + +/ CX, dialekt C++ z obsługą rozwoju środowiska wykonawczego systemu Windows lub w standardu C++ w modelu COM za pomocą biblioteki środowiska uruchomieniowego systemu Windows (WRL). Te aplikacje pierwotnie są przeznaczone do uruchamiania pełnego ekranu, mimo że w systemie Windows 10 użytkownicy mają możliwość uruchamiania ich w oknie pulpitu. Te aplikacje są ukierunkowane touch, ale ułatwia działać, jeśli preferowane użytkowników lub nie ma ekranu dotykowego za pomocą myszy. Te aplikacje są dystrybuowane w Sklepie Windows, faktów, które doprowadziło do nich wywoływana "Aplikacje ze Sklepu Windows."  
  
-   [Pulpitu, serwera i aplikacji w chmurze i gry](#BK_Native). Ta kategoria zawiera aplikacje pulpitu systemu Windows, czasami nazywane aplikacji Win32, ponieważ te aplikacje były przy użyciu interfejsu API Win32 na starszych niż Windows 8, wszystkie aplikacje systemu Windows były w tej kategorii. Aplikacje w tej kategorii można użyć MFC dla interfejsu użytkownika i ATL do interakcji z składniki systemu Windows, które są zazwyczaj obiektów COM.  
  
     Aplikacje, składniki lub biblioteki napisany za pomocą standardu C++ również mieści się w tej kategorii.  
  
     Ta kategoria zawiera również podstawowe składniki i obliczeniową kod w kontekście programowanie chmury i serwera przy użyciu języka C++. Czasami kodu wydajności intensywnie stanowiącej podstawę serwera lub aplikacji w chmurze są zapisywane w języku C++ w celu zwiększenia wydajności. Można skompilować taki kod do biblioteki DLL i używać go z języka C# lub Visual Basic.  
  
-   **Aplikacji programu .NET framework**. Większość aplikacji .NET Framework są napisane w języku C# lub Visual Basic, ale można też C + +/ CLI (/ CLR — opcja kompilatora języka Visual C++). Firma Microsoft zaleca używanie języka C + +/ CLI dla minimalnego warstwa międzyoperacyjności w większej aplikacji, która zawiera kodu zarządzanego i natywnego.  
  
##  <a name="BK_WindowsUniversal"></a>Uniwersalnych aplikacji systemu Windows  
 Z systemem Windows 10 aplikacje są można uruchamiać na wszystkich urządzeniach z systemem Windows 10, takich jak tablety i telefony komórkowe, a także na pulpicie. Na pulpicie, są w stanie uruchomić okna pulpitu, zamiast zawsze uruchomiona w trybie pełnoekranowym. Te aplikacje można również uruchomić na konsoli Xbox i na urządzeniach w przyszłości.  Model programowania do dwa typy aplikacji różni się od aplikacji klasycznych systemu Win32. Te aplikacje systemu Windows uruchomić środowiska uruchomieniowego systemu Windows, który zawiera elementy interfejsu użytkownika, najważniejsze usługi te aplikacje i zapewnia, i interfejs do różnych urządzeń, które są obsługiwane. Te aplikacje skompiluj do kodu natywnego i masz interfejsu użytkownika XAML lub użyj programu DirectX. Można również napisać składników środowiska wykonawczego systemu Windows w kodzie natywnym, które mogą korzystać z innych aplikacji systemu Windows — te obejmują aplikacje, które są napisane w języku C#, Visual Basic lub JavaScript. Aby uzyskać więcej informacji, zobacz [tworzenie pierwszej aplikacji Sklepu Windows w języku C++](http://go.microsoft.com/fwlink/?LinkID=534976), [Utwórz pierwszy gry Sklepu Windows za pomocą programu DirectX](http://go.microsoft.com/fwlink/p/?LinkId=244656), i [składniki tworzenia środowiska wykonawczego systemu Windows w języku C++](http://go.microsoft.com/fwlink/p/?LinkId=244658).  

 > [!TIP]  
> Dla systemu Windows 10 można konwertera aplikacji pulpitu pakietu istniejącej aplikacji klasycznych dla wdrożenia za pomocą portalu Sklepu Windows. Aby uzyskać więcej informacji, zobacz [przy użyciu środowiska uruchomieniowego Visual C++ w projekcie Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) i [przełączyć aplikację pulpitu do systemu Windows platformy Uniwersalnej z Mostek pulpitu](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root).
  
  
 Dla przykładów dla platformy uniwersalnej systemu Windows, temacie [próbki uniwersalnych systemu Windows w witrynie GitHub](https://github.com/Microsoft/Windows-universal-samples)  
  
 Jeśli masz istniejący projekt Windows 8.1, aby port go do systemu Windows 10, zobacz [przenoszenie na platformę Windows Universal](../porting/porting-to-the-universal-windows-platform-cpp.md). Jeśli korzystasz z istniejących klasycznej Win32 bibliotek pulpitu i kod, który chcesz zintegrować z aplikacji platformy uniwersalnej systemu Windows, zobacz [porady: użycie istniejącego kodu C++ w aplikacji platformy uniwersalnej systemu Windows](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).  
  
 Można również napisać składników, gier i aplikacji uniwersalnych systemu Windows bez użycia C + +/ CX; Zamiast tego można użyć Biblioteka szablonów C++ środowiska wykonawczego systemu Windows (Biblioteka szablonów C++ środowiska wykonawczego systemu Windows). Aby uzyskać więcej informacji, zobacz [Windows środowiska uruchomieniowego C++ szablonu biblioteki (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).  
  
 Z [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], można opracować aplikacji uniwersalnych systemu Windows, uruchomionych w systemie Windows 10 komputery i urządzenia przenośne. Można również tworzyć aplikacje Windows 8.1 i Windows Phone 8.1 aplikacji w [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], ale w tym celu należy najpierw zainstalować program Visual Studio 2013 na tym samym komputerze, a następnie skonfiguruj projektu do **programu Visual Studio 2013 (v120)** zestawu narzędzi . Aby skonfigurować to ustawienie w projekcie, otwórz właściwości projektu i **ogólne** sekcji, ustaw **zestaw narzędzi platformy** do **programu Visual Studio 2013 (v120)**.  
  
 W przypadku instalowania narzędzi Phone 8.0 w Instalatorze programu Visual Studio, możesz zastosować Windows Phone 8.0.  
  
 Nowe pojęcie wprowadzone w systemie Windows 10 w nazwie Umowy interfejsu API zastępuje stary praktyka przeznaczonych dla określonej wersji systemu Windows. Zamiast tego możesz wybrać które umowy interfejsu API aplikacji potrzeb, a następnie uruchomi na dowolnym urządzeniu systemu Windows, który obsługuje tych umów. Kontrakt interfejsu API jest zestawem stabilna interfejsów API, które umożliwiają dostęp do zasobów platformy lub urządzenia. Kontrakty interfejsu API można dołączyć jako odwołania w systemie projektu. W projekcie programu Visual Studio Jeśli Dodaj odwołanie do określonego zestawu SDK rozszerzenia programu Visual Studio dodaje odpowiednich umowach interfejsu API.  
  
 Aby uzyskać więcej informacji na temat wszystkich tych pojęć, zobacz [przewodnik uniwersalnych aplikacji systemu Windows](http://go.microsoft.com/fwlink/?LinkId=534605).  
  
##  <a name="BK_Native"></a>Pulpitu, serwera i aplikacji w chmurze i gry  
 W chmurze można zapisywać zestawów Azure natywnego kodu w języku C++ i wywołują je z ról sieci Web, które są tworzone w języku C#. Aby uzyskać więcej informacji, zobacz [zestawu Azure SDK](http://go.microsoft.com/fwlink/p/?LinkId=256416).  
  
 Aby uzyskać podstawowe informacje dotyczące pisania aplikacji klienta systemu Windows dla komputerów osobistych, zobacz [opracowywanie aplikacji systemu Windows w języku C++](http://msdn.microsoft.com/vstudio//hh304489) i [wprowadzenie do programowania w języku systemu Windows w języku C++](http://msdn.microsoft.com/library/windows/desktop/ff381398\(v=vs.85\).aspx).  
  
 W systemie Windows 10 Visual C++ służy do tworzenia wielu rodzajów programy:  
  
-   Aplikacje i narzędzia wiersza polecenia. Aby uzyskać więcej informacji, zobacz [aplikacji konsoli](../windows/console-applications-in-visual-cpp.md).  
  
-   Gry DirectX, które działają na komputerach PC lub konsoli Xbox. Aby uzyskać więcej informacji, zobacz [Centrum deweloperów DirectX](http://go.microsoft.com/fwlink/p/?LinkId=256418).  
  
-   Aplikacje użytkownika, które mają zaawansowany interfejs graficzny użytkownika. Aby uzyskać więcej informacji, zobacz [Hilo: opracowywanie aplikacji dla Windows w języku C++](http://go.microsoft.com/fwlink/p/?LinkId=256417)  
  
-   Aplikacje dla przedsiębiorstw i LOB, które działają na platformie .NET Framework lub służą jako most między aplikacjami .NET Framework i aplikacjami lub składnikami napisanymi w kodzie natywnym. Aby uzyskać więcej informacji, zobacz [.NET Programowanie w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
-   Klienty baz danych SQL, które działają w kodzie natywnym. Aby uzyskać więcej informacji, zobacz [SQL Server Native Client](http://go.microsoft.com/fwlink/p/?LinkId=256419).  
  
-   Dodatki dla aplikacji pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [tworzenia dodatku C++ dla programu Outlook 2010](http://go.microsoft.com/fwlink/p/?LinkId=256420)  
  
-   Sterowniki urządzeń. Aby uzyskać więcej informacji, zobacz [zestaw sterowników systemu Windows (WDK)](http://go.microsoft.com/fwlink/p/?LinkId=256421)  
  
-   Usługi systemu Windows. Aby uzyskać więcej informacji, zobacz [wprowadzenie do aplikacji usług systemu Windows](/dotnet/framework/windows-services/introduction-to-windows-service-applications).  
  
 Można używać Visual C++, aby zapakować prawie każdy rodzaj niestandardowej funkcjonalności o wysokiej wydajności do bibliotek Win32 DLL lub bibliotek DLL modelu COM, które mogą być wykorzystywane przez aplikacje napisane w języku C++ lub innym — na przykład C# lub Visual Basic. Aby uzyskać więcej informacji na temat biblioteki DLL systemu WIn32, zobacz [biblioteki dll w programie Visual C++](../build/dlls-in-visual-cpp.md). Aby uzyskać więcej informacji na temat programowanie COM, zobacz [składnik modelu COM.](http://msdn.microsoft.com/en-us/375d29a7-a1f3-4bd8-8621-bad7a049b2aa).  
  
## <a name="sdks-and-header-files"></a>Zestawy SDK i pliki nagłówkowe  
 Visual C++ obejmuje C Runtime Library (CRT), standardowa biblioteka C++ i innych bibliotek specyficzne dla firmy Microsoft. Uwzględnianie folderów zawierających pliki nagłówka dla biblioteki te są albo znajduje się w katalogu instalacyjnym programu Visual Studio w folderze \VC\ lub w przypadku CRT, folderu instalacyjnego zestawu SDK systemu Windows, na przykład Windows Kits\10 w plikach programu folder Windows 10 SDK.  Biblioteki Microsoft obejmują:  
  
-   Microsoft Foundation Classes (MFC): Zorientowana obiektowo platforma do tworzenia tradycyjnych programów systemu Windows — szczególnie aplikacji dla przedsiębiorstw — które cechuje bogaty interfejs użytkownika zawierający przyciski, pola listy, widoki drzewa i inne formanty. Aby uzyskać więcej informacji, zobacz [aplikacji pulpitu MFC](../mfc/mfc-desktop-applications.md).  
  
-   Active Template Library (ATL): Zaawansowana biblioteka pomocnicza do tworzenia składników modelu COM. Aby uzyskać więcej informacji, zobacz [ATL COM — składniki pulpitu](../atl/atl-com-desktop-components.md).  
  
-   C++ Accelerated Massive Parallelism (C++ AMP): Biblioteka, która umożliwia wykonywanie wysokiej wydajności obliczeń ogólnego przeznaczenia na procesorach GPU. Aby uzyskać więcej informacji, zobacz [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).  
  
-   Środowisko uruchomieniowe współbieżności: Biblioteka, która upraszcza pracę przy programowaniu współbieżnym i asynchronicznym dla urządzeń wielordzeniowych. Aby uzyskać więcej informacji, zobacz [współbieżność środowiska wykonawczego](../parallel/concrt/concurrency-runtime.md).  
  
 Wiele scenariuszy programowania dla systemu Windows wymaga również Windows SDK, które zawiera pliki nagłówkowe umożliwiające dostęp do składników systemu operacyjnego Windows. Domyślnie wszystkie wersje programu Visual Studio 2015, zainstaluj zestaw Windows SDK, który umożliwia tworzenie aplikacji uniwersalnych systemu Windows. Tworzenie aplikacji uniwersalnych systemu Windows dla systemu Windows 10, należy zestawu SDK systemu Windows w wersji systemu Windows 10. Aby uzyskać informacje o zestawie SDK systemu Windows 10, zobacz [zestawu Windows 10 SDK](http://go.microsoft.com/fwlink/p/?LinkId=534603). (Aby uzyskać więcej informacji na temat zestawy Windows SDK dla wcześniejszych wersji systemu Windows, zobacz [Omówienie zestawu Windows SDK](http://msdn.microsoft.com/Library/9a2db508-5b77-43f8-afa4-1ca82d24bb83)).  
  
 Inne platformy, takie jak Xbox i Azure, mają swoje własne zestawy SDK, które również można zainstalować. Aby uzyskać więcej informacji, zobacz Centrum deweloperów DirectX i Centrum deweloperów Azure.  
  
## <a name="development-tools"></a>Narzędzia programistyczne  
 Środowisko Visual Studio zawiera zaawansowany debuger kodu natywnego, narzędzia do analizy statycznej, graficzne narzędzia do debugowania, profesjonalny edytor kodu, wsparcie dla testów jednostkowych i wiele innych narzędzi. Aby uzyskać więcej informacji, zobacz [programowanie aplikacji w programie Visual Studio](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68), i [IDE i narzędzia deweloperskie](../ide/ide-and-tools-for-visual-cpp-development.md).  
  
## <a name="related-articles"></a>Powiązane artykuły  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Visual C++](../visual-cpp-in-visual-studio.md)|Temat nadrzędny zawartości dewelopera Visual C++.|