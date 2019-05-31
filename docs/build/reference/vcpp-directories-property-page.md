---
title: Strona właściwości katalogów VC++
ms.date: 10/09/2018
f1_keywords:
- VC.Project.VCDirectories.IncludePath
- VC.Project.VCDirectories.ReferencePath
- VC.Project.VCDirectories.SourcePath
- VC.Project.VCDirectories.LibraryWPath
- VC.Project.VCDirectories.ExecutablePath
- VC.Project.VCDirectories.LibraryPath
- VS.ToolsOptionsPages.Projects.VCDirectories
- VC.Project.VCDirectories.ExcludePath
helpviewer_keywords:
- VC++ Directories Property Page
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
ms.openlocfilehash: e739ea99df424f44dc43a28e3dc01c3529bb0c1a
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450717"
---
# <a name="vc-directories-property-page-windows"></a>VC ++ Directories Property Page (Windows)

Użyj tej strony właściwości stwierdzić programu Visual Studio, które katalogi do użycia podczas tworzenia projektu aktualnie wybrany. Aby ustawić katalogi dla wielu projektów w rozwiązaniu, użyj arkusza właściwości niestandardowej, zgodnie z opisem w [udziału lub resuse ustawienia projektu Visual Studio C++](../create-reusable-property-configurations.md).

Wersja systemu Linux na tej stronie, zobacz [katalogi VC ++ (Linux C++)](../../linux/prop-pages/directories-linux.md).

Aby uzyskać dostęp do **katalogi VC ++** strona właściwości:

1. Jeśli **Eksploratora rozwiązań** okno nie jest widoczne, następnie w menu głównym wybierz **widoku** > **Eksploratora rozwiązań**.
1. Kliknij prawym przyciskiem myszy węzeł projektu (nie rozwiązanie najwyższego poziomu) i wybierz polecenie **właściwości**.
1. W okienku po lewej stronie **stron właściwości** okno dialogowe, wybierz opcję **właściwości konfiguracji** > **katalogi VC ++** .

Katalogi VC ++ właściwości mają zastosowanie do projektu, nie węzła najwyższego poziomu rozwiązania. Jeśli nie widzisz **katalogi VC ++** w obszarze **właściwości konfiguracji**, wybierz węzeł projektu C++ w **Eksploratora rozwiązań** okna:

![Wybierz węzeł projektu](../media/vcppdir.png "wybierz węzeł projektu, aby wyświetlić właściwości katalogów VC ++")

Należy pamiętać, że **katalogi VC ++** strony właściwości dla projektów dla wielu platform wygląda inaczej. Aby uzyskać informacje specyficzne dla projektów języka Linux C++, zobacz [katalogi VC ++ (Linux C++)](../../linux/prop-pages/directories-linux.md).

Jeśli nie jesteś zaznajomiony z *właściwości projektu* w programie Visual Studio, może okazać się przydatne do odczytu pierwszy [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

Domyślne ustawienia dla **katalogi VC ++** właściwości zależą od typu projektu. Projekty pulpitu zawierają lokalizacje narzędzi języka C++ dla określonego zestawu narzędzi platformy i lokalizacji zestawu Windows SDK. Możesz zmienić **zestawu narzędzi platformy** i **wersja zestawu Windows SDK** na **właściwości konfiguracji** > **ogólne** Strona.

Aby wyświetlić wartości na żadnym z katalogów:

1. Wybierz jedną z właściwości w **katalogi VC ++** strony. Na przykład wybrać **katalogi bibliotek**.
1. Wybierz przycisk strzałki w dół na końcu pola wartości właściwości.
1. W menu rozwijanym wybierz **Edytuj**.

![Edytuj katalogi bibliotek](../media/vcppdir_libdir_edit.png "okno dialogowe Edytowanie ścieżki biblioteki")

Teraz pojawi się okno dialogowe następująco:

![Pokaż katalogi bibliotek](../media/vcppdir_libdir.png "okno dialogowe Dodawanie lub usuwanie ścieżki biblioteki")

Użyj tego okna dialogowego, aby wyświetlić bieżący katalog. Jednakże, jeśli chcesz zmienić lub dodać katalog go lepiej jest używać **Menedżer właściwości** utworzyć arkusz właściwości lub zmodyfikować domyślny arkusz właściwości użytkownika. Aby uzyskać więcej informacji, zobacz [udziału lub resuse ustawienia projektu Visual Studio C++](../create-reusable-property-configurations.md).

Jak wspomniano powyżej, jest wiele ścieżek dziedziczone wyrażonych za pomocą makra.  Aby zbadać bieżącą wartość makra, wybierz opcję **makra** przycisk w prawym dolnym rogu okna dialogowego. Należy pamiętać, że wiele makra są zależne od typu konfiguracji. Makra w kompilacji debugowania może zwrócić z inną ścieżką niż sam makra w kompilacji wydania.

Możesz wyszukać częściowe lub całkowite dopasowań w polu edycji. Na poniższej ilustracji przedstawiono wszystkie makra, które zawierają ciąg "WindowsSDK" i zawiera również bieżącą ścieżkę, która daje w wyniku makra:

![Zobacz makra wartości](../media/vcppdir_libdir_macros.png "okno dialogowe, aby edytować makra")

Uwaga: Lista jest wypełniana podczas wpisywania. Nie naciśnij **Enter**.

Aby uzyskać więcej informacji na temat makr i dlaczego należy ich używać zamiast zakodowanych ścieżek, jeśli to możliwe, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

Aby uzyskać listę często używanych makr, zobacz [typowe makra dla kompilacji polecenia i właściwości](common-macros-for-build-commands-and-properties.md).

Można zdefiniować własne makra na dwa sposoby:

- Ustawianie zmiennych środowiskowych w wierszu polecenia dla deweloperów. Wszystkie zmienne środowiskowe są traktowane jako makra i właściwości programu MSBuild.

- Definiowanie makr użytkownika w pliku .props. Aby uzyskać więcej informacji, zobacz [makra strony właściwości](../working-with-project-properties.md).

Aby uzyskać więcej informacji zobacz te Posty na blogu: [Katalogi VC ++](https://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx), [dziedziczone właściwości i arkusze właściwości](https://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx), i [Visual Studio 2010 C++ projektu Podręczniku uaktualniania programu](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/).

## <a name="directory-types"></a>Typy katalogów

Można również określić inne katalogi, jak poniżej.

**Katalogi plików wykonywalnych**<br/>
Katalogi, w których należy szukać plików wykonywalnych. Odnosi się do **ścieżki** zmiennej środowiskowej.

**Katalogi plików nagłówkowych**<br/>
Katalogi, w których należy szukać dołączanych plików, do których istnieją odwołania w kodzie źródłowym. Odnosi się do **INCLUDE** zmiennej środowiskowej.

**Katalogi odwołań**<br/>
Katalogi, w których należy szukać zestawów i pliki modułów (metadane), które są określone w kodzie źródłowym, [#using](../../preprocessor/hash-using-directive-cpp.md) dyrektywy. Odnosi się do **LIBPATH** zmiennej środowiskowej.

**Katalogi bibliotek**<br/>
Katalogi, w których należy szukać plików biblioteki (.lib); obejmują biblioteki wykonywalne. Odnosi się do **LIB** zmiennej środowiskowej. To ustawienie nie ma zastosowania do plików .obj; Aby utworzyć łącze do pliku .obj, na **właściwości konfiguracji** > **konsolidatora** > **ogólne** strony właściwości, wybierz opcję  **Dodatkowe zależności biblioteki** , a następnie określ względną ścieżkę pliku. Aby uzyskać więcej informacji, zobacz [strony właściwości konsolidatora](linker-property-pages.md).

**Katalogi WinRT biblioteki**<br/>
Katalogi do wyszukiwania plików bibliotek WinRT do wykorzystania w aplikacjach platformy uniwersalnej Windows (UWP).

**Katalogi źródłowe**<br/>
Katalogi, w których należy szukać plików źródłowych dla technologii IntelliSense.

**Wyklucz katalogi**<br/>
Przed każdym kompilacji programu Visual Studio wysyła zapytanie do sygnatury czasowej na wszystkie pliki w celu określenia, czy dowolne zostały zmienione od poprzedniej kompilacji. Jeżeli projekt zawiera duże biblioteki stabilny, możesz potencjalnie przyspieszyć czasy kompilacji poprzez wykluczenie tych katalogów z wyboru sygnatury czasowej.

## <a name="sharing-the-settings"></a>Współdzielenie ustawień

Właściwości projektu można udostępniać innym użytkownikom lub na wielu komputerach. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).
