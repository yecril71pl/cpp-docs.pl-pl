---
title: Zasoby
ms.date: 08/28/2019
ms.topic: article
ms.assetid: dade2f6b-c51f-4c33-9023-41956ae4b5f6
f1_keywords:
- VC.Project.VCResourceCompilerTool.PreprocessorDefinitions
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- VC.Project.VCResourceCompilerTool.Culture
- VC.Project.VCResourceCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCResourceCompilerTool.IgnoreStandardIncludePath
- VC.Project.VCResourceCompilerTool.ShowProgress
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.ResourceOutputFileName
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: c4a3048bfa07e9635662534b510fa57caa091f00
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336074"
---
# <a name="resources-property-page"></a>Strona właściwości Zasoby

W przypadku natywnych programów klasycznych systemu Windows kompilacja wywołuje [kompilator zasobów (rc.exe)](/windows/win32/menurc/resource-compiler) w celu dodania obrazów, tabel ciągów i plików *.res* do pliku binarnego. Właściwości udostępniane na tej stronie właściwości są przekazywane do kompilatora zasobów, a nie do kompilatora języka C++ lub konsolidatora. Aby uzyskać więcej informacji na temat właściwości wymienionych tutaj i sposobu mapowania do opcji wiersza polecenia RC, zobacz [Korzystanie z RC (Wiersz polecenia RC)](/windows/win32/menurc/using-rc-the-rc-command-line-). Aby uzyskać informacje na temat uzyskiwania dostępu do stron właściwości **Zasoby,** zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md) Aby programowo uzyskać dostęp do <xref:Microsoft.VisualStudio.VCProjectEngine.VCResourceCompilerTool>tych właściwości, zobacz .

Właściwości zasobów platformy .NET w aplikacjach C++/CLI są udostępniane na [stronie Właściwości zasobów zarządzanych](managed-resources-property-page.md).

## <a name="preprocessor-definitions"></a>Definicje preprocesora

Określa jedną lub więcej zdefiniowanych dla kompilatora zasobów. (/d[makro])

## <a name="undefine-preprocessor-definitions"></a>Definicje przederocesora przeddefine

Niedefińz symbolu. (/u)

## <a name="culture"></a>Culture

Wyświetla listę kultury (na przykład angielski us lub włoski) używane w zasobach. (/l [liczba])

## <a name="additional-include-directories"></a>Dodatkowe katalogi dołączania

Określa jeden lub więcej katalogów do dodania do ścieżki dołączania; użyj ogranicznika średnika, jeśli więcej niż jeden. (/I[ścieżka])

## <a name="ignore-standard-include-paths"></a>Ignoruj standardowe ścieżki dołączania

Uniemożliwia kompilatorowi zasobów wyszukiwanie plików dołączanych w katalogach określonych w zmiennych środowiskowych INCLUDE. (/X)

## <a name="show-progress"></a>Pokaż postęp

Wyślij komunikaty postępu do okna wyjściowego. (/v)

## <a name="suppress-startup-banner"></a>Pomijanie banera startowego

Pomijanie wyświetlania banera startowego i komunikatu informacyjnego (/nologo)

## <a name="resource-file-name"></a>Nazwa pliku zasobu

Określa nazwę pliku zasobu (/fo[file])

## <a name="null-terminate-strings"></a>Ciągi zakończenia zerowego

Dołącz null do wszystkich ciągów w tabelach ciągów. (/n)

## <a name="see-also"></a>Zobacz też

[Odwołanie do strony właściwości projektu języka C++](property-pages-visual-cpp.md)
