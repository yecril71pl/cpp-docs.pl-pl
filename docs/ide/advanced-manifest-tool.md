---
title: Zaawansowane, narzędzie manifestu, właściwości konfiguracji &lt;Projectname&gt; okno dialogowe strony właściwości
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCManifestTool.KeyFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- VC.Project.VCManifestTool.ValidateSignature
- VC.Project.VCManifestTool.KeyContainer
ms.assetid: 3d587366-05ea-4956-a978-313069660735
ms.openlocfilehash: 10da66c690106255d34c82b066f3450c5cc8a37a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530562"
---
# <a name="advanced-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Zaawansowane, narzędzie manifestu, właściwości konfiguracji &lt;Projectname&gt; okno dialogowe strony właściwości

To okno dialogowe umożliwia określenie opcji zaawansowanych dla [Mt.exe](https://msdn.microsoft.com/library/aa375649).

Aby uzyskać dostęp do tego okna dialogowego strony właściwości, otwórz strony właściwości dla projektu lub arkuszu właściwości. Rozwiń **narzędziu manifestu** węźle **właściwości konfiguracji**, a następnie wybierz pozycję **zaawansowane**.

## <a name="uielement-list"></a>Lista elementów UI

- **Aktualizuj skróty plików**

   Używa opcji /hashupdate w celu określenia, czy narzędzie manifestu zostanie obliczenia skrótu plików określonych w `<file>` elementów, a następnie zaktualizuj wartość skrótu atrybuty z obliczoną wartością.

- **Ścieżka wyszukiwania skróty plików aktualizacji**

   Określa ścieżkę wyszukiwania dla plików, które odwołują się `<file>` elementów. Ta opcja używa również opcja /hashupdate.

## <a name="see-also"></a>Zobacz też

[\<Plik > Element](/visualstudio/deployment/file-element-clickonce-application)<br>
[Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)<br>
[Strony właściwości narzędzia manifestu](../ide/manifest-tool-property-pages.md)<br>
[Praca z właściwościami projektu](../ide/working-with-project-properties.md)