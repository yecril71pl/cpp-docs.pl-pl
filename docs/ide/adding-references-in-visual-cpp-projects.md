---
title: Dodawanie odwołań w projektach języka Visual C++ | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 1438b364dac817fe2dbe47f117d672165a7693d5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722452"
---
# <a name="adding-references-in-visual-c-projects"></a>Dodawanie odwołań do projektów Visual C++
Bardzo często programy, aby wywoływać interfejsy API w innych plików binarnych, takich jak biblioteki dll, składników środowiska wykonawczego Windows, zestawy SDK rozszerzenia, składników COM i zestawy .NET. Zarówno na typ projektu i typ danych binarnych, zależy od sposobu, w jaki program znajdzie te pliki binarne.  
  
 W macierzystym projektu w języku C++ Jeśli korzystanie z natywnych bibliotek DLL lub COM składnikiem, który nie jest generowany przez inny projekt w rozwiązaniu umożliwia LoadLibrary lub CoCreateInstance Określ ścieżkę do pliku binarnego, w przeciwnym razie Niech system wyszukanie przez wyszukiwanie w określonych ekran powitalny lokalizacje zdefiniowane l.  
  
 W innych typów projektów, takich jak projekty platformy uniwersalnej systemu Windows lub C + +/ projektów interfejsu wiersza polecenia, lub gdy dane binarne, jest generowany przez inny projekt w rozwiązaniu, Dodaj *odwołania* zestawu, składnika lub projektu.   Odwołanie to zasadniczo zestaw danych, które zapewnia program, aby zlokalizować i nawiązać połączenie z plikiem binarnym.       Podczas dodawania odwołania programu Visual Studio obsługuje niskopoziomowy odpowiedzialny szczegółowe informacje. Do zestawu odwołania z projektu w języku C++ do .NET Frameworkassemblies (C + +/ interfejsu wiersza polecenia, tylko), składników COM, inne projekty w tym Twoje rozwiązanie udostępnionych projektów lub połączone usługi, kliknij prawym przyciskiem myszy **odwołania** węzła w **Eksploratora rozwiązań** aby przywołać **Menadżer odwołań**. Informacje wyświetlane w Menedżerze odwołań różnią się zależnie od typu projektu.  
  
 Z natywnego projektu C++ (ATL) pojęcia programu *odwołania* ma zastosowanie tylko do innych projektów w rozwiązaniu, w tym projekty udostępnione w taki sposób, aby wszystkie widoczne w **Menadżer odwołań**:  
  
 ![Program Visual C&#43; &#43; Menadżer odwołań &#40;projektach ATL&#41;](../ide/media/visual-c---reference-manager--atl-projects-.png "Visual C++ Reference Manager (projekty ATL)")  
  
 W języku C + +/ interfejsu wiersza polecenia lub Universal Windows Platform projektu, koncepcja odwołania dotyczy więcej rodzajów plików binarnych, oprócz innych projektów w rozwiązaniu.  Te są wszystkie dostępne w **Menadżer odwołań**.
  
## <a name="reference-properties"></a>Właściwości odwołania  
 Każdy rodzaj odwołania ma właściwości. Właściwości można wyświetlić, wybierając odwołania w Eksploratorze rozwiązań i naciskając klawisz **Alt + Enter**, lub kliknąć prawym przyciskiem myszy i wybierając **właściwości**. Niektóre właściwości są tylko do odczytu, a niektóre mogą być modyfikowane. Jednak zazwyczaj nie trzeba ręcznie zmodyfikować te właściwości.  
  
### <a name="activex-reference-properties"></a>Właściwości odwołania ActiveX  
 Właściwości odwołania ActiveX są dostępne tylko w przypadku odwołania do składników modelu COM. Te właściwości są wyświetlane tylko wtedy, gdy wybrano składnika modelu COM **odwołania** okienka. Nie można zmodyfikować właściwości.  
  
- **Pełna ścieżka kontrolki**

   Wyświetla ścieżkę katalogu przywoływanej kontrolki.  
  
- **Identyfikator GUID kontrolki**

   Wyświetla identyfikator GUID dla formantu ActiveX.  
  
- **Wersja kontrolki**

   Wyświetla wersję przywoływanej kontrolki ActiveX.  
  
- **Nazwa biblioteki typów**

   Nazwa przywoływanej biblioteki typów.  
  
- **Narzędzie otoki**

   Wyświetla narzędzie, które służy do tworzenia zestawu międzyoperacyjnego na podstawie przywoływanej biblioteki COM lub formantu ActiveX.  
  
### <a name="assembly-reference-properties"></a>Właściwości odwołania zestawu  
 Właściwości odwołania do zestawu są dostępne tylko dla odwołania do Frameworkassemblies .NET w języku C + +/ CLI projektów. Te właściwości są wyświetlane tylko wtedy, gdy wybrano .NET Frameworkassembly **odwołania** okienka. Nie można zmodyfikować właściwości.  
  
- **Ścieżka względna**

   Wyświetla ścieżkę względną z katalogu projektu do przywoływanego zestawu.  
  
### <a name="build-properties"></a>Właściwości kompilacji  
 Następujące właściwości są dostępne w różnych rodzajach odwołania. Umożliwiają one określają sposób tworzenia z odwołania.  
  
- **Kopia lokalna**

   Określa, czy ma być automatycznie kopiowany przywoływany zestaw do lokalizacji docelowej podczas kompilacji.  
  
- **Kopiuj lokalne zestawy satelickie**

   Określa, czy ma być automatycznie kopiowany zestawy satelickie przywoływanego zestawu do lokalizacji docelowej podczas kompilacji. Używany tylko, jeśli **Kopiuj lokalnie** jest `true`.  
  
- **Wyjście zestawu odwołania**

   Określa, że ten zestaw jest używany w procesie kompilacji. Jeśli `true`, zestaw jest używany w wierszu polecenia kompilatora podczas kompilacji.  
  
### <a name="project-to-project-reference-properties"></a>Właściwości odwołania projektu do projektu  
 Zdefiniuj następujące właściwości *odwołania projekt projekt* z projektu, który wybrano w **odwołania** okienka do innego projektu w tym samym rozwiązaniu. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project).  
  
- **Zależności biblioteki konsolidacji**

   Gdy ta właściwość jest **True**, system projektu łączy do projektu zależnego pliki .lib, które są tworzone przez niezależnych projektu. Zazwyczaj można określić **True**.  
  
- **Identyfikator projektu**

   Jednoznacznie identyfikuje niezależnie od projektu. Wartość właściwości jest systemu wewnętrznego identyfikator GUID, który nie może być modyfikowany.  
  
- **Używaj wejścia zależności biblioteki**

   Gdy ta właściwość jest **False**, system projektu nie połączy do projektu zależnego pliki .obj dla biblioteki utworzony przez projekt niezależny. W związku z tym wartość ta wyłącza łączenie przyrostowe. Zazwyczaj można określić **False** ponieważ Kompilowanie aplikacji może zająć dużo czasu, jeśli istnieje wiele projektów niezależnych.  
  
### <a name="reference-properties"></a>Właściwości odwołania  
 Następujące właściwości znajdują się na odwołania do zestawu modelu COM i .NET, a nie może być modyfikowany.  
  
- **Nazwa zestawu**

   Wyświetla nazwę zestawu dla przywoływanego zestawu.  
  
- **Kultury**

   Wyświetla kultura wybranego odwołania.  
  
- **Opis**

   Wyświetla opis wybranego odwołania.  
  
- **Pełna ścieżka**

   Wyświetla ścieżkę katalogu przywoływanego zestawu.  
  
- **Tożsamość**

   W przypadku Frameworkassemblies .NET Wyświetla pełną ścieżkę. Dla składników modelu COM Wyświetla identyfikator GUID.  
  
- **Etykieta**

   Wyświetla etykieta odwołania.  
  
- **Nazwa**

   Wyświetla nazwę odwołania.  
  
- **Token klucza publicznego**

   Wyświetla token klucza publicznego, który służy do identyfikowania przywoływanego zestawu.  
  
- **Silna nazwa**

   `true` Jeśli przywoływany zestaw ma silną nazwę. Silną nazwą ma unikatową wersję.  
  
- **Wersja**

   Wyświetla wersję przywoływanego zestawu.  
  
## <a name="see-also"></a>Zobacz też  
 [Strony właściwości](../ide/property-pages-visual-cpp.md)   
 [Praca z właściwościami projektu](../ide/working-with-project-properties.md)