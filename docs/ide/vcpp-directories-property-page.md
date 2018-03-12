---
title: "Strona właściwości katalogów VC ++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCDirectories.IncludePath
- VC.Project.VCDirectories.ReferencePath
- VC.Project.VCDirectories.SourcePath
- VC.Project.VCDirectories.LibraryWPath
- VC.Project.VCDirectories.ExecutablePath
- VC.Project.VCDirectories.LibraryPath
- VS.ToolsOptionsPages.Projects.VCDirectories
- VC.Project.VCDirectories.ExcludePath
dev_langs:
- C++
helpviewer_keywords:
- VC++ Directories Property Page
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1608bc5e78da98feb39be14d779677839f664058
ms.sourcegitcommit: eb246547c7c9adc7d7ac4083ef09bf6e54dec914
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="vc-directories-property-page-windows"></a>VC ++ strona właściwości katalogów (system Windows)

Użyj tej strony właściwości stwierdzić, które katalogi do użycia podczas tworzenia aktualnie wybrany projekt programu Visual Studio. Aby ustawić katalogów dla wielu projektów w rozwiązaniu, użyj arkusza właściwości niestandardowej, zgodnie z opisem w [tworzenia konfiguracji wielokrotnego użytku właściwości](working-with-project-properties.md#bkmkPropertySheets).

Dla wersji systemu Linux na tej stronie, zobacz [katalogi VC ++ (Linux C++)](../linux/prop-pages/directories-linux.md).   

Aby uzyskać dostęp do **katalogi VC ++** strony właściwości:

1. Jeśli **Eksploratora rozwiązań** okna nie jest widoczne, następnie w menu głównym wybierz **widoku** > **Eksploratora rozwiązań**.
1. Kliknij prawym przyciskiem myszy węzeł projektu (nie rozwiązanie najwyższego poziomu) i wybierz polecenie **właściwości**.
1. W lewym okienku **strony właściwości** okno dialogowe, wybierz opcję **właściwości konfiguracji** > **katalogi VC ++**.  

Katalogi VC ++ właściwości stosowane do projektu, nie węzła rozwiązania najwyższego poziomu. Jeśli nie widzisz **katalogi VC ++** w obszarze **właściwości konfiguracji**, wybierz węzeł projektu C++ w **Eksploratora rozwiązań** okno: 

![Wybierz węzeł projektu](media/vcppdir.png "wybierz węzeł projektu, aby wyświetlić właściwości katalogów VC ++")

Należy pamiętać, że **katalogi VC ++** strony właściwości dla projektów i platform wygląda inaczej. Aby uzyskać informacje specyficzne dla projektów Linux C++, zobacz [katalogi VC ++ (Linux C++)](../linux/prop-pages/directories-linux.md). 
 
Jeśli nie masz doświadczenia z *właściwości projektu* w programie Visual Studio, może być przydatne do odczytu pierwszego [Praca z właściwościami projektu](working-with-project-properties.md). 
 
Domyślne ustawienia **katalogi VC ++** właściwości są zależne od typu projektu. Dla projektów pulpitu obejmują one lokalizacje narzędzi C++ dla określonego zestawu narzędzi platformy i lokalizacji zestawu Windows SDK. Możesz zmienić **zestaw narzędzi platformy** i **wersji zestawu Windows SDK** na **właściwości konfiguracji** > **ogólne** Strona. 

Aby wyświetlić wartości na żadnym z katalogów:

1. Wybierz jedną z właściwości w **katalogi VC ++** strony. Na przykład wybrać **katalogi bibliotek**.
1. Wybierz przycisk strzałki w dół na końcu pola wartości właściwości.
1. Z menu rozwijanego wybierz **Edytuj**.

![Edytuj katalogi bibliotek](media/vcppdir_libdir_edit.png "okna dialogowego, aby edytować ścieżki biblioteki")

Pojawi się okno dialogowe następująco: 

![Pokaż katalogi bibliotek](media/vcppdir_libdir.png "okna dialogowego, aby dodać lub usunąć ścieżki biblioteki")

To okno dialogowe służy do wyświetlenia bieżącego katalogów. Jednak jeśli chcesz zmienić lub dodać katalog jest lepiej jest użyć **Menedżer właściwości** Aby utworzyć arkusz właściwości lub zmodyfikować domyślny arkusz właściwości użytkownika. Aby uzyskać więcej informacji, zobacz [tworzenia konfiguracji wielokrotnego użytku właściwości](working-with-project-properties.md#bkmkPropertySheets).

Jak pokazano powyżej, podano wiele ścieżek dziedziczone jako makr.  Aby sprawdzić bieżącą wartość makra, wybierz **makra** przycisk w prawym dolnym rogu okna dialogowego. Należy pamiętać, że wiele makra są zależne od typu konfiguracji. Makra kompilacji debugowania może zwrócić z inną ścieżką niż sam makra w kompilacji wydania. 

Można wyszukiwać dopasowania częściowej lub pełnej w polu edycji. Na poniższej ilustracji przedstawiono wszystkie makra zawierające ciąg "WindowsSDK", a także pokazanie bieżącej ścieżki, która daje w wyniku makra:

![Zobacz wartości makra](media/vcppdir_libdir_macros.png "okna dialogowego, aby edytować makra")

Uwaga: Lista jest wypełniana podczas pisania. Nie naciśnij **Enter**.

Aby uzyskać więcej informacji na temat makr i dlaczego należy ich używać zamiast ustalony ścieżek, jeśli to możliwe, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md#bkmkPropertiesVersusMacros). 

Lista często używane makra, zobacz [wspólnej makra dla poleceń kompilacji oraz właściwości](https://docs.microsoft.com/en-us/cpp/ide/common-macros-for-build-commands-and-properties).

Można zdefiniować własny makra na dwa sposoby:
-   Ustaw zmienne środowiskowe w wierszu polecenia dewelopera. Wszystkie zmienne środowiskowe są traktowane jako MSBuild właściwości/makra.
-   Definiowanie makr użytkownika w pliku .props. Aby uzyskać więcej informacji, zobacz [makra strony właściwości](working-with-project-properties.md#bkmkPropertiesVersusMacros). 

Aby uzyskać więcej informacji, zobacz wpisy na blogu: [katalogi VC ++](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx), [właściwości dziedziczone i arkusze właściwości](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx), i [programu Visual Studio 2010 C++ projektu przewodnik uaktualniania](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx).  
  
## <a name="directory-types"></a>Typy katalogów

Można również określić inne katalogi, jak poniżej.  
  
**Katalogi plików wykonywalnych**<br/>
Katalogi, w których należy szukać plików wykonywalnych. Odpowiada **ścieżki** zmiennej środowiskowej.

**Dołącz katalogi**<br/>
Katalogi, w których należy szukać dołączanych plików, do których istnieją odwołania w kodzie źródłowym. Odpowiada **INCLUDE** zmiennej środowiskowej.

**Odwołanie do katalogów**<br/>
 Katalogi wyszukiwania zestawów i modułów (metadanymi) pliki, których istnieją odwołania w kodzie źródłowym przez [#using](../preprocessor/hash-using-directive-cpp.md) dyrektywy. Odpowiada **LIBPATH** zmiennej środowiskowej.

**Katalogi bibliotek**<br/>
Katalogi, w których należy szukać plików biblioteki (.lib); obejmują biblioteki wykonywalne. Odpowiada **LIB** zmiennej środowiskowej. To ustawienie nie ma zastosowania do plików .obj; Aby utworzyć łącze do pliku .obj na **właściwości konfiguracji** > **konsolidatora** > **ogólne** strony właściwości, wybierz  **Dodatkowe zależności biblioteki** , a następnie określ ścieżkę względną pliku. Aby uzyskać więcej informacji, zobacz [strony właściwości konsolidatora](../ide/linker-property-pages.md).

**Katalogi bibliotek WinRT**<br/>
Katalogi wyszukiwania plików bibliotek WinRT do użycia w aplikacjach systemu Windows platformy Uniwersalnej. 

**Katalogi źródłowe**<br/>
Katalogi, w których należy szukać plików źródłowych dla technologii IntelliSense.

**Wyklucz katalogi**<br/>
Katalogi, których nie należy przeszukiwać podczas sprawdzania zależności kompilacji.

## <a name="sharing-the-settings"></a>Współdzielenie ustawień

Właściwości projektu można udostępniać innym użytkownikom lub na wielu komputerach. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).
