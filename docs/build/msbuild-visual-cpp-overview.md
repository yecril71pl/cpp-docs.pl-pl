---
title: Przegląd MSBuild (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae6e6d826f4bc1e8c9ab6cc28686e4ad1e6e3b02
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379266"
---
# <a name="msbuild-visual-c-overview"></a>Informacje o MSBuild (Visual C++)  
  
MSBuild jest standardowego kompilacji systemu dla projektów Visual C++. Podczas tworzenia projektu w programie Visual Studio zintegrowane środowisko programistyczne (IDE) używa narzędzia msbuild.exe, pliku XML na podstawie projektu i opcjonalne ustawienia plików. Chociaż można używać msbuild.exe i plik projektu w wierszu polecenia, IDE udostępnia interfejs użytkownika, dzięki czemu można łatwiej skonfigurować ustawienia i kompilowania projektu. Ten przegląd zawiera opis używaniu systemu MSBuild Visual C++.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
Przeczytaj następujące dokumenty dotyczące programu MSBuild.  
  
- [MSBuild](/visualstudio/msbuild/msbuild)  
 Omówienie pojęć MSBuild.  
  
- [Odwołanie do narzędzia MSBuild](/visualstudio/msbuild/msbuild-reference)  
 Informacje o systemie MSBuild.  
  
- [Odwołanie do schematu pliku projektu](/visualstudio/msbuild/msbuild-project-file-schema-reference)  
 Wyświetla listę elementów schematu XML programu MSBuild, wraz z ich atrybuty i elementy nadrzędne i podrzędne. Należy zwrócić uwagę szczególnie [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild), [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild), [docelowej](/visualstudio/msbuild/target-element-msbuild), i [zadań](/visualstudio/msbuild/task-element-msbuild) elementów.  
  
- [Dokumentacja wiersza polecenia](/visualstudio/msbuild/msbuild-command-line-reference)  
 Opisano opcje używane z msbuild.exe i argumenty wiersza polecenia.  
  
- [Odwołanie do zadania](/visualstudio/msbuild/msbuild-task-reference)  
 W tym artykule opisano zadania programu MSBuild. Pamiętaj, zwłaszcza tych zadań, które są specyficzne dla Visual C++: [bscmake — zadanie](/visualstudio/msbuild/bscmake-task), [CL — zadanie](/visualstudio/msbuild/cl-task), [cppclean — zadanie](/visualstudio/msbuild/cppclean-task), [lib — zadanie](/visualstudio/msbuild/lib-task), [Połączyć zadanie](/visualstudio/msbuild/link-task), [midl — zadanie](/visualstudio/msbuild/midl-task), [MT — zadanie](/visualstudio/msbuild/mt-task), [RC — zadanie](/visualstudio/msbuild/rc-task), [SETENV — zadanie](/visualstudio/msbuild/setenv-task), [ Vcmessage — zadanie](/visualstudio/msbuild/vcmessage-task), [xdcmake — zadanie](/visualstudio/msbuild/xdcmake-task), [XSD — zadanie](/visualstudio/msbuild/xsd-task).  
  
## <a name="msbuild-on-the-command-line"></a>MSBuild w wierszu polecenia  
  
Następująca instrukcja z [dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) pokazano, że narzędzia msbuild.exe ma niejawne lub jawne *project_file* argumentu (plik .vcxproj dla projektów Visual C++) oraz zero lub więcej wiersza polecenia *opcje* argumentów.  
  
> **MSBUILD.exe** [ *project_file* ] [ *opcje* ]  
  
Użyj **/target** (lub **/t**) i **/property** (lub **/p**) opcje wiersza polecenia, aby zastąpić właściwości i elementów docelowych, które są określona w pliku projektu.  
  
Podstawowa funkcja pliku projektu jest określenie *docelowego*, który jest stosowany do projektu i danych wejściowych i wyjściowych, które są wymagane do wykonania tej operacji określonej operacji. Plik projektu można określić co najmniej jednego celu, obejmujące docelowy domyślne.  
  
Każdym obiekcie docelowym składa się z sekwencji jednego lub więcej *zadania*. Każde zadanie jest reprezentowany przez klasę .NET Framework, która zawiera jedno polecenie do pliku wykonywalnego. Na przykład [CL — zadanie](/visualstudio/msbuild/cl-task) zawiera [cl.exe](../build/reference/compiling-a-c-cpp-program.md) polecenia.  
  
A *parametru zadania* jest właściwością klasy zadania i zazwyczaj odpowiada opcji wiersza polecenia pliku wykonywalnego polecenia. Na przykład `FavorSizeOrSpeed` parametr `CL` zadania odpowiada **/OS** i **/Ot** — opcje kompilatora.  
  
Parametry dodatkowe zadania obsługuje infrastrukturę programu MSBuild. Na przykład `Sources` parametru zadania określa zbiór zadań, które mogą być używane przez inne zadania. Aby uzyskać więcej informacji na temat zadań programu MSBuild, zobacz [odwołanie do zadania](/visualstudio/msbuild/msbuild-task-reference).  
  
Większość zadań wymaga wejściach i wyjściach, takich jak nazwy pliku, ścieżki i ciąg, parametry liczbowych i logicznych. Na przykład typowe wejściowy jest nazwa pliku źródłowego .cpp do skompilowania. Parametr wejściowy ważne jest ciągiem, który określa konfigurację kompilacji i platformy, na przykład "Debug\|Win32". Wejścia i wyjścia są określane przez co najmniej jednego użytkownika XML `Item` elementów zawartych w `ItemGroup` elementu.  
  
Plik projektu można również określić użytkownika *właściwości* i `ItemDefinitionGroup` *elementów*. Właściwości i elementów formularza pary nazwa/wartość, które mogą być używane jako zmienne w kompilacji. Definiuje część nazwy pary *makro*, i deklaruje składnik wartości *wartość makra*. Makra właściwości uzyskuje się dostęp za pomocą $(*nazwa*) notacji i makra element jest dostępny za pomocą %(*nazwa*) notacji.  
  
Inne elementy XML w pliku projektu można przetestować makra, a następnie warunkowo wartość dowolne makro lub kontrolować wykonywanie kompilacji. Makra nazwy i ciągi literału może zostać dołączona do wygenerowania konstrukcje, takie jak nazwa i ścieżka pliku. W wierszu polecenia **/property** opcji ustawia lub przesłania właściwość projektu. Nie można przywołać elementów w wierszu polecenia.  
  
MSBuild system warunkowo może wykonać elementu docelowego przed lub po inny element docelowy. Ponadto system można tworzyć docelowy oparty na to, czy pliki, które korzysta z elementem docelowym są nowsze od plików, które go emituje.  
  
## <a name="msbuild-in-the-ide"></a>MSBuild w środowisku IDE  
  
Podczas ustawiania właściwości projektu w środowisku IDE, a następnie zapisz projekt Visual C++ zapisuje ustawienia projektu w pliku projektu. Plik projektu zawiera ustawienia, które są unikatowe dla projektu, ale nie zawiera wszystkie ustawienia, które są wymagane, aby skompilować projekt. Plik projektu zawiera `Import` elementów, które obejmują sieci dodatkowych *pliki pomocy technicznej.* Pliki obsługi zawierać pozostałe właściwości, cele i ustawienia, które są wymagane, aby skompilować projekt.  
  
Większość elementów docelowych i właściwości w plikach pomocy technicznej istnieje wyłącznie w celu wdrożenia systemu kompilacji. W poniższej sekcji omówiono niektóre przydatne cele i właściwości, które można określić w wierszu polecenia programu MSBuild. Aby dowiedzieć się więcej elementów docelowych i właściwości, Poznaj plików w katalogach plik pomocy technicznej.  
  
### <a name="support-file-directories"></a>Katalogi plików obsługi  
  
Domyślnie podstawowe pliki obsługi języka Visual C++ znajdują się w następujących katalogów. Katalogi w ramach programu Microsoft Visual Studio są używane przez Visual Studio 2017 i nowszych wersjach, a katalogi w ramach MSBuild są używane przez program Visual Studio 2015 i wcześniejsze wersje.  
  
|Katalog|Opis|  
|---------------|-----------------|  
|*dysk*: \Program Files *(x86)* \Microsoft Visual Studio\\*roku*\\*wersji*\Common7\IDE\VC\VCTargets\ <br /><br />*dysk*: \Program Files *(x86)* \v4.0 \MSBuild\Microsoft.Cpp (x86)\\*wersji*\ |Zawiera pliki docelowe głównej (.targets) i pliki właściwości (.props), które są używane przez elementy docelowe. Domyślnie makro $(VCTargetsPath) odwołuje się do tego katalogu.|  
|*dysk*: \Program Files *(x86)* \Microsoft Visual Studio\\*roku*\\*wersji*\Common7\IDE\VC\VCTargets\ Platformy\\*platformy*\ <br /><br />*dysk*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*wersji*\Platforms\\*platformy*\ |Zawiera pliki docelowy i właściwości specyficzne dla platformy, które zastępują elementy docelowe i właściwości w katalogu nadrzędnego. Ten katalog zawiera także biblioteki DLL, który definiuje zadania, które są używane przez elementy docelowe w tym katalogu.<br /><br /> *Platformy* symbol zastępczy reprezentuje x64 RAMIĘ lub Win32 podkatalogu.|  
|*dysk*: \Program Files *(x86)* \Microsoft Visual Studio\\*roku*\\*wersji*\Common7\IDE\VC\VCTargets\ Platformy\\*platformy*\PlatformToolsets\\*zestawu narzędzi*\ <br /><br />*dysk*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*wersji*\Platforms\\*platformy*\ PlatformToolsets\\*zestawu narzędzi*\ <br /><br />*dysk*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\Platforms\\*platformy*\PlatformToolsets\\*zestawu narzędzi*\ |Zawiera katalogi, umożliwiających kompilacji do generowania aplikacji Visual C++ przy użyciu określonego *zestawu narzędzi*.<br /><br /> *Roku* i *wersji* symbole zastępcze są używane przez program Visual Studio 2017 i późniejszych wersjach. *Wersji* symbol zastępczy jest V110 dla programu Visual Studio 2012, V120 dla programu Visual Studio 2013 lub Visual Studio 2015 w wersji 140. *Platformy* symbol zastępczy reprezentuje x64 RAMIĘ lub Win32 podkatalogu. *Zestawu narzędzi* symbol zastępczy reprezentuje podkatalogu zestawu narzędzi, na przykład w wersji 140 do tworzenia aplikacji systemu Windows za pomocą narzędzi Visual Studio 2015, v120_xp do kompilacji dla systemu Windows XP przy użyciu zestawu narzędzi programu Visual Studio 2013 lub v110_wp80 do Tworzenie aplikacji Windows Phone 8.0 przy użyciu zestawu narzędzi programu Visual Studio 2012.<br /><br />Ścieżkę zawierającą katalogów, umożliwiających kompilacji do generowania aplikacji Visual C++ 2008 lub Visual C++ 2010 nie zawiera *wersji*i *platformy* reprezentuje symbolu zastępczego x64 Itanium lub Win32 podkatalogu. *Zestawu narzędzi* podkatalogu zestawu narzędzi v90 lub v100 reprezentuje symbol zastępczy.|  
  
### <a name="support-files"></a>Pliki obsługi  
  
Katalogi plików pomocy technicznej zawiera pliki o następujących rozszerzeniach:  
  
|Rozszerzenia|Opis|  
|---------------|-----------------|  
|.TARGETS|Zawiera `Target` elementów XML, które określają zadania, które są wykonywane przez element docelowy. Może również zawierać `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup`, a zdefiniowane przez użytkownika `Item` elementów służących do przypisywania pliki i opcje wiersza polecenia do parametrów zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz [Target — Element (MSBuild)](/visualstudio/msbuild/target-element-msbuild).|  
|.props|Zawiera `Property Group` i zdefiniowanych przez użytkownika `Property` elementów XML, które określają ustawienia plików i parametrów, które są używane podczas kompilacji.<br /><br /> Może również zawierać `ItemDefinitionGroup` i zdefiniowanych przez użytkownika `Item` elementów XML, które określają dodatkowe ustawienia. Elementy zdefiniowane w grupie definicji elementu przypominają właściwości, ale nie ma dostępu z poziomu wiersza polecenia. Pliki projektu Visual C++ często używa elementów zamiast właściwości do reprezentowania ustawienia.<br /><br /> Aby uzyskać więcej informacji, zobacz [ItemGroup — Element (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), [ItemDefinitionGroup — Element (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild), i [Item — Element (MSBuild)](/visualstudio/msbuild/item-element-msbuild).|  
|.xml|Zawiera elementy XML, które deklaruje i zainicjuj elementy interfejsu użytkownika IDE, takich jak arkusze właściwości i strony właściwości i formantów pól tekstowych pole i listy.<br /><br /> Pliki .xml obsługuje bezpośrednio IDE, nie programu MSBuild. Jednak wartości właściwości IDE są przypisane do tworzenia właściwości i elementów.<br /><br /> Większość plików .xml znajdują się w podkatalogu specyficzne dla ustawień regionalnych. Na przykład pliki dla regionu Stanów Zjednoczonych angielski znajdują się w $(VCTargetsPath) \1033\\.|  
  
## <a name="user-targets-and-properties"></a>Cele użytkownika i właściwości  
  
Najbardziej efektywny sposób używania programu MSBuild w wierszu polecenia, pomaga ustalić, które właściwości i obiekty docelowe są i przydatności. Większość właściwości i elementów docelowych pomocy zaimplementować system kompilacji Visual C++, a w związku z tym nie są istotne dla użytkownika. W tej sekcji opisano niektóre zastanowić zorientowane na użytkownika właściwości i elementów docelowych.  

### <a name="platformtoolset-property"></a>Właściwość jest zestaw narzędzi platformy  
  
`PlatformToolset` Właściwość określa, które zestaw narzędzi Visual C++ jest używany podczas kompilacji. Domyślnie jest używany bieżący zestaw narzędzi. Gdy ta właściwość jest ustawiona, wartość właściwości jest połączony z literałów ciągów w ścieżce katalogu, który zawiera pliki właściwość i docelowych, które są wymagane do utworzenia projektu dla konkretnej platformy. Tworzenie za pomocą tej wersji narzędzi platformy musi być zainstalowany zestaw narzędzi platformy.  
  
Na przykład ustawić `PlatformToolset` właściwości `v140` używania narzędzi Visual C++ 2015 i biblioteki można skompilować aplikację:  
  
`msbuild myProject.vcxproj /p:PlatformToolset=v140`  
  
### <a name="preferredtoolarchitecture-property"></a>Właściwość PreferredToolArchitecture  
  
`PreferredToolArchitecture` Właściwość określa, czy kompilatora 32-bitowy lub 64-bitowe i narzędzia są używane w kompilacji. Ta właściwość nie ma wpływu na dane wyjściowe architektura platformy lub konfiguracji. Domyślnie program MSBuild używa x86 wersji kompilatora i narzędzi, jeśli ta właściwość nie jest ustawiona.  
  
Na przykład ustawić `PreferredToolArchitecture` właściwości `x64` używać kompilator 64-bitowy i narzędzia do tworzenia aplikacji:  
  
`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`  
  
### <a name="useenv-property"></a>Właściwość UseEnv  
  
Domyślnie ustawienia specyficzne dla platformy bieżący projekt musi zostać zastąpiona zmiennych środowiskowych PATH, INCLUDE LIB, LIBPATH, konfiguracji i platformy. Ustaw `UseEnv` właściwości `true` aby zagwarantować, że zmienne środowiskowe nie zostały zastąpione.  
  
`msbuild myProject.vcxproj /p:UseEnv=true`  
  
### <a name="targets"></a>Obiekty docelowe  
  
Brak setki obiektów docelowych w pliki obsługi programu Visual C++. Jednak większość to zorientowane na system obiektów docelowych, które użytkownik można zignorować. Większość elementów docelowych systemu są poprzedzone znaku podkreślenia (_) lub mieć nazwę, która rozpoczyna się od "PrepareFor", "Obliczeniowe", "Przed", "Po", "Przed" lub "Post".  
  
W poniższej tabeli wymieniono kilka przydatne cele zorientowane na użytkownika.  
  
|docelowy|Opis|  
|------------|-----------------|  
|BscMake|Wykonuje narzędzie przeglądać informacje o konserwacji narzędzie Microsoft bscmake.exe.|  
|Kompilacja|Kompiluje projekt.<br /><br /> Jest to domyślny obiekt docelowy dla projektu.|  
|ClCompile|Wykonuje narzędzie kompilatora Visual C++ cl.exe.|  
|Czyszczenie|Usuwa tymczasowy i pośredniego kompilacja plików.|  
|Lib|Narzędzie Microsoft 32-bitowy Library Manager wykonuje lib.exe.|  
|Łącze|Wykonuje narzędzia konsolidatora Visual C++ link.exe.|  
|ManifestResourceCompile|Pobiera listę zasobów z manifestu, a następnie wykonuje narzędzia kompilatora zasobów systemu Windows firmy Microsoft rc.exe.|  
|Midl|Wykonuje narzędzie kompilatora Microsoft interfejsu Definition Language (MIDL) midl.exe.|  
|Skompiluj ponownie|Czyści a potem kompiluje projektu.|  
|ResourceCompile|Wykonuje narzędzia kompilatora zasobów systemu Windows firmy Microsoft rc.exe.|  
|Xdcmake —|Wykonuje narzędzie dokumentacji XML xdcmake.exe.|  
|XSD|Wykonuje narzędzie definicji schematu XML xsd.exe.|  
  
## <a name="see-also"></a>Zobacz też  
  
[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
