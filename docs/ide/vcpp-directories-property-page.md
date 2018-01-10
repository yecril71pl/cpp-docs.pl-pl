---
title: "Strona właściwości katalogów VC ++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
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
dev_langs: C++
helpviewer_keywords: VC++ Directories Property Page
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2c92a97ccd28a1bc7d1fae518cf499b45d339dae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="vc-directories-property-page-windows"></a>VC ++ strona właściwości katalogów (system Windows)

Użyj tej strony właściwości stwierdzić, które katalogi do użycia podczas tworzenia aktualnie wybrany projekt programu Visual Studio. Aby ustawić katalogów dla wielu projektów w rozwiązaniu, użyj arkusza właściwości niestandardowej, zgodnie z opisem w [tworzenia konfiguracji wielokrotnego użytku właściwości](working-with-project-properties.md#bkmkPropertySheets).

Dla wersji systemu Linux na tej stronie, zobacz [katalogi VC ++ (Linux C++)](../linux/prop-pages/directories-linux.md).   

Aby uzyskać dostęp do **katalogi VC ++** strony właściwości:

1. w menu głównym wybierz **widok | Eksplorator rozwiązań**
1. Kliknij prawym przyciskiem myszy węzeł projektu (nie rozwiązanie najwyższego poziomu) i wybierz polecenie **właściwości**
1. w lewym okienku **strony właściwości** okna dialogowego rozwiń **właściwości konfiguracji** i wybierz **katalogi VC ++**.  

Właściwości katalogi VC ++ odnoszą się do projektu, nie węzła najwyższego poziomu rozwiązania:

![Wybierz węzeł projektu](media/vcppdir.png "wybierz węzeł projektu, aby wyświetlić właściwości katalogów VC ++")

Jeśli widzisz stronę właściwości, upewnij się, masz węzła projektu wybrany w **Eksploratora rozwiązań**. Należy pamiętać, że **katalogi VC ++** strony właściwości dla projektów i platform wygląda inaczej. Dla projektów z systemem innym niż Windows, temacie [katalogi VC ++ (Linux C++)](../linux/prop-pages/directories-linux.md) lub. 
 
Jeśli nie masz doświadczenia z *właściwości projektu* w programie Visual Studio, może być przydatne do odczytu pierwszego [Praca z właściwościami projektu](working-with-project-properties.md). 
 
Ustawienia domyślne katalogi VC ++ są zależne od typu projektu. Dla projektów pulpitu obejmują one lokalizacje narzędzi VC ++ dla określonego zestawu narzędzi platformy i lokalizacji zestawu Windows SDK. Możesz zmienić **zestaw narzędzi platformy** i **wersji zestawu Windows SDK** na **właściwości konfiguracji — ogólne** strony. Aby wyświetlić wartości na żadnym z katalogów:

1. w prawym okienku **katalogi VC ++** wybierz wiersz. Na przykład **katalogi bibliotek**
1. Kliknij przycisk strzałki w dół na prawo
1. Wybierz **Edytuj**.

![Edytuj katalogi bibliotek](media/vcppdir_libdir_edit.png "okna dialogowego, aby edytować ścieżki biblioteki")

Pojawi się okno dialogowe następująco: 

![Pokaż katalogi bibliotek](media/vcppdir_libdir.png "okna dialogowego, aby dodać lub usunąć ścieżki biblioteki")

To okno dialogowe służy do wyświetlenia bieżącego katalogów. Jednak jeśli chcesz zmienić lub dodać katalog jest lepiej jest użyć **Menedżer właściwości** Aby utworzyć arkusz właściwości lub zmodyfikować domyślny arkusz właściwości użytkownika. Aby uzyskać więcej informacji, zobacz [tworzenia konfiguracji wielokrotnego użytku właściwości](working-with-project-properties.md#bkmkPropertySheets).

Jak pokazano powyżej, podano wiele ścieżek dziedziczone jako makr.  Aby sprawdzić bieżącą wartość makra, wybierz **makra** przycisk w prawym dolnym rogu okna dialogowego. Należy pamiętać, że wiele makra są zależne od typu konfiguracji. Makra kompilacji debugowania może zwrócić z inną ścieżką niż sam makra w kompilacji wydania. 

Można wyszukiwać dopasowania częściowej lub pełnej w polu edycji. Na poniższej ilustracji przedstawiono wszystkie makra zawierające ciąg "WindowsSDK", a także pokazanie bieżącej ścieżki, która daje w wyniku makra:

![Zobacz wartości makra](media/vcppdir_libdir_macros.png "okna dialogowego, aby edytować makra")

Uwaga: Listy są powielane podczas pisania. Nie naciśnij **Enter**.

Aby uzyskać więcej informacji na temat makr i dlaczego należy ich używać zamiast ustalony ścieżek, jeśli to możliwe, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md#bkmkPropertiesVersusMacros). 

Lista często używane makra, zobacz [wspólnej makra dla poleceń kompilacji oraz właściwości](https://docs.microsoft.com/en-us/cpp/ide/common-macros-for-build-commands-and-properties).

Można zdefiniować własny makra na dwa sposoby:
-   Ustaw zmienne środowiskowe w wierszu polecenia dewelopera. Wszystkie zmienne środowiskowe są traktowane jako MSBuild właściwości/makra.
-   Definiowanie makr użytkownika w pliku .props. Aby uzyskać więcej informacji, zobacz [makra strony właściwości](working-with-project-properties.md#bkmkPropertiesVersusMacros). 

Aby uzyskać więcej informacji, zobacz wpisy na blogu: [katalogi VC ++](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx), [właściwości dziedziczone i arkusze właściwości](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx), i [programu Visual Studio 2010 C++ projektu przewodnik uaktualniania](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx).  
  
## <a name="directory-types"></a>Typy katalogów

Można również określić inne katalogi, jak poniżej.  
  
**Katalogi plików wykonywalnych**  
Katalogi, w których należy szukać plików wykonywalnych. Odpowiada **ścieżki** zmiennej środowiskowej.

**Dołącz katalogi**  
Katalogi, w których należy szukać dołączanych plików, do których istnieją odwołania w kodzie źródłowym. Odpowiada **INCLUDE** zmiennej środowiskowej.

**Odwołanie do katalogów**  
 Katalogi wyszukiwania zestawów i modułów (metadanymi) pliki, których istnieją odwołania w kodzie źródłowym przez [#using](../preprocessor/hash-using-directive-cpp.md) dyrektywy. Odpowiada **LIBPATH** zmiennej środowiskowej.

**Katalogi bibliotek**  
Katalogi, w których należy szukać plików biblioteki (.lib); obejmują biblioteki wykonywalne. Odpowiada **LIB** zmiennej środowiskowej. To ustawienie nie ma zastosowania do plików .obj; Aby utworzyć łącze do pliku .obj na [konsolidatora](../ide/linker-property-pages.md)**ogólne** strony właściwości, wybierz opcję **dodatkowe zależności biblioteki** , a następnie określ ścieżkę względną pliku.

**Katalogi źródłowe**  
Katalogi, w których należy szukać plików źródłowych dla technologii IntelliSense.

**Wyklucz katalogi**  
Katalogi, których nie należy przeszukiwać podczas sprawdzania zależności kompilacji.

## <a name="sharing-the-settings"></a>Współdzielenie ustawień

Właściwości projektu można udostępniać innym użytkownikom lub na wielu komputerach. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).
