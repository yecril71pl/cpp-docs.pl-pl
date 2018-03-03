---
title: "Które klasy ATL ułatwienia zawierania formantów ActiveX? | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
ms.assetid: 803a4605-7f4c-4139-8638-49d8783d31b0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 880c7bd52476614a4356690aff2fda286e9f3aef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="which-atl-classes-facilitate-activex-control-containment"></a>Które klasy ATL ułatwienia zawierania formantów ActiveX?
Kod hosting kontrolki w ATL nie wymagają użycia dowolnej klasy ATL; Możesz po prostu utworzyć **"AtlAxWin80"** okno i użyj interfejsu API hosting kontrolki w razie potrzeby (Aby uzyskać więcej informacji, zobacz **co to jest interfejs API Hosting formantu ATL**. Jednak następujące klasy ułatwić funkcje zawierania do użycia.  
  
|Class|Opis|  
|-----------|-----------------|  
|[CAxWindow](../atl/reference/caxwindow-class.md)|Opakowuje **"AtlAxWin80"** okna, zapewniająca metod tworzenia okna, tworzenie formantu i/lub dołączanie formantu do okna i pobierania wskaźniki interfejsu dla obiektu hosta.|  
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|Opakowuje **"AtlAxWinLic80"** okna, zapewniająca metod tworzenia okna, tworzenie formantu i/lub dołączanie licencjonowanego formantu do okna i pobierania wskaźniki interfejsu dla obiektu hosta.|  
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|Działa jako klasę podstawową dla klasy formantów ActiveX oparte na zasób okna dialogowego. Takie formanty może zawierać inne kontrolki ActiveX.|  
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|Działa jako klasę podstawową dla klasy okien dialogowych oparte na zasób okna dialogowego. Takie okien dialogowych mogą zawierać formantów ActiveX.|  
|[CWindow](../atl/reference/cwindow-class.md)|Udostępnia metodę, [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol), który zwróci wskaźnika interfejsu w formancie podany identyfikator okna hosta. Ponadto otoki Windows API udostępnianych przez `CWindow` zazwyczaj ułatwić zarządzanie oknem.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zawierania kontrolek — często zadawane pytania](../atl/atl-control-containment-faq.md)

