---
title: Strony właściwości (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.NotAProp.Edit
dev_langs:
- C++
helpviewer_keywords:
- project-file macro
- project properties [C++], default values
- user-defined values
- project properties [C++], setting
- macros, project-file
- property pages, project settings
- Visual C++ projects, properties
- build macro
- user-defined macros
ms.assetid: 13ffe3ea-1bc3-4bee-be5e-053a8a99cce4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1dc831dff6d1e3dbef4fc762712e8125a5b20e1
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "33339712"
---
# <a name="property-pages-visual-c"></a>Strony właściwości (Visual C++)

Za pomocą stron właściwości, można określić ustawienia dla projektów programu Visual Studio. Aby otworzyć **strony właściwości** okno dialogowe dla programu Visual Studio projektu na **projektu** menu, wybierz **właściwości**.

Można określić ustawienia projektu, dzięki czemu mają one zastosowanie wszystkie konfiguracje kompilacji lub możesz określić inny projekt właściwości dla każdej konfiguracji kompilacji. Na przykład można określić niektórych ustawień do konfiguracji wydania i inne ustawienia konfiguracji debugowania.

Nie wszystkie dostępne strony zawsze są wyświetlane w **strony właściwości** okno dialogowe. Stron, które są wyświetlane, zależy od typów plików w projekcie.

Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).

Dla projektów z systemem innym niż Windows, temacie [odwołania do strony właściwości C++ Linux](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->.

## <a name="default-properties-vs-modified-properties"></a>Domyślne właściwości vs. Zmodyfikowane właściwości

Jeśli używasz **nowy projekt** okno dialogowe, aby utworzyć projekt Visual Studio używa szablonu określonego projektu można zainicjować właściwości projektu. W związku z tym wartości właściwości w szablonie można traktować jako wartości domyślne dla tego typu projektu. W innych typów projektów właściwości mogą mieć różne domyślne wartości.

Wartość właściwości projektu zostanie wyświetlone czcionką pogrubioną, czy jego modyfikacji. Można zmodyfikować właściwości projektu z następujących powodów:

- Kreator aplikacji zmienia właściwość, ponieważ wymaga ona wartość właściwości innego niż ten, który określono w szablonie projektu.

- Określ wartość inną właściwość w **nowy projekt** okno dialogowe.

- Określ inną właściwość na stronie właściwości projektu.

> [!TIP]
> Aby zapoznać się ostateczny zestaw wartości właściwości, które używa MSBuild, aby skompilować projekt, sprawdź plik dane wyjściowe preprocesora, który można utworzyć przy użyciu tego wiersza polecenia: **MSBuild / przetwarzanie wstępne:** *preprocessor_output_ Nazwa pliku*<sub>opt</sub> *project_filename*<sub>opcjonalnych</sub>

## <a name="resetting-properties"></a>Resetowanie właściwości

Po wyświetleniu **strony właściwości** okno dialogowe projektu i węzła projektu wybrano w **Eksploratora rozwiązań**, wiele właściwości, można wybrać **dziedziczyć nadrzędnym lub projektu ustawienia domyślne** lub zmodyfikuj wartość w inny sposób.

Po wyświetleniu **strony właściwości** okno dialogowe projektu i pliku wybrano w **Eksploratora rozwiązań**, wiele właściwości, można wybrać **dziedziczyć nadrzędnym lub domyślnych wartościach projektu** lub zmodyfikuj wartość w inny sposób. Jednak jeśli projekt zawiera wiele plików, które mają wartości właściwości, które różnią się od wartości domyślne projektu, projekt będzie trwać dłużej.

> [!TIP]
> Aby odświeżyć **strony właściwości** okno dialogowe, aby wyświetla najnowsze ustawienia, wybierz **Zastosuj**.

Większość domyślne projektu to domyślnych ustawień systemowych (platform). Wartości domyślne niektórych projektu pochodzi z arkuszy stylów, które są stosowane po zaktualizowaniu właściwości w **wartości domyślne projektu** sekcji **ogólne** stronę właściwości konfiguracji dla projektu. Aby uzyskać więcej informacji, zobacz [ogólna strona właściwości (projekt)](../ide/general-property-page-project.md).

## <a name="specifying-user-defined-values"></a>Określanie wartości zdefiniowanej przez użytkownika

Należy określić wartość dla niektórych właściwości. Wartości zdefiniowane przez użytkownika może zawierać znaki alfanumeryczne lub nazwy makro pliku projektu. Niektóre z tych właściwości może trwać tylko jedna wartość zdefiniowana przez użytkownika, ale inne wykorzystują Rozdzielana średnikami lista wielu wartości.

Określenie wartości zdefiniowanej przez użytkownika dla właściwości lub listy, jeśli właściwość może zająć wiele wartości zdefiniowanej przez użytkownika, w kolumnie z prawej strony nazwy właściwości, wykonaj jedną z następujących czynności:

- Wpisz wartość lub listę wartości.

- Wybierz strzałkę listy rozwijanej. Jeśli **Edytuj** jest dostępna, wybierz go, a następnie w polu tekstowym wpisz wartość lub listę wartości. Innym sposobem określania listy polega na wpisaniu każdej wartości w osobnym wierszu w polu tekstowym. Na stronie właściwości wartości będą wyświetlane jako listę rozdzielaną średnikami.

   Aby wstawić makro pliku projektu jako wartość, wybierz **makra** , a następnie kliknij dwukrotnie nazwę makra.

- Wybierz strzałkę listy rozwijanej. Jeśli **Przeglądaj** jest dostępna, wybierz go, a następnie wybierz co najmniej jedną wartość.

Dla właściwości wielowartościowe **dziedziczyć nadrzędnym lub domyślnych wartościach projektu** opcja jest dostępna, wybierz strzałkę listy rozwijanej w kolumnie z prawej strony nazwy właściwości, a następnie wybierz polecenie **Edytuj**. Domyślnie opcja jest zaznaczona.

Zwróć uwagę, że strona właściwości są wyświetlane tylko ustawienia na bieżącym poziomie wielowartościowe właściwość, która dziedziczy z poziomu innego. Na przykład, jeśli wybrano plik **Eksploratora rozwiązań** i wybierz C/C++ **definicje preprocesora** właściwości, definicje poziomu plików są wyświetlane, ale dziedziczone definicje na poziomie projektu nie są wyświetlane. Umożliwia wyświetlenie zarówno bieżącym poziomie i dziedziczonej wartości, wybierz strzałkę listy rozwijanej w kolumnie z prawej strony nazwy właściwości, a następnie wybierz pozycję **Edytuj**. Jeśli używasz [modelu projektu Visual C++](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine), to zachowanie jest również w efekcie dla obiektów w projektach i plików. Oznacza to, że określona w zapytaniu dla wartości dla właściwości na poziomie plików nie otrzymasz wartości tej samej właściwości na poziomie projektu. Należy jawnie pobrać wartości właściwości na poziomie projektu. Ponadto niektóre dziedziczonej wartości właściwości mogą pochodzić z arkusza stylów, który nie jest dostępny programowo.

## <a name="in-this-section"></a>W tej sekcji

[Zaawansowane narzędzia manifestu właściwości konfiguracji \<Projectname > stron właściwości — okno dialogowe](../ide/advanced-manifest-tool.md)

[Strony właściwości wiersza polecenia](../ide/command-line-property-pages.md)

[Strona właściwości Niestandardowy krok budowania: ogólne](../ide/custom-build-step-property-page-general.md)

[Dodawanie odwołań](../ide/adding-references-in-visual-cpp-projects.md)

[Strona właściwości ogólnych (plik)](../ide/general-property-page-file.md)

[Strona właściwości ogólnych (projekt)](../ide/general-property-page-project.md)

[Narzędzie ogólne, manifestu właściwości konfiguracji \<Projectname > stron właściwości — okno dialogowe](../ide/general-manifest-tool-configuration-properties.md)

[Strony właściwości HLSL](../ide/hlsl-property-pages.md)

[Strony właściwości HLSL: zaawansowane](../ide/hlsl-property-pages-advanced.md)

[Strony właściwości HLSL: ogólne](../ide/hlsl-property-pages-general.md)

[Strony właściwości HLSL: pliki wyjściowe](../ide/hlsl-property-pages-output-files.md)

[Dane wejściowe i wyjściowe narzędzie, właściwości konfiguracji manifestu \<Projectname > stron właściwości — okno dialogowe](../ide/input-and-output-manifest-tool.md)

[Izolowane, narzędzia manifestu, właściwości, \<Projectname > stron właściwości — okno dialogowe](../ide/isolated-com-manifest-tool.md)

[Strony właściwości konsolidatora](../ide/linker-property-pages.md)

[Strona właściwości Zarządzane zasoby](../ide/managed-resources-property-page.md)

[Strony właściwości narzędzia manifestu](../ide/manifest-tool-property-pages.md)

[Strony właściwości MIDL](../ide/midl-property-pages.md)

[Strony właściwości MIDL: zaawansowane](../ide/midl-property-pages-advanced.md)

[Strony właściwości MIDL: ogólne](../ide/midl-property-pages-general.md)

[Strony właściwości MIDL: wyjściowe](../ide/midl-property-pages-output.md)

[Strona właściwości NMake](../ide/nmake-property-page.md)

[Strony właściwości zasobów](../ide/resources-property-pages.md)

[Strona właściwości katalogów VC++](../ide/vcpp-directories-property-page.md)

[Strona właściwości Odwołania sieci Web](../ide/web-references-property-page.md)

[Strona właściwości Narzędzie generowania danych XML](../ide/xml-data-generator-tool-property-page.md)

[Strony właściwości Narzędzie generowania dokumentów XML](../ide/xml-document-generator-tool-property-pages.md)

## <a name="see-also"></a>Zobacz także

[Instrukcje: Tworzenie i usuwanie zależności projektu](/visualstudio/ide/how-to-create-and-remove-project-dependencies)  
[Instrukcje: Tworzenie i edytowanie konfiguracji](/visualstudio/ide/how-to-create-and-edit-configurations)  
