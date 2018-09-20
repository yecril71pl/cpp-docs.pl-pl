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
ms.openlocfilehash: c24ed9328f77d26a8ad11a6ff6bdbf47bad9fbe3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381416"
---
# <a name="property-pages-visual-c"></a>Strony właściwości (Visual C++)

Za pomocą stron właściwości, można określić ustawienia dla projektów programu Visual Studio. Aby otworzyć **stron właściwości** okno dialogowe dla programu Visual Studio projektu na **projektu** menu, wybierz **właściwości**.

Możesz określić ustawienia projektu tak, aby dotyczyły one wszystkie konfiguracje kompilacji lub można określić właściwości inny projekt, dla każdej konfiguracji kompilacji. Na przykład można określić pewne ustawienia konfiguracji wydania i inne ustawienia konfiguracji debugowania.

Nie wszystkie dostępne strony są zawsze wyświetlane w **stron właściwości** okno dialogowe. Które strony są wyświetlane, zależy od typów plików w projekcie.

Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).

Dla projektów innych niż Windows, zobacz [dokumentacja strony właściwości C++ Linux](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->.

## <a name="default-properties-vs-modified-properties"></a>Domyślne właściwości programu vs. Zmodyfikowane właściwości

Kiedy używasz **nowy projekt** okno dialogowe, aby utworzyć projekt, Visual Studio używa tego szablonu określonego projektu, można zainicjować właściwości projektu. W związku z tym wartości właściwości w szablonie można traktować jako wartości domyślne dla tego typu projektu. W innych typów projektów właściwości mogą mieć różne domyślne wartości.

Wartość właściwości projektu pojawia się pogrubioną czcionką, gdy zostanie zmodyfikowany. Można zmodyfikować właściwości projektu z następujących powodów:

- Kreator aplikacji zmienia właściwość, ponieważ wymaga ona wartością innej właściwości niż ten, który jest określony w szablonie projektu.

- Określ wartość inną właściwość w **nowy projekt** okno dialogowe.

- Na stronie właściwości projektu można określić wartość inną właściwość.

> [!TIP]
> Aby wyświetlić ostateczny zestaw wartości właściwości, które korzysta z programu MSBuild do kompilowania projektu, należy sprawdzić plik dane wyjściowe preprocesora, który można tworzyć przy użyciu tego wiersza polecenia: **MSBuild / przetwarzanie wstępne:** *preprocessor_output_ Nazwa pliku*<sub>zoptymalizowany pod kątem</sub> *project_filename*<sub>zoptymalizowany pod kątem</sub>

## <a name="resetting-properties"></a>Resetowanie właściwości

Po wyświetleniu **stron właściwości** wybrano okno dialogowe projektu i węzeł projektu w **Eksploratora rozwiązań**, wiele właściwości, można wybrać **Dziedzicz z nadrzędnych bądź projektowych ustawienia domyślne** lub zmodyfikowaniu wartości w inny sposób.

Po wyświetleniu **stron właściwości** okno dialogowe projektu i pliku wybrano w **Eksploratora rozwiązań**, wiele właściwości, można wybrać **Dziedzicz z nadrzędnych bądź projektowych wartości domyślnych** lub zmodyfikowaniu wartości w inny sposób. Jednakże jeśli projekt zawiera wiele plików, które mają wartości właściwości, które różnią się od wartości domyślne projektu, projekt będzie trwać dłużej kompilacji.

> [!TIP]
> Aby odświeżyć **stron właściwości** okno dialogowe tak, aby wyświetlał najnowsze ustawienia, wybierz **Zastosuj**.

Większość ustawień domyślnych projektu są domyślnych ustawień systemowych (platformy). Niektóre wartości domyślne projektu pochodzi od arkuszy stylów, które są stosowane podczas aktualizowania właściwości **wartości domyślne projektu** części **ogólne** strona właściwości konfiguracji projektu. Aby uzyskać więcej informacji, zobacz [strona właściwości ogólnych (projekt)](../ide/general-property-page-project.md).

## <a name="specifying-user-defined-values"></a>Określanie wartości zdefiniowane przez użytkownika

Należy zdefiniować wartości dla niektórych właściwości. Wartości zdefiniowane przez użytkownika może zawierać znaki alfanumeryczne lub nazw makr w pliku projektu. Niektóre z tych właściwości można wykonać tylko jedna wartość zdefiniowana przez użytkownika, ale inne mogą przejąć rozdzielaną średnikami listę wielu wartości.

Aby określić zdefiniowanych przez użytkownika wartości właściwości lub listy, jeśli właściwość może zająć wiele wartości zdefiniowanej przez użytkownika, w kolumnie z prawej strony nazwy właściwości, wykonaj jedną z następujących czynności:

- Wpisz wartość lub listę wartości.

- Wybierz strzałkę listy rozwijanej. Jeśli **Edytuj** jest dostępna, wybierz go, a następnie w polu tekstowym wpisz wartość lub listę wartości. Alternatywny sposób w celu określenia listy jest typu każdej wartości w oddzielnym wierszu w polu tekstowym. Na stronie właściwości wartości będą wyświetlane jako listę rozdzielaną średnikami.

   Aby wstawić makro pliku projektu jako wartości, wybierz opcję **makra** a następnie kliknij dwukrotnie nazwę makra.

- Wybierz strzałkę listy rozwijanej. Jeśli **Przeglądaj** jest dostępna, wybierz go, a następnie wybierz co najmniej jedną wartość.

Dla właściwości wielowartościowe **Dziedzicz z nadrzędnych bądź projektowych wartości domyślnych** opcja jest dostępna, wybierz strzałkę listy rozwijanej w kolumnie z prawej strony nazwy właściwości, a następnie wybierz polecenie **Edytuj**. Domyślnie opcja jest zaznaczona.

Należy zauważyć, że strona właściwości są wyświetlane tylko ustawienia na bieżącym poziomie dla wielokrotnych wartościach właściwości, która dziedziczy z poziomu innej. Na przykład, jeśli wybrano plik **Eksploratora rozwiązań** i wybraniu języka C/C++ **definicje preprocesora** właściwości definicji na poziomie plików są wyświetlane, ale dziedziczone definicje na poziomie projektu nie są wyświetlane. Aby wyświetlić bieżący poziom i dziedziczonej wartości, wybierz strzałkę listy rozwijanej w kolumnie z prawej strony nazwy właściwości, a następnie wybierz **Edytuj**. Jeśli używasz [model projektów Visual C++](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine), to zachowanie jest również wpływu dla obiektów na plikach i projektach. Oznacza to kiedy wykonujesz zapytanie o wartości we właściwości na poziomie plików, nie otrzymasz wartości tej samej właściwości na poziomie projektu. Należy jawnie uzyskać wartości właściwości na poziomie projektu. Ponadto niektóre dziedziczone wartości właściwości mogą pochodzić z arkusza stylów, który nie jest dostępny programowo.

## <a name="in-this-section"></a>W tej sekcji

[Zaawansowane, narzędzie manifestu, właściwości konfiguracji \<nazwa_projektu > okno dialogowe strony właściwości](../ide/advanced-manifest-tool.md)

[Strony właściwości wiersza polecenia](../ide/command-line-property-pages.md)

[Strona właściwości Niestandardowy krok budowania: ogólne](../ide/custom-build-step-property-page-general.md)

[Dodawanie odwołań](../ide/adding-references-in-visual-cpp-projects.md)

[Strona właściwości ogólnych (plik)](../ide/general-property-page-file.md)

[Strona właściwości ogólnych (projekt)](../ide/general-property-page-project.md)

[Ogólne, narzędzie manifestu, właściwości konfiguracji \<nazwa_projektu > okno dialogowe strony właściwości](../ide/general-manifest-tool-configuration-properties.md)

[Strony właściwości HLSL](../ide/hlsl-property-pages.md)

[Strony właściwości HLSL: zaawansowane](../ide/hlsl-property-pages-advanced.md)

[Strony właściwości HLSL: ogólne](../ide/hlsl-property-pages-general.md)

[Strony właściwości HLSL: pliki wyjściowe](../ide/hlsl-property-pages-output-files.md)

[Wejście i wyjście, narzędzie manifestu, właściwości konfiguracji \<nazwa_projektu > okno dialogowe strony właściwości](../ide/input-and-output-manifest-tool.md)

[COM izolowany, narzędzie manifestu, właściwości konfiguracji, \<nazwa_projektu > okno dialogowe strony właściwości](../ide/isolated-com-manifest-tool.md)

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

[Instrukcje: Tworzenie i usuwanie zależności projektu](/visualstudio/ide/how-to-create-and-remove-project-dependencies)<br>
[Instrukcje: Tworzenie i edytowanie konfiguracji](/visualstudio/ide/how-to-create-and-edit-configurations)
