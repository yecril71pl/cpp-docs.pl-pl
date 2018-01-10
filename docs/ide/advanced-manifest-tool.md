---
title: "Zaawansowane narzędzia manifestu właściwości konfiguracji &lt;Projectname&gt; stron właściwości — okno dialogowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.KeyFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- VC.Project.VCManifestTool.ValidateSignature
- VC.Project.VCManifestTool.KeyContainer
dev_langs: C++
ms.assetid: 3d587366-05ea-4956-a978-313069660735
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c756da4ef7b89113ce26e7218011d708ff4c935c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="advanced-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Zaawansowane narzędzia manifestu właściwości konfiguracji &lt;Projectname&gt; stron właściwości — okno dialogowe
To okno dialogowe służy do określenia opcji zaawansowanych [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Aby uzyskać dostęp do tej strony właściwości — okno dialogowe, otwórz strony właściwości projektu lub arkuszu właściwości. Rozwiń węzeł **narzędziu manifestu** węźle **właściwości konfiguracji**, a następnie wybierz **zaawansowane**.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Aktualizuj skróty plików**  
 Opcja /hashupdate jest używana do określenia, że narzędzia manifestu będzie obliczeniowe skrótu plików określonych w `<file>` elementy, a następnie aktualizacji skrót atrybutów z obliczoną wartością.  
  
 **Ścieżka wyszukiwania skrótów plików aktualizacji**  
 Określa ścieżkę wyszukiwania dla plików, które są używane w `<file>` elementów. Ta opcja używa również opcję /hashupdate.  
  
## <a name="see-also"></a>Zobacz też  
 [\<Plik > — Element](/visualstudio/deployment/file-element-clickonce-application)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Strony właściwości narzędzia manifestu](../ide/manifest-tool-property-pages.md)   
 [Praca z właściwościami projektu](../ide/working-with-project-properties.md)   