---
title: "Manifest narzędzia konfiguracji właściwości (Visual C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.MergeRulesFile
- VC.Project.VCManifestTool.UseUnicodeResponseFiles
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.UseFAT32Workaround
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
dev_langs: C++
ms.assetid: b99368a5-6819-482c-a06e-f2409290cfd1
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: aba154afb6c3f30c305518702f42c618335f5b8e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="general-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Narzędzie ogólne, manifestu właściwości konfiguracji &lt;Projectname&gt; stron właściwości — okno dialogowe
To okno dialogowe służy do określania ogólnych opcji dla [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Aby uzyskać dostęp do tej strony właściwości — okno dialogowe, otwórz strony właściwości projektu lub arkuszu właściwości. Rozwiń węzeł **narzędziu manifestu** węźle **właściwości konfiguracji**, a następnie wybierz **ogólne**.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Pomiń Baner startowy**  
 **Tak (/ nologo)** Określa, że po uruchomieniu narzędzia manifestu powoduje ukrycie standardowych danych o prawach autorskich firmy Microsoft. Użyj tej opcji, aby pominąć niechciane dane wyjściowe w plikach dziennika, po uruchomieniu mt.exe jako część procesu kompilacji lub ze środowiska kompilacji.  
  
 **Pełne dane wyjściowe**  
 **Tak (/ verbose)** Określa, że będą wyświetlane informacje o dodatkowych kompilacji podczas generowania manifestu.  
  
 **Tożsamość zestawu**  
 Użyto opcji /identity do określenia ciąg tożsamości, która składa się z wartości atrybutów [ \<assemblyIdentity > elementu](/visualstudio/deployment/assemblyidentity-element-clickonce-application). Ciąg tożsamości rozpoczyna się od wartości `name` atrybutów i następuje *atrybutu* = *wartość* pary. Atrybuty w ciąg tożsamości są rozdzielone przecinkami.  
  
 Poniżej przedstawiono przykład ciąg tożsamości:  
  
 `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Strony właściwości narzędzia manifestu](../ide/manifest-tool-property-pages.md)   
 [Praca z właściwościami projektu](../ide/working-with-project-properties.md)   