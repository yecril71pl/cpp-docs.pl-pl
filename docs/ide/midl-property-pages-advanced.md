---
title: 'Strony właściwości MIDL: Zaawansowane | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
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
dev_langs:
- C++
helpviewer_keywords:
- MIDL, property pages
ms.assetid: d1c92e01-f403-4ed6-ab45-4043a3c9c6bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5f87518c23848cea91a3e3c48361aa0a63fa88a2
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33330807"
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
  
 \* / niezawodne jest tylko do użytku podczas kompilowania dla systemu Windows 2000 lub nowszym komputera. Możesz utworzyć Projekt ATL i chcesz używać / robust, zmień ten wiersz w pliku dlldatax.c:  
  
```  
#define _WIN32_WINNT 0x0400   //for Windows NT 4.0 or Windows 95 with DCOM  
to   
#define _WIN32_WINNT 0x0500   //for Windows NT 4.0 or Windows 95 with DCOM  
```  
  
 Aby uzyskać informacje dotyczące dostępu do **zaawansowane** stronę właściwości w **MIDL** folderu, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
 Aby uzyskać informacje dotyczące sposobu uzyskania programowego dostępu do MIDL opcje dla projektów C++, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>.  
  
## <a name="see-also"></a>Zobacz też  
 [Strony właściwości MIDL](../ide/midl-property-pages.md)