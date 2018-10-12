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
ms.openlocfilehash: 9c337ec94f863e6c19851bcf962db61f277491cf
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163247"
---
# <a name="msbuild-visual-c-overview"></a>Informacje o MSBuild (Visual C++)

Program MSBuild jest standardowym systemem kompilacji dla projektów Visual C++. Podczas tworzenia projektu w programie Visual Studio zintegrowane środowisko programistyczne (IDE) korzysta z narzędzia msbuild.exe, pliku projektu opartego na języku XML i plików ustawień opcjonalnych. Mimo że można użyć msbuild.exe i pliku projektu w wierszu polecenia, IDE udostępnia interfejs użytkownika, aby można było łatwiej skonfigurować ustawienia i tworzyć projekt. W tym omówieniu opisano, jak Visual C++ korzysta z systemu MSBuild.

## <a name="prerequisites"></a>Wymagania wstępne

Przeczytaj następujące dokumenty dotyczące programu MSBuild.

- [Program MSBuild](/visualstudio/msbuild/msbuild) pojęcia dotyczące Omówienie programu MSBuild.

- [Odwołanie do MSBuild](/visualstudio/msbuild/msbuild-reference) informacje referencyjne o systemu MSBuild.

- [Odwołanie do schematu pliku projektu](/visualstudio/msbuild/msbuild-project-file-schema-reference) Wyświetla listę elementów schematu XML środowiska MSBuild, wraz z ich atrybutami oraz elementami nadrzędnymi i podrzędnymi. Należy zwrócić szczególną uwagę [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild), [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild), [docelowej](/visualstudio/msbuild/target-element-msbuild), i [zadań](/visualstudio/msbuild/task-element-msbuild) elementów.

- [Informacje dotyczące wiersza polecenia](/visualstudio/msbuild/msbuild-command-line-reference) opisano argumenty wiersza polecenia i opcje, których można używać z msbuild.exe.

- [Zadania, odwołanie](/visualstudio/msbuild/msbuild-task-reference) zadania w tym artykule opisano programu MSBuild. Należy zwrócić szczególną uwagę te zadania, które są specyficzne dla języka Visual C++: [bscmake — zadanie](/visualstudio/msbuild/bscmake-task), [cl — zadanie](/visualstudio/msbuild/cl-task), [cppclean — zadanie](/visualstudio/msbuild/cppclean-task), [lib — zadanie](/visualstudio/msbuild/lib-task), [Połączyć zadanie](/visualstudio/msbuild/link-task), [MIDL — zadanie](/visualstudio/msbuild/midl-task), [MT — zadanie](/visualstudio/msbuild/mt-task), [RC — zadanie](/visualstudio/msbuild/rc-task), [SETENV — zadanie](/visualstudio/msbuild/setenv-task), [ Vcmessage — zadanie](/visualstudio/msbuild/vcmessage-task), [xdcmake — zadanie](/visualstudio/msbuild/xdcmake-task), [XSD — zadanie](/visualstudio/msbuild/xsd-task).

## <a name="msbuild-on-the-command-line"></a>Program MSBuild w wierszu polecenia

Poniższa instrukcja z [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) ilustruje, że narzędzie msbuild.exe trwa niejawny lub jawny *project_file* argumentu (plik .vcxproj dla projektów Visual C++) oraz zero lub więcej wierszy polecenia *opcje* argumentów.

> **MSBUILD.exe** [ *project_file* ] [ *opcje* ]

Użyj **/target** (lub **/t**) i **/property** (lub **/p**) opcje wiersza polecenia, aby zastąpić określonych właściwości i elementy docelowe, które są określona w pliku projektu.

Podstawową funkcją pliku projektu jest zdefiniowanie *docelowej*, który jest określoną operacją stosowaną do projektu oraz wejść i wyjść, które są wymagane do wykonania tej operacji. Plik projektu można określić jeden lub więcej obiektów docelowych, które mogą zawierać domyślny adres docelowy.

Każdego obiektu docelowego, który składa się z sekwencji jednego lub więcej *zadania*. Każde zadanie jest reprezentowane przez klasę .NET Framework, która zawiera polecenia pliku wykonywalnego. Na przykład [cl — zadanie](/visualstudio/msbuild/cl-task) zawiera [cl.exe](../build/reference/compiling-a-c-cpp-program.md) polecenia.

A *parametru zadania* jest właściwością zadania klasy i zazwyczaj reprezentuje opcję wiersza polecenia dla polecenia pliku wykonywalnego. Na przykład `FavorSizeOrSpeed` parametru `CL` zadania odpowiada **/Os** i **/Ot** opcje kompilatora.

Parametry dodatkowe zadania obsługuje infrastrukturę programu MSBuild. Na przykład `Sources` zadań parametr określa zestaw zadań, które mogą być wykorzystane przez inne zadania. Aby uzyskać więcej informacji na temat zadań MSBuild, zobacz [odwołanie do zadania](/visualstudio/msbuild/msbuild-task-reference).

Większość zadań wymaga danych wejściowych i wyjściowych, takich jak nazwy plików, ścieżek i ciąg parametrów liczbowych lub logicznych. Na przykład typowymi danymi wejściowymi jest nazwa pliku źródłowego .cpp do skompilowania. Ważny parametr wejściowy jest ciągiem, który określa konfigurację kompilacji i platformy, na przykład "debugowanie\|Win32". Dane wejściowe i wyjściowe są określane przez co najmniej jeden XML zdefiniowane przez użytkownika `Item` elementów zawartych w słowniku `ItemGroup` elementu.

Plik projektu można również określić użytkownika *właściwości* i `ItemDefinitionGroup` *elementów*. Właściwości i elementy tworzą pary nazwa/wartość, które mogą być używane jako zmienne w kompilacji. Składnik nazwy pary definiuje *— makro*, a składnik wartości deklaruje *wartość makra*. Makro właściwości jest dostępne przy użyciu składni $(*nazwa*) notacją i makro elementu odbywa się za pomocą %(*nazwa*) notacji.

Inne elementy XML w pliku projektu mogą testować makra, a następnie warunkowo wartość każdego makra lub kontrolować wykonywanie kompilacji. Nazwy makr i ciągi literałowe mogą zostać łączone w celu generowania konstrukcji, takich jak ścieżka i nazwa pliku. W wierszu polecenia **/property** opcji ustawia lub zastępuje właściwość projektu. Nie można odwoływać się do elementów w wierszu polecenia.

MSBuild system warunkowo może wykonać element docelowy, przed lub po innym elementem docelowym. Ponadto system można zbudować obiekt docelowy oparty na to, czy pliki, które zużywa docelowej są nowsze niż pliki, które on emituje.

## <a name="msbuild-in-the-ide"></a>Program MSBuild w środowisku IDE

Podczas ustawiania właściwości projektu w środowisku IDE, a następnie zapisujesz projekt, Visual C++ zapisuje ustawienia projektu do pliku projektu. Plik projektu zawiera ustawienia, które są unikatowe dla projektu, ale nie zawiera wszystkich ustawień, które są wymagane do kompilowania projektu. Plik projektu zawiera `Import` elementy, które zawierają sieć dodatkowych *plików obsługi.* Pliki obsługi zawierają pozostałe właściwości, cele i ustawienia, które są wymagane do skompilowania projektu.

Większość obiektów docelowych i właściwości w plikach pomocy technicznej istnieje wyłącznie w celu implementowania systemu kompilacji. W poniższej sekcji omówiono niektóre użyteczne cele i właściwości, które można określić w wierszu polecenia programu MSBuild. Aby dowiedzieć się więcej obiektów docelowych i właściwości, Eksploruj pliki w katalogach plików pomocy technicznej.

### <a name="support-file-directories"></a>Obsługa katalogów plików

Domyślnie pliki obsługi podstawowego języka Visual C++ znajdują się w następujących katalogach. Katalogi w ramach programu Microsoft Visual Studio są używane przez program Visual Studio 2017 i nowsze wersje, katalogi w ramach programu MSBuild są używane przez program Visual Studio 2015 i wcześniejszych wersji.

|Katalog|Opis|
|---------------|-----------------|
|*dysk*: \Program Files *(x86)* \Microsoft Visual Studio\\*roku*\\*wersji*\Common7\IDE\VC\VCTargets\ <br /><br />*dysk*: \Program Files *(x86)* \v4.0 \MSBuild\Microsoft.Cpp (x86)\\*wersji*\ |Zawiera podstawowe pliki docelowe (.targets) i pliki właściwości (.props), które są używane przez elementy docelowe. Domyślnie makro $(VCTargetsPath) odwołuje się do tego katalogu.|
|*dysk*: \Program Files *(x86)* \Microsoft Visual Studio\\*roku*\\*wersji*\Common7\IDE\VC\VCTargets\ Platform\\*platformy*\ <br /><br />*dysk*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*wersji*\Platforms\\*platformy*\ |Zawiera pliki docelowych i właściwości specyficzne dla platformy, które zastępują cele i właściwości w katalogu nadrzędnym. Ten katalog zawiera również biblioteki DLL, który określa zadania, które są używane przez cele w tym katalogu.<br /><br /> *Platformy* symbol zastępczy reprezentuje ARM, Win32 lub x64 podkatalogu.|
|*dysk*: \Program Files *(x86)* \Microsoft Visual Studio\\*roku*\\*wersji*\Common7\IDE\VC\VCTargets\ Platform\\*platformy*\PlatformToolsets\\*zestawu narzędzi*\ <br /><br />*dysk*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*wersji*\Platforms\\*platformy*\ PlatformToolsets\\*zestawu narzędzi*\ <br /><br />*dysk*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\Platforms\\*platformy*\PlatformToolsets\\*zestawu narzędzi*\ |Zawiera katalogi, które umożliwiają kompilacji wygenerowanie aplikacji Visual C++ przy użyciu określonego *narzędzi*.<br /><br /> *Roku* i *wersji* symbole zastępcze są używane przez program Visual Studio 2017 i nowsze wersje. *Wersji* symbol zastępczy jest V110 dla programu Visual Studio 2012, V120 dla programu Visual Studio 2013 lub Visual Studio 2015 w wersji 140. *Platformy* symbol zastępczy reprezentuje ARM, Win32 lub x64 podkatalogu. *Narzędzi* symbol zastępczy reprezentuje podkatalog zestawu narzędzi, na przykład w wersji 140 do tworzenia aplikacji Windows przy użyciu zestawu narzędzi programu Visual Studio 2015 v120_xp tworzenie dla Windows XP przy użyciu zestawu narzędzi Visual Studio 2013 lub v110_wp80 do Twórz aplikacje Windows Phone 8.0 przy użyciu zestawu narzędzi programu Visual Studio 2012.<br /><br />Ścieżką, która zawiera katalogi, które umożliwiają kompilacji wygenerowanie aplikacji Visual C++ 2008 lub Visual C++ 2010 nie obejmuje *wersji*i *platformy* reprezentuje symbol zastępczy Itanium, Win32 lub x64 podkatalogu. *Narzędzi* symbol zastępczy reprezentuje podkatalog zestawu narzędzi v90 lub v100.|

### <a name="support-files"></a>Pliki pomocy technicznej

Katalogi plików obsługi zawierają pliki z tymi rozszerzeniami:

|Rozszerzenie|Opis|
|---------------|-----------------|
|.TARGETS|Zawiera `Target` elementów XML, które określają zadania, które są wykonywane przez element docelowy. Może również zawierać `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup`i zdefiniowane przez użytkownika `Item` elementy, które są używane do przypisywania plików i opcji wiersza polecenia do parametrów zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz [Target — Element (MSBuild)](/visualstudio/msbuild/target-element-msbuild).|
|.props|Zawiera `Property Group` i zdefiniowane przez użytkownika `Property` elementów XML, które określają ustawienia plików i parametrów, które są używane podczas kompilacji.<br /><br /> Może również zawierać `ItemDefinitionGroup` i zdefiniowane przez użytkownika `Item` elementów XML, które określają dodatkowe ustawienia. Elementy zdefiniowane w grupie definicji elementów przypominają właściwości, ale nie są dostępne z poziomu wiersza polecenia. Pliki projektu Visual C++ często używają elementów zamiast właściwości do reprezentowania ustawień.<br /><br /> Aby uzyskać więcej informacji, zobacz [itemgroup — Element (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), [ItemDefinitionGroup — Element (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild), i [Item — Element (MSBuild)](/visualstudio/msbuild/item-element-msbuild).|
|.xml|Zawiera elementy XML, które deklaruje i inicjuje elementy interfejsu użytkownika IDE, takie jak arkusze właściwości i strony właściwości i tekstu pola i formanty pola listy.<br /><br /> Pliki .xml bezpośrednio obsługują IDE, nie MSBuild. Jednak wartości właściwości środowiska IDE są przypisywane do właściwości i elementów kompilacji.<br /><br /> Większość plików .XML znajduje się w podkatalogu specyficzne dla ustawień regionalnych. Na przykład pliki dla regionu Angielski-Stany Zjednoczone znajdują się w $(VCTargetsPath) \1033\\.|

## <a name="user-targets-and-properties"></a>Cele i właściwości użytkownika

Za pomocą najbardziej efektywne programu MSBuild w wierszu polecenia, warto wiedzieć, które właściwości i elementy docelowe są przydatne i istotne. Większość właściwości i obiektów docelowych ułatwia implementację systemu kompilacji Visual C++, a w związku z tym nie mają znaczenia dla użytkownika. W tej sekcji opisano niektóre zorientowane ukierunkowanych na użytkownika właściwości i obiektów docelowych.

### <a name="platformtoolset-property"></a>Właściwość PlatformToolset

`PlatformToolset` Właściwość określa, który zestaw narzędzi Visual C++ jest używany w kompilacji. Domyślnie używany jest bieżący zestaw narzędzi. Gdy ta właściwość jest ustawiona, wartość właściwości jest połączona z ciągami tekstowymi ścieżkę katalogu, zawierającego pliki właściwości i docelowych, które są wymagane do utworzenia projektu dla konkretnej platformy. Tworzenie za pomocą tej wersji zestawu narzędzi platformy można zainstalować zestawu narzędzi platformy.

Na przykład ustawić `PlatformToolset` właściwość `v140` używać bibliotek i narzędzi Visual C++ 2015 do budowania aplikacji:

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>Właściwość PreferredToolArchitecture

`PreferredToolArchitecture` Właściwość określa, czy 32-bitową lub 64-bitowy kompilator i narzędzia są używane w kompilacji. Właściwość ta nie wpływa na konfigurację ani architekturę platformy wyjściowej. Domyślnie MSBuild używa x86 wersję kompilatora i narzędzi, jeśli ta właściwość nie jest ustawiona.

Na przykład ustawić `PreferredToolArchitecture` właściwość `x64` używać 64-bitowego kompilatora i narzędzi do budowania aplikacji:

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>Właściwość UseEnv

Domyślnie ustawienia specyficzne dla platformy dla bieżącego projektu zastępują zmienne środowiskowe PATH, INCLUDE, LIB, LIBPATH, Konfiguracja i PLATFORMA. Ustaw `UseEnv` właściwości **true** celu zagwarantowania, że zmienne środowiskowe nie są zastępowane.

`msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>Obiekty docelowe

Istnieją setki obiektów docelowych w plikach obsługi języka Visual C++. Jednak większość to cele systemowe, które użytkownik może ignorować. Większość obiektów docelowych systemów jest poprzedzonych znakiem podkreślenia (_) lub mają nazwę, która zaczyna się od "PrepareFor", "Compute", "Before", "After", "Pre" lub "Post".

W poniższej tabeli wymieniono kilka przydatne celów ukierunkowanych na użytkownika.

|Docelowy|Opis|
|------------|-----------------|
|BscMake|Uruchamia narzędzie przeglądać informacje o konserwacji narzędzie Microsoft bscmake.exe.|
|Kompilacja|Kompiluje projekt.<br /><br /> Jest to domyślny cel dla projektu.|
|ClCompile|Uruchamia narzędzie kompilatora Visual C++ cl.exe.|
|czyszczenie|Usuwa tymczasowe i pośrednie pliki kompilacji.|
|lib|Uruchamia narzędzie Microsoft 32-bitowy Library Manager, lib.exe.|
|Łącze|Uruchamia narzędzie konsolidatora Visual C++ link.exe.|
|ManifestResourceCompile|Wyodrębnia listę zasobów z manifestu, a następnie uruchamia narzędzie kompilatora zasobów systemu Microsoft Windows rc.exe.|
|Midl|Uruchamia narzędzie kompilatora języka definicji interfejsu Microsoft (MIDL) midl.exe.|
|Ponowna kompilacja|Czyści, a następnie kompiluje projekt.|
|ResourceCompile|Uruchamia narzędzie kompilatora zasobów systemu Microsoft Windows rc.exe.|
|Xdcmake —|Uruchamia narzędzie dokumentacji XML xdcmake.exe.|
|XSD|Uruchamia narzędzie definicji schematu XML xsd.exe. *Zobacz uwagi poniżej.*|

> [!NOTE]
> Projekt w programie Visual Studio 2017, obsługa C++ **xsd** plików jest przestarzała. Można nadal używać **Microsoft.VisualC.CppCodeProvider** , dodając **CppCodeProvider.dll** ręcznie do pamięci podręcznej GAC.

## <a name="see-also"></a>Zobacz też

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
