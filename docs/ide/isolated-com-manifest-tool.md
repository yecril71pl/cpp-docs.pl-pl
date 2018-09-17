---
title: Narzędzie manifestu COM izolowany właściwości (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
dev_langs:
- C++
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5439e04fdb2563748bc21fb494cc09fd7bd5c929
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720099"
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>COM izolowany, narzędzie manifestu, właściwości konfiguracji, &lt;Projectname&gt; okno dialogowe strony właściwości
To okno dialogowe służy do określania **COM izolowany** opcje dla [Mt.exe](https://msdn.microsoft.com/library/aa375649).  
  
Aby uzyskać dostęp do tego okna dialogowego strony właściwości, otwórz strony właściwości dla projektu lub arkuszu właściwości. Rozwiń **narzędziu manifestu** węźle **wspólne właściwości**, a następnie wybierz pozycję **COM izolowany**.  
  
## <a name="task-list"></a>Lista zadań  
  
-   [Instrukcje: kompilowanie izolowanych aplikacji korzystających ze składników COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
## <a name="uielement-list"></a>Lista elementów UI  
- **Plik biblioteki typów**

   Używa opcji/tlb, aby określić nazwę pliku biblioteki typów (pliku .tlb), narzędzie manifestu, zostanie użyta do wygenerowania pliku manifestu.  
  
- **Plik skryptu rejestratora**

   Opcja /rgs jest używana do określenia nazwy plik skryptu rejestratora (pliku .rgs), narzędzie manifestu, zostanie użyta do wygenerowania pliku manifestu.  
  
- **Nazwa pliku składnika**

   Opcja/dll jest używana do określenia nazwy zasobu, który zostanie wygenerowany przez narzędzie manifestu. Wprowadź wartość tej właściwości podczas wartości dla dowolnego **pliku biblioteki typów** lub **plik skryptu rejestratora** zostały określone.  
  
- **Plik zastępstw**

   Używa opcji /replacements, aby określić pełną ścieżkę do pliku, który zawiera wartości dla wymienialnych ciągów w pliku .rgs.  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje izolowane](/windows/desktop/SbsCs/isolated-applications)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Strony właściwości narzędzia manifestu](../ide/manifest-tool-property-pages.md)   
 [Praca z właściwościami projektu](../ide/working-with-project-properties.md)   