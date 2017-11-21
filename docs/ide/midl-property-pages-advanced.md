---
title: "Strony właściwości MIDL: Zaawansowane | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ValidateParameters
dev_langs: C++
helpviewer_keywords: MIDL, property pages
ms.assetid: d1c92e01-f403-4ed6-ab45-4043a3c9c6bb
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 15abdc0f35d3f69e301020bb3c9c4f8fb6e9d321
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="midl-property-pages-advanced"></a>Strony właściwości MIDL: zaawansowane
**Zaawansowane** stronę właściwości w **MIDL** folderu określa następujące opcje kompilatora MIDL:  
  
-   Włącz sprawdzanie błędów ([/Error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Sprawdź alokacje ([/Error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Sprawdź granice ([/Error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Sprawdź zakres ([/Error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Sprawdź wskaźniki odwołań ([/Error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Sprawdź dane ([/Error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Sprawdź poprawność parametrów ([/ robust](http://msdn.microsoft.com/library/windows/desktop/aa367363)) *  
  
-   Wyrównanie członka struktury ([/Zp](http://msdn.microsoft.com/library/windows/desktop/aa367388))  
  
-   Przekieruj dane wyjściowe ([/o](http://msdn.microsoft.com/library/windows/desktop/aa367351))  
  
-   Opcje przetwarzania wstępnego C ([/cpp_opt](http://msdn.microsoft.com/library/windows/desktop/aa367318))  
  
-   Usuń definicje preprocesora ([/U](http://msdn.microsoft.com/library/windows/desktop/aa367373))  
  
 \*/ niezawodne jest tylko do użytku podczas kompilowania dla systemu Windows 2000 lub nowszym komputera. Możesz utworzyć Projekt ATL i chcesz używać / robust, zmień ten wiersz w pliku dlldatax.c:  
  
```  
#define _WIN32_WINNT 0x0400   //for Windows NT 4.0 or Windows 95 with DCOM  
to   
#define _WIN32_WINNT 0x0500   //for Windows NT 4.0 or Windows 95 with DCOM  
```  
  
 Aby uzyskać informacje dotyczące dostępu do **zaawansowane** stronę właściwości w **MIDL** folderu, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
 Aby uzyskać informacje dotyczące sposobu uzyskania programowego dostępu do MIDL opcje dla projektów C++, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>.  
  
## <a name="see-also"></a>Zobacz też  
 [Strony właściwości MIDL](../ide/midl-property-pages.md)