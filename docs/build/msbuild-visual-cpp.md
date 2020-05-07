---
title: MSBuild w wierszu polecenia — C++
ms.date: 12/12/2018
helpviewer_keywords:
- MSBuild
ms.assetid: 7a1be7ff-0312-4669-adf2-5f5bf507d560
ms.openlocfilehash: e95d99cf5c63c824bb9bade8e76bc3ca99079669
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220574"
---
# <a name="msbuild-on-the-command-line---c"></a>MSBuild w wierszu polecenia — C++

Ogólnie rzecz biorąc, zalecamy używanie programu Visual Studio do ustawiania właściwości projektu i wywoływać system MSBuild. Można jednak użyć narzędzia **MSBuild** bezpośrednio z wiersza polecenia. Proces kompilacji jest kontrolowany przez informacje w pliku projektu (. vcxproj), który można utworzyć i edytować. Plik projektu określa opcje kompilacji na podstawie etapów kompilacji, warunków i zdarzeń. Ponadto można określić zero lub więcej argumentów *opcji* wiersza polecenia.

> **MSBuild. exe** [ *project_file* ] [ *Opcje* ]

Opcje wiersza polecenia **/Target** (lub **/t**) i **/Property** (lub **/p**) umożliwiają przesłonięcie określonych właściwości i obiektów docelowych, które są określone w pliku projektu.

Istotną funkcją pliku projektu jest określenie *elementu docelowego*, który jest konkretną operacją zastosowana do projektu, a danymi wejściowymi i wyjściowymi, które są wymagane do wykonania tej operacji. Plik projektu może określać jeden lub więcej obiektów docelowych, które mogą zawierać domyślny element docelowy.

Każdy element docelowy składa się z sekwencji co najmniej jednego *zadania*. Każde zadanie jest reprezentowane przez klasę .NET Framework, która zawiera jedno polecenie wykonywalne. Na przykład [zadanie CL](/visualstudio/msbuild/cl-task) zawiera polecenie [CL. exe](reference/compiling-a-c-cpp-program.md) .

*Parametr Task* jest właściwością zadania klasy i zazwyczaj reprezentuje opcję wiersza polecenia pliku wykonywalnego. Na przykład `FavorSizeOrSpeed` parametr `CL` zadania odpowiada opcjom kompilatora **/OS** i **/OT** .

Dodatkowe parametry zadań obsługują infrastrukturę programu MSBuild. Na przykład parametr `Sources` zadania określa zestaw zadań, które mogą być używane przez inne zadania. Aby uzyskać więcej informacji na temat zadań programu MSBuild, zobacz [Dokumentacja zadania](/visualstudio/msbuild/msbuild-task-reference).

Większość zadań wymaga danych wejściowych i wyjściowych, takich jak nazwy plików, ścieżki i parametry String, numeric lub Boolean. Na przykład typowa wartość wejściowa to nazwa pliku źródłowego. cpp do skompilowania. Ważny parametr wejściowy jest ciągiem, który określa konfigurację i platformę kompilacji, na przykład "Debug\|Win32". Dane wejściowe i wyjściowe są określane przez co najmniej jeden zdefiniowany przez użytkownika `Item` element XML zawarty w `ItemGroup` elemencie.

Plik projektu może również określać *Właściwości* i `ItemDefinitionGroup` *elementy*zdefiniowane przez użytkownika. Właściwości i elementy tworzą pary nazwa/wartość, które mogą być używane jako zmienne w kompilacji. Składnik Name pary definiuje *makro*, a składnik wartości deklaruje *wartość makra*. Do makra właściwości uzyskuje się dostęp przy użyciu notacji $ (*name*), a do polecenia elementu uzyskuje się dostęp przy użyciu notacji%(*name*).

Inne elementy XML w pliku projektu mogą testować makra, a następnie warunkowo ustawiać wartość dowolnego makra lub sterować wykonywaniem kompilacji. Nazwy makr i ciągi literału można łączyć w celu generowania konstrukcji, takich jak ścieżka i nazwa pliku. W wierszu polecenia opcja **/Property** ustawia lub zastępuje właściwość projektu. Do elementów nie można odwoływać się w wierszu polecenia.

System MSBuild może warunkowo wykonać element docelowy przed lub po innym miejscu docelowym. Ponadto system może stworzyć obiekt docelowy w zależności od tego, czy pliki zużywane przez element docelowy są nowsze niż pliki, które emituje.

Aby uzyskać więcej informacji na temat programu MSBuild, zobacz:

- Program [MSBuild](/visualstudio/msbuild/msbuild) Przegląd koncepcji programu MSBuild.

- [Dokumentacja programu MSBuild](/visualstudio/msbuild/msbuild-reference) Informacje referencyjne na temat systemu MSBuild.

- [Odwołanie do schematu pliku projektu](/visualstudio/msbuild/msbuild-project-file-schema-reference) Wyświetla listę elementów schematu XML programu MSBuild wraz z ich atrybutami oraz elementami nadrzędnymi i podrzędnymi. W szczególności należy zwrócić uwagę na elementy [Item](/visualstudio/msbuild/itemgroup-element-msbuild), [Property](/visualstudio/msbuild/propertygroup-element-msbuild), [Target](/visualstudio/msbuild/target-element-msbuild)i [Task](/visualstudio/msbuild/task-element-msbuild) .

- [Dokumentacja wiersza polecenia](/visualstudio/msbuild/msbuild-command-line-reference) Zawiera opis argumentów wiersza polecenia i opcji, których można użyć z programem MSBuild. exe.

- [Odwołanie do zadania](/visualstudio/msbuild/msbuild-task-reference) Opisuje zadania programu MSBuild. W szczególności należy zwrócić uwagę na następujące zadania, które są specyficzne dla Visual C++: [zadanie BSCMAKE](/visualstudio/msbuild/bscmake-task), dane [CL](/visualstudio/msbuild/cl-task), zadanie [CPPClean —](/visualstudio/msbuild/cppclean-task), [lib zadanie](/visualstudio/msbuild/lib-task), [zadanie łączenia](/visualstudio/msbuild/link-task), zadanie [MIDL](/visualstudio/msbuild/midl-task), [MT](/visualstudio/msbuild/mt-task)Task, [RC](/visualstudio/msbuild/rc-task), zadanie [setenv](/visualstudio/msbuild/setenv-task), zadanie [VCMessage —](/visualstudio/msbuild/vcmessage-task)

## <a name="in-this-section"></a>W tej sekcji

|Termin|Definicja|
|----------|----------------|
|[Przewodnik: Tworzenie projektu C++ przy użyciu programu MSBuild](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)|Pokazuje, jak utworzyć projekt Visual Studio C++ przy użyciu programu **MSBuild**.|
|[Porady: korzystanie ze zdarzeń kompilacji w projektach MSBuild](how-to-use-build-events-in-msbuild-projects.md)|Pokazuje, jak określić akcję, która występuje na etapie particuler w kompilacji: przed rozpoczęciem kompilacji; przed uruchomieniem kroku linku; lub po zakończeniu kompilacji.|
|[Porady: dodawanie niestandardowego kroku kompilacji do projektów MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)|Pokazuje, jak dodać etap zdefiniowany przez użytkownika do sekwencji kompilacji.|
|[Porady: dodawanie niestandardowych narzędzi kompilacji do projektów MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)|Pokazuje, jak skojarzyć narzędzie kompilacji z określonym plikiem.|
|[Porady: integrowanie narzędzi niestandardowych we właściwościach projektu](how-to-integrate-custom-tools-into-the-project-properties.md)|Pokazuje, jak dodać opcje niestandardowego narzędzia do właściwości projektu.|
|[Instrukcje: modyfikowanie platformy docelowej i zestawu narzędzi platformy](how-to-modify-the-target-framework-and-platform-toolset.md)|Demonstruje sposób kompilowania projektu dla wielu struktur lub zestawów narzędzi.|

## <a name="see-also"></a>Zobacz też

[Używanie zestawu narzędzi MSVC z poziomu wiersza polecenia](building-on-the-command-line.md)
