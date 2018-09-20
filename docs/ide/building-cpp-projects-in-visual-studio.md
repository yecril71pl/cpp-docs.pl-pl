---
title: Kompilowanie projektów C++ w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ projects, building
- projects [C++], building
- builds [C++], about building in Visual Studio
ms.assetid: 9e8bc1a2-bb17-4951-937a-c757ed88d2d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0da2464684a06b62c6e22ea04bb68a01dc36f42b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382352"
---
# <a name="building-c-projects-in-visual-studio"></a>Kompilowanie projektów C++ w Visual Studio

W programie Visual Studio zintegrowane środowisko programistyczne (IDE) istnieje kilka sposobów tworzenia całego rozwiązania lub tylko jeden projekt w nim. Można także zmodyfikować ustawienia kompilacji i określić niestandardowych kroków kompilacji się proces tworzenia bardziej wydajne.

Aby utworzenie rozwiązania, w którym jest otwarta w programie Visual Studio i wybranego w **Eksploratora rozwiązań**, możesz:

- Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.

- Lub w **Eksploratora rozwiązań**, otwórz menu skrótów dla rozwiązania, a następnie wybierz **Kompiluj rozwiązanie**.

- Lub naciśnij klawisz F7. (Jest to domyślny skrót klawiaturowy dla ustawień rozwoju języka C/C++).

- Lub w [okna polecenia](/visualstudio/ide/reference/command-window) (na pasku menu wybierz **widoku**, **Windows inne**, **okna polecenia**), wprowadź `Build.BuildSolution`.

- Lub w [Szybkie uruchamianie](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box) wprowadź `build build solution`.

Aby skompilować projekt, który wybrano w **Eksploratora rozwiązań**, możesz:

- Na pasku menu wybierz **kompilacji**, **kompilacji \<Nazwa projektu >**.

- Lub w **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **kompilacji**.

- Lub, w oknie wiersza polecenia (na pasku menu wybierz **widoku**, **Windows inne**, **okna polecenia**), wprowadź `Build.BuildOnlyProject`.

- Lub, w polu Szybkie uruchamianie wpisz `build project only build only <project name>`.

W przypadku tworzenia aplikacji Visual C++ w programie Visual Studio, można modyfikować wiele ustawień kompilacji w oknie dialogowym strony właściwości projektu. Aby uzyskać informacje o sposobie ustawiania właściwości projektu, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).

Na przykład o tym, jak używać IDE do tworzenia, kompilowania i debugowania projektu w języku C++, zobacz [Instruktaż: Zapoznaj się z programu Visual Studio IDE, za pomocą języka C++](/visualstudio/ide/getting-started-with-cpp-in-visual-studio). Na przykład o tym, jak używać IDE do tworzenia w języku C + +/ CLR projektu, zobacz [wskazówki: kompilowanie programu C++ przeznaczonego dla CLR w programie Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md). Na przykład o tym, jak używać IDE do tworzenia aplikacji środowiska wykonawczego Windows, zobacz [tworzenie pierwszej aplikacji przy użyciu języka C++ środowiska wykonawczego Windows](https://msdn.microsoft.com/library/windows/apps/hh974580.aspx).

Aby przeczytać więcej na temat sposobu tworzenia, modyfikowania ustawień kompilacji i określ niestandardowe kroki kompilacji, zobacz następujące artykuły.

## <a name="in-this-section"></a>W tej sekcji

[Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](../ide/understanding-custom-build-steps-and-build-events.md)<br>
Opisuje sposób dostosowywania procesu kompilacji w zintegrowanym środowisku programistycznym.

[Typowe makra dla właściwości i poleceń kompilacji](../ide/common-macros-for-build-commands-and-properties.md)<br>
Wyświetla listę makra, które są dostępne, gdzie ciągi są akceptowane.

[Konstruowanie projektów zewnętrznych](../ide/building-external-projects.md)<br>
W tym artykule omówiono kompilowanie projektów, które używają obiektów poza zintegrowanym środowisku programistycznym.

[Pliki projektu](../ide/project-files.md)<br>
Przedstawia informacje o strukturze XML w pliku .vcxproj.

## <a name="related-sections"></a>Sekcje pokrewne

[VC ++ katalogi, projekty, okno dialogowe Opcje](vcpp-directories-property-page.md)<br>
(Tylko dla projektów programu MSBuild) W tym artykule omówiono, jak zmodyfikować ścieżkę wyszukiwania dla plików wykonywalnych, podając pliki, pliki biblioteki i pliki kodu źródłowego podczas kompilacji.

[Kompilowanie i tworzenie](/visualstudio/ide/compiling-and-building-in-visual-studio)<br>
Zawiera informacje dotyczące tworzenia aplikacji w programie Visual Studio.

[Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)<br>
Zawiera łącza do tematów opisujących, tworzenie programu z wiersza polecenia lub zintegrowanego środowiska projektowego programu Visual Studio.

[Dokumentacja kompilacji w języku C/C++](../build/reference/c-cpp-building-reference.md)<br>
Zawiera łącza do przeglądu w procesie tworzenia programów w języku C++, kompilatora i konsolidatora, narzędzi i opcji dodatkowych kompilacji.

[Uaktualnianie projektów ze starszych wersji programu Visual C++](../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br>
Zawiera łącza do tematów obejmujących problemów dotyczących uaktualniania projektu C++ na nowsze wersje zestawu narzędzi kompilatora.

[Visual C++ przewodnik przenoszenia i uaktualniania](../porting/visual-cpp-porting-and-upgrading-guide.md) szczegółowe informacje na temat sposobu uaktualniania aplikacji w języku C++, które zostały utworzone we wcześniejszych wersjach programu Visual Studio, a także jak przeprowadzić migrację aplikacji, które zostały utworzone przy użyciu narzędzi innych niż program Visual Studio.

## <a name="see-also"></a>Zobacz też

[Aplikacje uniwersalne systemu Windows (C++)](../windows/universal-windows-apps-cpp.md)