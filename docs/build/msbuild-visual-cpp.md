---
title: Program MSBuild w wierszu polecenia — C++
ms.date: 12/12/2018
f1_keywords:
- MSBuild
helpviewer_keywords:
- MSBuild
ms.assetid: 7a1be7ff-0312-4669-adf2-5f5bf507d560
ms.openlocfilehash: 565b1c47b4476fa7cb830e15b978b389f4344ee1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273316"
---
# <a name="msbuild-on-the-command-line---c"></a>Program MSBuild w wierszu polecenia — C++

Ogólnie rzecz biorąc zalecane jest użycie programu Visual Studio do ustawiania właściwości projektu i wywoływać systemu MSBuild. Można jednak użyć **MSBuild** narzędzie bezpośrednio z poziomu wiersza polecenia. Proces kompilacji jest kontrolowana przez informacje zawarte w pliku projektu (.vcxproj), który można tworzyć i edytować. Plik projektu określa opcje kompilacji na podstawie kompilacji etapach, warunki i zdarzenia. Ponadto można określić wartość zero lub więcej wierszy polecenia *opcje* argumentów.

> **msbuild.exe** [ *project_file* ] [ *options* ]

Użyj **/target** (lub **/t**) i **/property** (lub **/p**) opcje wiersza polecenia, aby zastąpić określonych właściwości i elementy docelowe, które są określona w pliku projektu.

Podstawową funkcją pliku projektu jest zdefiniowanie *docelowej*, który jest określoną operacją stosowaną do projektu oraz wejść i wyjść, które są wymagane do wykonania tej operacji. Plik projektu można określić jeden lub więcej obiektów docelowych, które mogą zawierać domyślny adres docelowy.

Każdego obiektu docelowego, który składa się z sekwencji jednego lub więcej *zadania*. Każde zadanie jest reprezentowane przez klasę .NET Framework, która zawiera polecenia pliku wykonywalnego. Na przykład [cl — zadanie](/visualstudio/msbuild/cl-task) zawiera [cl.exe](reference/compiling-a-c-cpp-program.md) polecenia.

A *parametru zadania* jest właściwością zadania klasy i zazwyczaj reprezentuje opcję wiersza polecenia dla polecenia pliku wykonywalnego. Na przykład `FavorSizeOrSpeed` parametru `CL` zadania odpowiada **/Os** i **/Ot** opcje kompilatora.

Parametry dodatkowe zadania obsługuje infrastrukturę programu MSBuild. Na przykład `Sources` zadań parametr określa zestaw zadań, które mogą być wykorzystane przez inne zadania. Aby uzyskać więcej informacji na temat zadań MSBuild, zobacz [odwołanie do zadania](/visualstudio/msbuild/msbuild-task-reference).

Większość zadań wymaga danych wejściowych i wyjściowych, takich jak nazwy plików, ścieżek i ciąg parametrów liczbowych lub logicznych. Na przykład typowymi danymi wejściowymi jest nazwa pliku źródłowego .cpp do skompilowania. Ważny parametr wejściowy jest ciągiem, który określa konfigurację kompilacji i platformy, na przykład "debugowanie\|Win32". Dane wejściowe i wyjściowe są określane przez co najmniej jeden XML zdefiniowane przez użytkownika `Item` elementów zawartych w słowniku `ItemGroup` elementu.

Plik projektu można również określić użytkownika *właściwości* i `ItemDefinitionGroup` *elementów*. Właściwości i elementy tworzą pary nazwa/wartość, które mogą być używane jako zmienne w kompilacji. Składnik nazwy pary definiuje *— makro*, a składnik wartości deklaruje *wartość makra*. Makro właściwości jest dostępne przy użyciu składni $(*nazwa*) notacją i makro elementu odbywa się za pomocą %(*nazwa*) notacji.

Inne elementy XML w pliku projektu mogą testować makra, a następnie warunkowo wartość każdego makra lub kontrolować wykonywanie kompilacji. Nazwy makr i ciągi literałowe mogą zostać łączone w celu generowania konstrukcji, takich jak ścieżka i nazwa pliku. W wierszu polecenia **/property** opcji ustawia lub zastępuje właściwość projektu. Nie można odwoływać się do elementów w wierszu polecenia.

MSBuild system warunkowo może wykonać element docelowy, przed lub po innym elementem docelowym. Ponadto system można zbudować obiekt docelowy oparty na to, czy pliki, które zużywa docelowej są nowsze niż pliki, które on emituje.

Aby uzyskać więcej informacji na temat programu MSBuild zobacz:

- [Program MSBuild](/visualstudio/msbuild/msbuild) pojęcia dotyczące Omówienie programu MSBuild.

- [Odwołanie do MSBuild](/visualstudio/msbuild/msbuild-reference) informacje referencyjne o systemu MSBuild.

- [Odwołanie do schematu pliku projektu](/visualstudio/msbuild/msbuild-project-file-schema-reference) Wyświetla listę elementów schematu XML środowiska MSBuild, wraz z ich atrybutami oraz elementami nadrzędnymi i podrzędnymi. Należy zwrócić szczególną uwagę [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild), [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild), [docelowej](/visualstudio/msbuild/target-element-msbuild), i [zadań](/visualstudio/msbuild/task-element-msbuild) elementów.

- [Informacje dotyczące wiersza polecenia](/visualstudio/msbuild/msbuild-command-line-reference) opisano argumenty wiersza polecenia i opcje, których można używać z msbuild.exe.

- [Zadania, odwołanie](/visualstudio/msbuild/msbuild-task-reference) zadania w tym artykule opisano programu MSBuild. Należy zwrócić szczególną uwagę te zadania, które są specyficzne dla języka Visual C++: [Bscmake — zadanie](/visualstudio/msbuild/bscmake-task), [cl — zadanie](/visualstudio/msbuild/cl-task), [cppclean — zadanie](/visualstudio/msbuild/cppclean-task), [lib — zadanie](/visualstudio/msbuild/lib-task), [połączyć zadanie](/visualstudio/msbuild/link-task), [MIDL — zadanie](/visualstudio/msbuild/midl-task), [MT — zadanie](/visualstudio/msbuild/mt-task), [RC — zadanie](/visualstudio/msbuild/rc-task), [SETENV — zadanie](/visualstudio/msbuild/setenv-task), [vcmessage — zadanie](/visualstudio/msbuild/vcmessage-task)

## <a name="in-this-section"></a>W tej sekcji

|Termin|Definicja|
|----------|----------------|
|[Przewodnik: korzystanie z MSBuild do tworzenia projektu Visual C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)|Pokazuje, jak utworzyć projekt Visual C++ przy użyciu **MSBuild**.|
|[Instrukcje: korzystanie ze zdarzeń kompilacji w projektach MSBuild](how-to-use-build-events-in-msbuild-projects.md)|Pokazuje, jak określić akcję, która występuje na etapie particuler w kompilacji: przed rozpoczęciem kompilacji; przed uruchomieniem kroku łącze; lub po zakończeniu kompilacji.|
|[Instrukcje: dodawanie niestandardowego kroku kompilacji do projektów MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)|Przedstawiono sposób dodawania użytkownika etapu sekwencji kompilacji.|
|[Instrukcje: dodawanie niestandardowych narzędzi kompilacji do projektów MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)|Pokazuje, jak skojarzyć narzędzie kompilacji z określonego pliku.|
|[Instrukcje: integrowanie narzędzi niestandardowych we właściwościach projektu](how-to-integrate-custom-tools-into-the-project-properties.md)|Pokazuje, jak dodać opcje dla narzędzi niestandardowych we właściwościach projektu.|
|[Instrukcje: modyfikowanie platformy docelowej i zestawu narzędzi platformy](how-to-modify-the-target-framework-and-platform-toolset.md)|Pokazuje, jak skompilować projekt dla wielu platform ani zestawów narzędzi.|

## <a name="see-also"></a>Zobacz także

[Używanie zestawu narzędzi MSVC z poziomu wiersza polecenia](building-on-the-command-line.md)
