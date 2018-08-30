---
title: Zaawansowane, narzędzie manifestu, właściwości konfiguracji &lt;Projectname&gt; okno dialogowe strony właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.KeyFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- VC.Project.VCManifestTool.ValidateSignature
- VC.Project.VCManifestTool.KeyContainer
dev_langs:
- C++
ms.assetid: 3d587366-05ea-4956-a978-313069660735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b12c53f2793f7ac083ca06143be18aa6234f1de
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201587"
---
# <a name="advanced-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Zaawansowane, narzędzie manifestu, właściwości konfiguracji &lt;Projectname&gt; okno dialogowe strony właściwości
To okno dialogowe umożliwia określenie opcji zaawansowanych dla [Mt.exe](https://msdn.microsoft.com/library/aa375649).  
  
 Aby uzyskać dostęp do tego okna dialogowego strony właściwości, otwórz strony właściwości dla projektu lub arkuszu właściwości. Rozwiń **narzędziu manifestu** węźle **właściwości konfiguracji**, a następnie wybierz pozycję **zaawansowane**.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Aktualizuj skróty plików**  
 Używa opcji /hashupdate w celu określenia, czy narzędzie manifestu zostanie obliczenia skrótu plików określonych w `<file>` elementów, a następnie zaktualizuj wartość skrótu atrybuty z obliczoną wartością.  
  
 **Ścieżka wyszukiwania skróty plików aktualizacji**  
 Określa ścieżkę wyszukiwania dla plików, które odwołują się `<file>` elementów. Ta opcja używa również opcja /hashupdate.  
  
## <a name="see-also"></a>Zobacz też  
 [\<Plik > Element](/visualstudio/deployment/file-element-clickonce-application)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Strony właściwości narzędzia manifestu](../ide/manifest-tool-property-pages.md)   
 [Praca z właściwościami projektu](../ide/working-with-project-properties.md)   