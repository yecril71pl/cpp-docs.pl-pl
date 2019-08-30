---
title: Informacje C++ o stronie właściwości projektu systemu Windows — Visual Studio
ms.date: 08/28/2019
helpviewer_keywords:
- project-file macro
- project properties [C++], default values
- user-defined values
- project properties [C++], setting
- macros, project-file
- property pages, project settings
- C++ projects, properties
- build macro
- user-defined macros
ms.assetid: 13ffe3ea-1bc3-4bee-be5e-053a8a99cce4
ms.openlocfilehash: c9fd4fc00e86e0660972fc0bd37b66b2fea02ee0
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177471"
---
# <a name="windows-c-project-property-page-reference"></a>Informacje C++ o stronie właściwości projektu systemu Windows

W programie Visual Studio można określić opcje kompilatora i konsolidatora, ścieżki plików i inne ustawienia kompilacji za pomocą stron właściwości projektu. Właściwości i strony właściwości, które są dostępne, zależą od typu projektu. Na przykład projekt pliku reguł programu make ma stronę właściwości NMake, która nie występuje w projekcie MFC lub konsoli Win32. Aby otworzyć **strony właściwości**, wybierz**Właściwości** **projektu** > z menu głównego lub kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**. Poszczególne pliki mają również strony właściwości, które umożliwiają ustawianie opcji kompilowania i kompilowania tylko dla tego pliku. Poniższa ilustracja przedstawia strony właściwości dla projektu MFC.

![Strony właściwości dla C++ projektu](media/example-prop-page.png)

Ta sekcja zawiera krótkie informacje o samych stronach właściwości. Opcje i ustawienia widoczne na stronach właściwości są udokumentowane w ich własnych tematach i są powiązane ze strony właściwości. Aby uzyskać więcej informacji na temat właściwości projektu, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

W przypadku stron właściwości w projektach systemu Linux zapoznaj się z informacjami na [stronie właściwości systemu Linux C++ ](../../linux/prop-pages-linux.md).

## <a name="in-this-section"></a>W tej sekcji

- [Strona właściwości ogólnych (projekt)](general-property-page-project.md)
- [Strona właściwości ogólnych (plik)](general-property-page-file.md)
- [Zaawansowana Strona właściwości](advanced-property-page.md)
- [Strona właściwości katalogów VC++](vcpp-directories-property-page.md)
- [Strony właściwości konsolidatora](linker-property-pages.md)
- [Strony właściwości narzędzia manifestu](manifest-tool-property-pages.md)
- [Strony właściwości HLSL](hlsl-property-pages.md)
- [Strony właściwości wiersza polecenia](command-line-property-pages.md)
- [Strona właściwości Niestandardowy krok kompilacji: Ogólne](custom-build-step-property-page-general.md)
- [Dodawanie odwołań](../adding-references-in-visual-cpp-projects.md)
- [Strona właściwości Zarządzane zasoby](managed-resources-property-page.md)
- [Strony właściwości MIDL](midl-property-pages.md)
- [Strona właściwości NMake](nmake-property-page.md)
- [Strony właściwości zasobów](resources-property-pages.md)
- [Strona właściwości Odwołania sieci Web](web-references-property-page.md)
- [Strona właściwości Narzędzie generowania danych XML](xml-data-generator-tool-property-page.md)
- [Strony właściwości Narzędzie generowania dokumentów XML](xml-document-generator-tool-property-pages.md)

## <a name="see-also"></a>Zobacz także

[Instrukcje: Tworzenie i usuwanie zależności projektu](/visualstudio/ide/how-to-create-and-remove-project-dependencies)<br/>
[Instrukcje: Tworzenie i edytowanie konfiguracji](/visualstudio/ide/how-to-create-and-edit-configurations)<br/>
[Informacje C++ na stronie właściwości systemu Linux](../../linux/prop-pages-linux.md)
