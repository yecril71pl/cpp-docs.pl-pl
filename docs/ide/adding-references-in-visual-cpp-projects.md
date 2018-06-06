---
title: Dodawanie odwołań do projektów Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.References
dev_langs:
- C++
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bda420768b1ff0819ba666f71d62bfffa86e2105
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33336111"
---
# <a name="adding-references-in-visual-c-projects"></a>Dodawanie odwołań do projektów Visual C++
Bardzo często programy do wywołania do interfejsów API w innych plików binarnych, takich jak biblioteki dll, składników środowiska wykonawczego systemu Windows, rozszerzenia SDK składników COM i zestawów platformy .NET. Sposób, w jaki te pliki binarne wyszukiwany zależy od zarówno na typ projektu, a typ danych binarnych.  
  
 W projekcie natywnych języka C++ zużywają natywnej biblioteki DLL lub składnika COM, który nie jest są produkowane przez inny projekt w rozwiązaniu, użycie metody LoadLibrary lub wywołanie funkcji CoCreateInstance można określić ścieżkę do pliku binarnego, w przeciwnym razie Niech system go zlokalizować przez wyszukiwanie w określonych ekran powitalny Definicja l lokalizacje.  
  
 W przypadku innych typów projektów, takich jak projekty platformy UWP lub C + +/ projektów interfejsu wiersza polecenia, lub gdy dane binarne jest tworzony przez inny projekt w rozwiązaniu, Dodaj *odwołania* zestawu, składnika lub projektu.   Odwołanie jest zasadniczo zestaw danych, które umożliwia programowi zlokalizować i nawiązać połączenie z danych binarnych.       Podczas dodawania odwołania programu Visual Studio obsługuje niski poziom szczegółów. Można ustawić odwołania z projektu C++ do .NET Frameworkassemblies (C + +/ CLI tylko), składniki modelu COM, inne projekty, w tym Twojego rozwiązania udostępnionych projektów lub połączone usługi, kliknij prawym przyciskiem myszy **odwołania** węzła w **Eksploratora rozwiązań** można wyświetlić **Menedżera odwołań**. Informacje wyświetlane w Menedżerze odwołania różni się zależnie od typu projektu.  
  
 W natywnego projektu C++ (ATL) pojęcie o *odwołania* ma zastosowanie tylko do innych projektów w rozwiązaniu, w tym udostępnionych projektów w taki sposób, aby wszystkie pojawi się w **Menedżera odwołań**:  
  
 ![Visual C&#43; &#43; Menedżera odwołań &#40;projektów ATL&#41;](../ide/media/visual-c---reference-manager--atl-projects-.png "Menedżera odwołań Visual C++ (projekty ATL)")  
  
 W języku C + +/ projektu interfejsu wiersza polecenia lub platformy uniwersalnej systemu Windows, pojęcie odwołań dotyczy rodzaje więcej plików binarnych, oprócz innych projektów w rozwiązaniu.  Te są wszystkie dostępne w **Menedżera odwołań**.
  
## <a name="reference-properties"></a>Właściwości odwołania  
 Każdy rodzaj odwołania ma właściwości. Właściwości można wyświetlić, wybierając odwołania w Eksploratorze rozwiązań i naciskając klawisz **Alt + Enter**, w przeciwnym razie kliknięcie prawym przyciskiem myszy i wybierając pozycję **właściwości**. Niektóre właściwości są tylko do odczytu i niektóre może być modyfikowany. Jednak zwykle nie trzeba ręcznie zmodyfikować te właściwości.  
  
### <a name="activex-reference-properties"></a>Właściwości odwołania ActiveX  
 Właściwości odwołania ActiveX są dostępne tylko dla odwołania do składników COM. Te właściwości są wyświetlane tylko po wybraniu składnika modelu COM w **odwołania** okienka. Nie można zmodyfikować właściwości.  
  
 **Pełna ścieżka kontrolki**  
 Wyświetla ścieżkę katalogu przywoływanej kontrolki.  
  
 **GUID kontrolki**  
 Wyświetla identyfikator GUID dla formantu ActiveX.  
  
 **Kontrola wersji**  
 Wyświetla wersję przywoływanej kontrolki ActiveX.  
  
 **Nazwy biblioteki typów**  
 Nazwa przywoływanej biblioteki typów.  
  
 **Narzędzie otoki**  
 Wyświetla narzędzie, które służy do tworzenia zestawu międzyoperacyjnego na podstawie przywoływanej biblioteki COM lub formantu ActiveX.  
  
### <a name="assembly-reference-properties"></a>Właściwości odwołania zestawu  
 Właściwości odwołania zestawu są dostępne tylko dla odwołania do Frameworkassemblies .NET w języku C + +/ CLI projektów. Te właściwości są wyświetlane tylko wtedy, gdy wybrano .NET Frameworkassembly **odwołania** okienka. Nie można zmodyfikować właściwości.  
  
 **Ścieżka względna**  
 Wyświetla ścieżkę względną z katalogu projektu do przywoływanego zestawu.  
  
### <a name="build-properties"></a>Właściwości kompilacji  
 Następujące właściwości są dostępne w różnych rodzajów odwołań. Umożliwiają one określają sposób tworzenia z odwołaniami.  
  
 **Kopiuj lokalnie**  
 Określa, czy ma być automatycznie kopiowany zestaw z odwołania do lokalizacji docelowej podczas kompilacji.  
  
 **Kopiuj lokalne zestawy satelickie**  
 Określa, czy ma być automatycznie kopiowany zestawy satelickie przywoływanego zestawu do lokalizacji docelowej podczas kompilacji. Używana, tylko jeśli **Kopiuj lokalnie** jest `true`.  
  
 **Odwołanie do zestawu wyjściowego**  
 Określa, że ten zestaw jest używany w procesie kompilacji. Jeśli `true`, zestaw jest używany w wierszu polecenia kompilatora podczas kompilacji.  
  
### <a name="project-to-project-reference-properties"></a>Właściwości odwołania projektu do projektu  
 Zdefiniuj następujące właściwości *odwołania projektu do projektu* z projektu, który wybrano w **odwołania** okienka do innego projektu w tym samym rozwiązaniu. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project).  
  
 **Zależności biblioteki konsolidacji**  
 Gdy ta właściwość jest **True**, system projektu zawiera linki do projektów zależnych pliki .lib, które są tworzone przez niezależnego projektu. Zazwyczaj będzie określać **True**.  
  
 **Identyfikator projektu**  
 Identyfikuje niezależne projektu. Wartość właściwości to system wewnętrzny identyfikator GUID, który nie może być modyfikowany.  
  
 **Używaj wejścia zależności biblioteki**  
 Gdy ta właściwość jest **False**, system projektów nie połączy do projektów zależnych plików .obj biblioteki utworzonego przez niezależnego projektu. W związku z tym wartość ta powoduje wyłączenie, konsolidowania przyrostowego. Zazwyczaj będzie określać **False** ponieważ tworzenie aplikacji może zająć dużo czasu, jeśli istnieje wiele niezależnych projektów.  
  
### <a name="reference-properties"></a>Właściwości odwołania  
 Następujące właściwości znajdują się odwołania do zestawu COM i .NET i nie może być modyfikowany.  
  
 **Nazwa zestawu**  
 Wyświetla nazwę zestawu przywoływanego zestawu.  
  
 **Kultury**  
 Wyświetla kultura wybranego odwołania.  
  
 **Opis**  
 Wyświetla opis wybranego odwołania.  
  
 **Pełna ścieżka**  
 Wyświetla ścieżkę katalogu przywoływanego zestawu.  
  
 **Tożsamość**  
 W przypadku .NET Frameworkassemblies Wyświetla pełną ścieżkę. Dla składników COM Wyświetla identyfikator GUID.  
  
 **Etykieta**  
 Wyświetla etykieta odwołania.  
  
 **Nazwa**  
 Wyświetla nazwę odwołania.  
  
 **Token klucza publicznego**  
 Wyświetla token klucza publicznego, który służy do identyfikowania przywoływanego zestawu.  
  
 **Silnej nazwy**  
 `true` Jeśli przywoływany zestaw ma silnej nazwy. Zestaw jest unikalnie wersjonowany.  
  
 **Wersja**  
 Wyświetla wersję przywoływanego zestawu.  
  
## <a name="see-also"></a>Zobacz też  
 [Strony właściwości](../ide/property-pages-visual-cpp.md)   
 [Praca z właściwościami projektu](../ide/working-with-project-properties.md)