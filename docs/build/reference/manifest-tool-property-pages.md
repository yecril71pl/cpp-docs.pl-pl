---
title: Strony właściwości narzędzia manifestu
ms.date: 07/24/2019
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.GenerateCatalogFiles
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.ReplacementsFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- vc.project.AdditionalOptionsPage
ms.assetid: f33499c4-7733-42d9-80e3-8a5018786965
ms.openlocfilehash: e1d0f1ac889cb915216ceb70d48e36efe4ad21bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336299"
---
# <a name="manifest-tool-property-pages"></a>Strony właściwości narzędzia manifestu

Użyj tych stron, aby określić opcje ogólne dla [Mt.exe](/windows/win32/sbscs/mt-exe). Te strony znajdują się w obszarze **Narzędzie** > **Properties** > **manifestu****właściwości** > konfiguracji właściwości projektu .

## <a name="general-property-page"></a>Strona właściwości ogólnych

### <a name="suppress-startup-banner"></a>Pomijanie banera startowego

   **Tak (/nologo)** określa, że standardowe dane praw autorskich firmy Microsoft będą ukryte po uruchomieniu narzędzia manifestu. Ta opcja służy do wygaszanie niepożądanych danych wyjściowych w plikach dziennika, po uruchomieniu mt.exe jako część procesu kompilacji lub ze środowiska kompilacji.

### <a name="verbose-output"></a>Pełne dane wyjściowe

   **Tak (/pełne)** określa, że dodatkowe informacje o kompilacji będą wyświetlane podczas generowania manifestu.

### <a name="assembly-identity"></a>Tożsamość zestawu

Używa /identity option, aby określić ciąg tożsamości, który składa się z atrybutów [ \<dla assemblyIdentity> Element](/visualstudio/deployment/assemblyidentity-element-clickonce-application). Ciąg tożsamości rozpoczyna się od `name` wartości atrybutu, a następnie par*wartości* *atrybutu.* =  Atrybuty w ciągu tożsamości są rozdzielane przecinkiem.

Jest to przykładowy ciąg tożsamości:`Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="input-and-output-property-page"></a>Strona właściwości wejścia i wyjścia

### <a name="additional-manifest-files"></a>Dodatkowe pliki manifestów

Używa **/manifest** opcji, aby określić pełne ścieżki dodatkowych plików manifestu, które narzędzie manifestu będzie przetwarzać lub scalać. Pełne ścieżki są rozdzielane średnikiem. (-manifest [manifest1] [manifest2] ...)

### <a name="input-resource-manifests"></a>Manifesty zasobów wejściowych

Używa **/inputresource** opcja, aby określić pełną ścieżkę zasobu typu RT_MANIFEST, do wprowadzania danych do narzędzia manifestu. Ścieżka może być po określonym identyfikatorze zasobu. Przykład:

`dll_with_manifest.dll;#1`

### <a name="embed-manifest"></a>Osadzanie manifestu

- **Tak** określa, że system projektu osadza plik manifestu aplikacji do zestawu.

- **Brak** określa, że system projektu utworzy plik manifestu aplikacji jako plik autonomiczny.

### <a name="output-manifest-file"></a>Plik manifestu wyjściowego

Określa nazwę wyjściowego pliku manifestu. Ta właściwość jest opcjonalna, gdy tylko jeden plik manifestu jest obsługiwany przez narzędzie manifestu. (-out:[plik];#[Identyfikator zasobu])

### <a name="manifest-resource-file"></a>Plik zasobu manifestu

Określa plik zasobów wyjściowych używany do osadzania manifestu w danych wyjściowych projektu.

### <a name="generate-catalog-files"></a>Generowanie plików wykazu

Używa opcji **/makecdfs,** aby określić, że narzędzie manifestu wygeneruje pliki definicji katalogu (pliki cdf), które są używane do tworzenia katalogów. (/makecdfs)

### <a name="generate-manifest-from-managedassembly"></a>Generowanie manifestu z managedassembly

Generuje manifest z zestawu zarządzanego. (-zarządzanyaszenazyna:\[plik])

### <a name="suppress-dependency-element"></a>Pomijanie elementu zależności

Używany z -managedassembly. pomija generowanie elementów zależności w końcowym manifeście. (-nodependency)

### <a name="generate-category-tags"></a>Generowanie znaczników kategorii

Używany z -managedassembly. -category powoduje wygenerowanie tagów kategorii. (kategoria)

### <a name="dpi-awareness"></a>Świadomość DPI

Określa, czy aplikacja jest obsługujących dpi. Domyślnie ustawienie jest **Tak** dla projektów MFC i **nie** w przeciwnym razie, ponieważ tylko projekty MFC zostały wbudowane w świadomości DPI. Można zastąpić ustawienie **tak,** jeśli dodasz kod do obsługi różnych ustawień DPI. Aplikacja może wydawać się rozmyte lub małe, jeśli ustawisz go jako DPI-aware, gdy nie jest.

**Choices**

- **Brak**
- **Funkcja wysokiej rozdzielczości DPI**
- **Na monitor o wysokiej rozdzielczości DPI**

## <a name="isolated-com-property-page"></a>Strona właściwości Izolowane COM

Aby uzyskać więcej informacji na temat izolowanych com, zobacz [Izolowane aplikacje](/windows/win32/SbsCs/isolated-applications) i [jak: Tworzenie izolowanych aplikacji do korzystania ze składników COM](../how-to-build-isolated-applications-to-consume-com-components.md).

### <a name="type-library-file"></a>Wpisz plik biblioteki

Określa bibliotekę typów, która ma być używana do obsługi manifestu regfree COM. (-tlb:[plik])

### <a name="registrar-script-file"></a>Plik skryptu rejestratora

Określa plik skryptu rejestratora, który ma być używany do obsługi manifestu regfree COM. (-rgs:[plik])

### <a name="component-file-name"></a>Nazwa pliku składnika

Określa nazwę pliku składnika, który jest zbudowany z .tlb lub .rgs określonych. (-dll:[plik])

### <a name="replacements-file"></a>Plik zastępczy

Określa plik zawierający wartości wymiennych ciągów w pliku RGS. (zamienniki:[plik])

## <a name="advanced-property-page"></a>Strona właściwości zaawansowanej

### <a name="update-file-hashes"></a>Aktualizuj skróty plików

Oblicza skrót plików określonych w elementach plików i aktualizuje atrybut skrótu o tę wartość. (hashupdate:[ścieżka])

### <a name="update-file-hashes-search-path"></a>Ścieżka wyszukiwania skrótów plików aktualizacji

Określa ścieżkę wyszukiwania, która ma być używana podczas aktualizowania skrótów plików.

### <a name="additional-options"></a>Opcje dodatkowe

Opcje dodatkowe

## <a name="see-also"></a>Zobacz też

[Odwołanie do strony właściwości projektu języka C++](property-pages-visual-cpp.md)
