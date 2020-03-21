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
ms.openlocfilehash: 20ca118b3aacb02333d49b67d13de30f11dc5d8d
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079496"
---
# <a name="manifest-tool-property-pages"></a>Strony właściwości narzędzia manifestu

Te strony służą do określania opcji ogólnych dla programu [Mt. exe](/windows/win32/sbscs/mt-exe). Te strony znajdują się w obszarze **właściwości** > **projektu** > **Właściwości konfiguracji** > **narzędzie manifestu**.

## <a name="general-property-page"></a>Ogólna strona właściwości

### <a name="suppress-startup-banner"></a>Pomiń transparent startowy

   **Tak (/nologo)** określa, że standardowe dane dotyczące praw autorskich firmy Microsoft będą ukrywane po uruchomieniu narzędzia manifestu. Użyj tej opcji, aby pominąć niechciane dane wyjściowe w plikach dziennika, gdy uruchamiasz program Mt. exe jako część procesu kompilacji lub ze środowiska kompilacji.

### <a name="verbose-output"></a>Pełne dane wyjściowe

   **Tak (/verbose)** określa, że podczas generowania manifestu będą wyświetlane dodatkowe informacje o kompilacji.

### <a name="assembly-identity"></a>Tożsamość zestawu * *

Używa opcji/Identity, aby określić ciąg tożsamości, który składa się z atrybutów [elementu\<assemblyIdentity >](/visualstudio/deployment/assemblyidentity-element-clickonce-application). Ciąg tożsamości rozpoczyna się od wartości atrybutu `name` i następuje po niej para par *wartości* = *Attribute* . Atrybuty w ciągu tożsamości są rozdzielane przecinkami.

Jest to przykładowy ciąg tożsamości: `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="input-and-output-property-page"></a>Strona właściwości danych wejściowych i wyjściowych

###  <a name="additional-manifest-files"></a>Dodatkowe pliki manifestu

Używa opcji **/manifest** , aby określić pełne ścieżki dodatkowych plików manifestu, które narzędzie manifestu będzie przetwarzać lub scalać. Pełne ścieżki są rozdzielone średnikami. (-manifest [manifest1] [manifest2]...)

###  <a name="input-resource-manifests"></a>Manifesty zasobów wejściowych

Używa opcji **/inputresource** , aby określić pełną ścieżkę zasobu typu RT_MANIFEST, aby wejść do narzędzia manifestu. Po ścieżce może następować określony identyfikator zasobu. Na przykład:

`dll_with_manifest.dll;#1`

###  <a name="embed-manifest"></a>Osadź manifest

- **Tak** określa, że system projektu osadzi plik manifestu aplikacji w zestawie.

- **Nie** określa, że system projektu utworzy plik manifestu aplikacji jako plik autonomiczny.

###  <a name="output-manifest-file"></a>Wyjściowy plik manifestu

Określa nazwę pliku manifestu danych wyjściowych. Ta właściwość jest opcjonalna, gdy tylko jeden plik manifestu jest obsługiwany przez narzędzie manifestu. (-out: [plik]; # [identyfikator zasobu])

###  <a name="manifest-resource-file"></a>Plik zasobów manifestu

Określa plik zasobów wyjściowych służący do osadzenia manifestu w danych wyjściowych projektu.

###  <a name="generate-catalog-files"></a>Generuj pliki katalogu

Używa opcji **/makecdfs** , aby określić, że narzędzie manifestu będzie generować pliki definicji wykazu (pliki. CDF), które są używane do tworzenia wykazów. /makecdfs

###  <a name="generate-manifest-from-managedassembly"></a>Generuj manifest z ManagedAssembly

Generuje manifest z zarządzanego zestawu. (-managedassemblyname: [plik])

###  <a name="suppress-dependency-element"></a>Pomiń element zależności

Używane z-managedassembly. pomija Generowanie elementów zależności w manifeście końcowym. (-nodependency)

###  <a name="generate-category-tags"></a>Generuj Tagi kategorii

Używane z-managedassembly. -Category powoduje, że Tagi kategorii mają być generowane. (-Category)

###  <a name="dpi-awareness"></a>Rozpoznawanie DPI

Określa, czy aplikacja obsługuje DPI. Domyślnie ustawienie ma **wartość tak** dla projektów MFC i **nie ma żadnych** innych, ponieważ tylko projekty MFC mają świadomość rozdzielczości DPI. Można zastąpić ustawienie wartości **tak** , jeśli dodasz kod obsługujący różne ustawienia DPI. Twoja aplikacja może wydawać się rozmyte lub małe, jeśli ustawisz ją jako niezależną od rozdzielczości DPI.

**Decyzji**

- **Dawaj**
- **Duże rozdzielczości DPI**
- **Na monitor o wysokiej rozdzielczości DPI**

## <a name="isolated-com-property-page"></a>Strona właściwości izolowanego modelu COM

Aby uzyskać więcej informacji na temat izolowanego modelu COM, zobacz [izolowane aplikacje](/windows/win32/SbsCs/isolated-applications) i [instrukcje: Kompilowanie izolowanych aplikacji do korzystania ze składników com](../how-to-build-isolated-applications-to-consume-com-components.md).

###  <a name="type-library-file"></a>Plik biblioteki typów

Określa bibliotekę typów, która ma być używana do obsługi manifestu COM nierejestrowanego. (-tlb: [plik])

###  <a name="registrar-script-file"></a>Plik skryptu rejestratora

Określa plik skryptu rejestratora, który ma być używany na potrzeby obsługi manifestu nierejestrowanego COM. (-RGS: [plik])

###  <a name="component-file-name"></a>Nazwa pliku składnika

Określa nazwę pliku składnika skompilowanego na podstawie określonego. tlb lub. RGS. (-dll: [plik])

###  <a name="replacements-file"></a>Plik zamienników

Określa plik, który zawiera wartości dla wymiennych ciągów w pliku RGS. (zamiany: [plik])

## <a name="advanced-property-page"></a>Zaawansowana Strona właściwości

###  <a name="update-file-hashes"></a>Zaktualizuj skróty plików

Oblicza wartość skrótu plików określonych w elementach pliku i aktualizuje atrybut hash o tej wartości. (hashupdate: [ścieżka])

###  <a name="update-file-hashes-search-path"></a>Ścieżka wyszukiwania aktualizacji skrótów plików

Określa ścieżkę wyszukiwania do użycia podczas aktualizowania skrótów plików.

###  <a name="additional-options"></a>Opcje dodatkowe

Opcje dodatkowe

## <a name="see-also"></a>Zobacz też

[C++odwołanie do strony właściwości projektu](property-pages-visual-cpp.md)
