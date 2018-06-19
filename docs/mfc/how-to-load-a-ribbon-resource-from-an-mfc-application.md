---
title: 'Porady: ładowanie zasobu wstążki z aplikacji MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b014e1725ae6c5043c051242a74e29338c3ef2d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344194"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>Porady: ładowanie zasobu wstążki z aplikacji MFC
Aby użyć zasobu wstążki w aplikacji, należy zmodyfikować ładowanie zasobu Wstążki aplikacji.  
  
### <a name="to-load-a-ribbon-resource"></a>Ładowanie zasobu wstążki  
  
1.  Deklarowanie `Ribbon Control` obiektu w `CMainFrame` klasy.  
  
 ```  
    CMFCRibbonBar m_wndRibbonBar;   
 ```  
  
2.  W `CMainFrame::OnCreate`, Utwórz i zainicjuj formantu wstążki.  
  
 ```  
    if (!m_wndRibbonBar.Create (this))  
 {  
    return -1;  
 }  
 
    if (!m_wndRibbonBar.LoadFromResource(IDR_RIBBON))  
 {  
    return -1;  
 }  
 ```  
  
## <a name="see-also"></a>Zobacz też  
 [Projektant wstążki (MFC)](../mfc/ribbon-designer-mfc.md)

