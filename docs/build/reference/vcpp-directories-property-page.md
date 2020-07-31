---
title: Strona właściwości katalogów VC++
ms.date: 07/17/2019
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
ms.openlocfilehash: 06e9508ae09f9c7581648b45098f497fda785013
ms.sourcegitcommit: 13f42c339fb7af935e3a93ac80e350d5e784c9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2020
ms.locfileid: "87470800"
---
# <a name="vc-directories-property-page-windows"></a>Strona właściwości katalogów VC + + (system Windows)

Ta strona właściwości służy do informowania programu Visual Studio o katalogach, które będą używane podczas kompilowania aktualnie wybranego projektu. Aby ustawić katalogi dla wielu projektów w rozwiązaniu, Użyj niestandardowego arkusza właściwości, zgodnie z opisem w temacie [udostępnianie lub ponowne użycie ustawień projektu programu Visual Studio C++](../create-reusable-property-configurations.md).

Aby uzyskać wersję systemu Linux na tej stronie, zobacz [Katalogi VC + + (Linux C++)](../../linux/prop-pages/directories-linux.md).

Aby uzyskać dostęp do strony właściwości **katalogów VC + +** :

1. Jeśli okno **Eksplorator rozwiązań** nie jest widoczne, w menu głównym wybierz polecenie **Wyświetl**  >  **Eksplorator rozwiązań**.
1. Kliknij prawym przyciskiem myszy węzeł projektu (nie rozwiązanie najwyższego poziomu) i wybierz polecenie **Właściwości**.
1. W lewym okienku okna dialogowego **strony właściwości** wybierz kolejno pozycje **Właściwości konfiguracji**  >  **Katalogi VC + +**.

Właściwości katalogów VC + + dotyczą projektu, a nie węzła rozwiązania najwyższego poziomu. Jeśli nie widzisz **katalogów VC + +** w obszarze **Właściwości konfiguracji**, wybierz węzeł projektu C++ w oknie **Eksplorator rozwiązań** :

![Wybierz węzeł projektu](../media/vcppdir.png "Wybierz węzeł projektu, aby wyświetlić właściwości katalogów VC + +")

Należy pamiętać, że strona właściwości **katalogów VC + +** dla projektów międzyplatformowych wygląda inaczej. Aby uzyskać informacje specyficzne dla projektów systemu Linux C++, zobacz [Katalogi VC + + (Linux C++)](../../linux/prop-pages/directories-linux.md).

Jeśli nie znasz *właściwości projektu* w programie Visual Studio, warto zapoznać się z tematem pierwsze odczytywanie [ustawienia kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

Ustawienia domyślne właściwości **katalogów VC + +** zależą od typu projektu. W przypadku projektów klasycznych obejmują lokalizacje narzędzi C++ dla określonego zestawu narzędzi platformy i lokalizacji Windows SDK. Zestaw **narzędzi platformy** i **wersję Windows SDK** można zmienić na stronie Ogólne **Właściwości konfiguracji**  >  **General** .

Aby wyświetlić wartości dla dowolnego katalogu:

1. Wybierz jedną z właściwości na stronie **katalogów VC + +** . Na przykład wybierz pozycję **katalogi bibliotek**.
1. Wybierz przycisk strzałki w dół na końcu pola wartość właściwości.
1. Z menu rozwijanego wybierz polecenie **Edytuj**.

![Edytuj katalogi biblioteki](../media/vcppdir_libdir_edit.png "Okno dialogowe edycji ścieżek biblioteki")

Zobaczysz teraz okno dialogowe podobne do tego:

![Pokaż katalogi bibliotek](../media/vcppdir_libdir.png "Okno dialogowe umożliwiające dodawanie lub usuwanie ścieżek biblioteki")

To okno dialogowe służy do wyświetlania bieżących katalogów. Jeśli jednak chcesz zmienić lub dodać katalog, lepiej jest użyć **Menedżer właściwości** , aby utworzyć arkusz właściwości, lub zmodyfikować domyślny arkusz właściwości użytkownika. Aby uzyskać więcej informacji, zobacz [udostępnianie lub ponowne używanie ustawień projektu programu Visual Studio C++](../create-reusable-property-configurations.md).

Jak pokazano powyżej, wiele dziedziczonych ścieżek jest podawanych jako makra.  Aby przejrzeć bieżącą wartość makra, wybierz przycisk **makra** w prawym dolnym rogu okna dialogowego. Należy zauważyć, że wiele makr zależy od typu konfiguracji. Makro w kompilacji debugowania może oszacować inną ścieżkę niż to samo makro w kompilacji wydania.

Możesz wyszukać częściowe lub kompletne dopasowania w polu edycji. Na poniższej ilustracji przedstawiono wszystkie makra, które zawierają ciąg "WindowsSDK", a także ścieżkę bieżącą, którą to makro daje:

![Wyświetlanie wartości makr](../media/vcppdir_libdir_macros.png "Okno dialogowe edytowania makr")

Uwaga: lista jest wypełniana podczas pisania. Nie naciskaj klawisza **Enter**.

Aby uzyskać więcej informacji na temat makr i przyczyn ich używania zamiast ścieżek zakodowanych w miarę możliwości, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

Listę często używanych makr można znaleźć [w temacie Common MACROS for Build Commands and Properties](common-macros-for-build-commands-and-properties.md).

Własne makra można definiować na dwa sposoby:

- Ustaw zmienne środowiskowe w wierszu polecenia dewelopera. Wszystkie zmienne środowiskowe są traktowane jako właściwości i makra programu MSBuild.

- Zdefiniuj makra użytkownika w pliku. props. Aby uzyskać więcej informacji, zobacz [makra strony właściwości](../working-with-project-properties.md).

Aby uzyskać więcej informacji, zobacz te wpisy w blogu: [Katalogi VC + +](https://docs.microsoft.com/archive/blogs/vsproject/vc-directories), [dziedziczone właściwości i arkusze właściwości](https://docs.microsoft.com/cpp/build/project-property-inheritance)oraz [Podręcznik uaktualniania projektu programu Visual Studio 2010 C++](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/).

## <a name="directory-types"></a>Typy katalogów

Można również określić inne katalogi, jak poniżej.

**Katalogi wykonywalne**<br/>
Katalogi, w których należy szukać plików wykonywalnych. Odpowiada zmiennej środowiskowej **Path** .

**Katalogi dołączania**<br/>
Katalogi, w których należy szukać dołączanych plików, do których istnieją odwołania w kodzie źródłowym. Odnosi się do zmiennej środowiskowej **include** .

**Katalogi odwołań**<br/>
Katalogi, w których mają być wyszukiwane pliki zestawów i modułów (metadane), które są przywoływane w kodzie źródłowym przez dyrektywę [#using](../../preprocessor/hash-using-directive-cpp.md) . Odnosi się do zmiennej środowiskowej **LIBPATH** .

**Katalogi bibliotek**<br/>
Katalogi, w których należy szukać plików biblioteki (.lib); obejmują biblioteki wykonywalne. Odpowiada zmiennej środowiskowej **lib** . To ustawienie nie ma zastosowania do plików. obj; Aby utworzyć link do pliku. obj, na **Configuration Properties**  >  stronie właściwości ogólne**konsolidatora**właściwości konfiguracji  >  **General** wybierz pozycję **dodatkowe zależności biblioteki** , a następnie określ ścieżkę względną pliku. Aby uzyskać więcej informacji, zobacz [strony właściwości konsolidatora](linker-property-pages.md).

**Katalogi WinRT**<br/>
Katalogi do wyszukiwania plików biblioteki WinRT do użycia w aplikacjach platforma uniwersalna systemu Windows (platformy UWP).

**Katalogi źródłowe**<br/>
Katalogi, w których należy szukać plików źródłowych dla technologii IntelliSense.

**Wyklucz katalogi**<br/>
Przed każdą kompilacją program Visual Studio wysyła zapytanie do sygnatury czasowej dla wszystkich plików, aby określić, czy którykolwiek z nich został zmodyfikowany od czasu poprzedniej kompilacji. Jeśli projekt ma duże stabilne biblioteki, można skrócić czas kompilacji, wykluczając te katalogi ze sprawdzenia sygnatury czasowej.

## <a name="sharing-the-settings"></a>Współdzielenie ustawień

Właściwości projektu można udostępniać innym użytkownikom lub na wielu komputerach. Aby uzyskać więcej informacji, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).
