---
title: "Kompilowanie projektów C++ w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ projects, building
- projects [C++], building
- builds [C++], about building in Visual Studio
ms.assetid: 9e8bc1a2-bb17-4951-937a-c757ed88d2d1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 074b43619d307d4d6ffeec1a057c9c27a4f9d05f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="building-c-projects-in-visual-studio"></a>Kompilowanie projektów C++ w Visual Studio
W programie Visual Studio zintegrowane środowisko programistyczne (IDE) istnieje kilka sposobów skompiluj całe rozwiązanie lub tylko jednego projektu w nim. Można również zmodyfikować ustawienia kompilacji i określić niestandardowe kroki procesu kompilacji dokonanie efektywniejsze procesie tworzenia aplikacji.  
  
 Aby zbudować rozwiązanie, które jest otwarty w programie Visual Studio i zaznaczone w **Eksploratora rozwiązań**, można wykonywać następujące czynności:  
  
-   Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
-   Lub, w **Eksploratora rozwiązań**, otwórz menu skrótów dla rozwiązania, a następnie wybierz pozycję **Kompiluj rozwiązanie**.  
  
-   Możesz również nacisnąć klawisz F7. (Jest to domyślny skrót klawiaturowy ustawienia środowiska deweloperskiego C/C++).  
  
-   Lub, w [okno polecenia](/visualstudio/ide/reference/command-window) (na pasku menu wybierz **widoku**, **inne okna**, **okno polecenia**), wprowadź `Build.BuildSolution`.  
  
-   Lub, w [Szybkie uruchamianie](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box) wprowadź `build build solution`.  
  
 Aby utworzyć projekt, który wybrano w **Eksploratora rozwiązań**, można wykonywać następujące czynności:  
  
-   Na pasku menu wybierz **kompilacji**, **kompilacji \<Nazwa projektu >**.  
  
-   Lub, w **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz pozycję **kompilacji**.  
  
-   Lub, w oknie wiersza polecenia (na pasku menu wybierz **widoku**, **inne okna**, **okno polecenia**), wprowadź `Build.BuildOnlyProject`.  
  
-   W polu Szybkie uruchamianie wprowadzić `build project only build only <project name>`.  
  
 Podczas tworzenia aplikacji Visual C++ w programie Visual Studio można modyfikować wiele ustawień kompilacji w oknie dialogowym stron właściwości projektu. Aby uzyskać informacje na temat ustawiania właściwości projektu, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
 Na przykład sposobu tworzenia, kompilacji i debugowania projektu C++ za pomocą środowiska IDE, zobacz [wskazówki: eksplorowanie środowiska IDE programu Visual Studio z C++](/visualstudio/ide/getting-started-with-cpp-in-visual-studio). Na przykład o używaniu środowiska IDE do kompilacji C + +/ CLR projektu, zobacz [wskazówki: kompilowanie programu C++ przeznaczonego dla CLR w Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md). Na przykład o używaniu środowiska IDE umożliwiające utworzenie aplikacji środowiska wykonawczego systemu Windows, temacie [tworzenie pierwszej aplikacji środowiska wykonawczego systemu Windows w języku C++](http://msdn.microsoft.com/library/windows/apps/hh974580.aspx).  
  
 Aby przeczytać więcej informacji o sposobie tworzenia, zmodyfikuj ustawienia kompilacji i określić niestandardowe kroki procesu kompilacji, zobacz następujące artykuły.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](../ide/understanding-custom-build-steps-and-build-events.md)  
 Opisuje sposób dostosowywania procesu kompilacji w zintegrowane środowisko programistyczne.  
  
 [Typowe makra dla właściwości i poleceń kompilacji](../ide/common-macros-for-build-commands-and-properties.md)  
 Wyświetla listę makra, które są dostępne, gdzie parametry są akceptowane.  
  
 [Konstruowanie projektów zewnętrznych](../ide/building-external-projects.md)  
 W tym artykule omówiono kompilowania projektów, korzystających z urządzeń poza zintegrowane środowisko programistyczne.  
  
 [Pliki projektu](../ide/project-files.md)  
 Przedstawia informacje o strukturze XML w pliku .vcxproj.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [VC ++ katalogów, projektów, opcje — Okno dialogowe](vcpp-directories-property-page.md)  
 (Tylko dla projektów MSBuild) Omówiono sposób zmodyfikować ścieżkę wyszukiwania dla plików wykonywalnych, Dołącz pliki, pliki bibliotek i pliki kodu źródłowego podczas kompilacji.  
  
 [Kompilowanie i tworzenie](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 Zawiera informacje na temat tworzenia w programie Visual Studio.  
  
 [Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)  
 Zawiera łącza do tematów opisujących kompilowania programu z wiersza polecenia lub zintegrowane środowisko programistyczne Visual Studio.  
  
 [Dokumentacja kompilacji w języku C/C++](../build/reference/c-cpp-building-reference.md)  
 Zawiera łącza do omówienie tworzenia programów w języku C++, kompilatora i konsolidatora, narzędzi i opcji dodatkowych kompilacji.  
  
 [Uaktualnianie projektów ze starszych wersji programu Visual C++](../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
 Zawiera łącza do tematów obejmujących problemów dotyczących uaktualniania projektu C++ do nowszej wersji zestawu narzędzi kompilatora.  
  
[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)  
  Szczegółowe informacje o sposobie uaktualniania aplikacji C++, które zostały utworzone we wcześniejszych wersjach programu Visual Studio i przeprowadzanie migracji aplikacji, które zostały utworzone przy użyciu narzędzia innego niż Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje uniwersalne systemu Windows (C++)](../windows/universal-windows-apps-cpp.md)