---
title: "Narzędzie manifestu izolowane właściwości modelu COM (Visual C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
dev_langs: C++
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fe2098c4caead6ebc9ad4747354ae96f093f2c91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Izolowane, narzędzia manifestu, właściwości, &lt;Projectname&gt; stron właściwości — okno dialogowe
To okno dialogowe służy do określania **izolowanego COM** opcje [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Aby uzyskać dostęp do tej strony właściwości — okno dialogowe, otwórz strony właściwości projektu lub arkuszu właściwości. Rozwiń węzeł **narzędziu manifestu** węzeł w węźle **wspólne właściwości**, a następnie wybierz **izolowanego COM**.  
  
## <a name="task-list"></a>Lista zadań  
  
-   [Instrukcje: kompilowanie izolowanych aplikacji korzystających ze składników COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Pliku biblioteki typów**  
 Używa opcji/tlb, aby określić nazwę pliku biblioteki typów (pliku .tlb) używanego do generowania pliku manifestu narzędzia manifestu.  
  
 **Plik skryptu rejestratora**  
 Opcja /rgs jest używana do określenia nazwy plik skryptu rejestratora (pliku .rgs), który narzędzia manifestu będzie używał do generowania pliku manifestu.  
  
 **Nazwa pliku składnika**  
 Opcja/dll jest używana do określenia nazwy zasobu, który zostanie wygenerowany przez narzędzie manifestu. Wprowadź wartość dla tej właściwości po wartości w obu **pliku biblioteki typów** lub **plik skryptu rejestratora** zostały określone.  
  
 **Plik zastępstw**  
 Używa opcji /replacements, aby określić pełną ścieżkę do pliku, który zawiera wartości dla wymienialnych ciągów w pliku .rgs.  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje izolowane](http://msdn.microsoft.com/library/aa375190)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Strony właściwości narzędzia manifestu](../ide/manifest-tool-property-pages.md)   
 [Praca z właściwościami projektu](../ide/working-with-project-properties.md)   