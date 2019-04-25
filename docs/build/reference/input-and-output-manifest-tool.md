---
title: Narzędzie manifestu C++ wejście i wyjście właściwości
ms.date: 08/27/2018
f1_keywords:
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.DependencyInformationFile
- VC.Project.VCManifestTool.OutputResourceManifest
- VC.Project.VCManifestTool.GenerateCatalogFiles
ms.assetid: a8bb20f6-7ace-45ca-bab0-b4f4a5caf170
ms.openlocfilehash: 1731665ffa6117896490115028b4744e195beae2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291058"
---
# <a name="input-and-output-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Wejście i wyjście, narzędzie manifestu, właściwości konfiguracji &lt;Projectname&gt; okno dialogowe strony właściwości

To okno dialogowe służy do określania opcji wejściowe i wyjściowe dla [Mt.exe](/windows/desktop/SbsCs/mt-exe).

Aby uzyskać dostęp do tego okna dialogowego strony właściwości, otwórz strony właściwości dla projektu lub arkuszu właściwości. Rozwiń **narzędziu manifestu** węźle **właściwości konfiguracji**, a następnie wybierz pozycję **danych wejściowych i wyjściowych**.

## <a name="uielement-list"></a>Lista elementów UI

**Dodatkowe pliki manifestu**<br/>
Używa **/manifest** możliwość określenia pełnej ścieżki dodatkowe pliki manifestu, przetwarzających narzędzia manifestu lub scalania. Pełne ścieżki są rozdzielone średnikami.

**Manifesty zasobów wejściowych**<br/>
Używa **/inputresource** opcję, aby określić pełną ścieżkę zasobu typu RT_MANIFEST jako danych wejściowych na narzędziu manifestu. Ścieżka może następować identyfikator określonego zasobu. Na przykład:

`dll_with_manifest.dll;#1`

Identyfikator zasobu jest opcjonalny i domyślnie CREATEPROCESS_MANIFEST_RESOURCE_ID w winuser.h.

**Osadź Manifest**<br/>
- **Tak** określa system projektu będzie Osadzanie pliku manifestu aplikacji do zestawu.

- **Nie** Określa, czy system projektu spowoduje utworzenie pliku manifestu aplikacji jako autonomiczny plik.

**Plik wynikowy manifestu**<br/>
Określa nazwę wyjściowego pliku manifestu. Ta właściwość jest opcjonalna, gdy tylko jeden plik manifestu jest wykonywane są operacje za pomocą narzędzia manifestu.

**Plik zasobów manifestu**<br/>
Określa dane wyjściowe pliki zasoby używane do osadzania manifestu w danych wyjściowych projektu.

**Generuj pliki katalogu**<br/>
Używa **/makecdfs** opcję, aby określić, czy narzędzie manifestu, spowoduje wygenerowanie plików definicji katalogu (pliki .cdf), które służą do katalogów.

**Generuj Manifest z biblioteki ManagedAssembly**<br/>
Generuje manifest z zarządzanego zestawu. (**- managedassemblyname:**<em>pliku</em>).

**Pomiń Element zależności**<br/>
Używane z **- managedassembly** opcji. Ten tag pomija generację zależności elementów w manifeście końcowym.

**Generuj tagi kategorii**<br/>
Używane z **- managedassembly** opcji. Ten tag powoduje, że tagi kategorii do wygenerowania.

**Włączanie rozpoznawanie DPI**<br/>
Określa, czy aplikacja jest obsługującą ustawienia DPI. Domyślnym ustawieniem jest **tak** dla projektów MFC i **nie** inaczej, ponieważ tylko projekty MFC mają wbudowane świadomości DPI. Można zastąpić to ustawienie, aby **tak** Jeśli dodasz kod służący do obsługi różnych ustawień DPI. Aplikacja może pojawić się rozmyte lub małe, jeśli zostanie ustawiona jako obsługującą ustawienia DPI gdy nie jest.

## <a name="see-also"></a>Zobacz także

[Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)<br/>
[Strony właściwości narzędzia manifestu](manifest-tool-property-pages.md)<br/>
[Ustawianie właściwości kompilacji i kompilatora języka C++ w programie Visual Studio](../working-with-project-properties.md)<br/>
