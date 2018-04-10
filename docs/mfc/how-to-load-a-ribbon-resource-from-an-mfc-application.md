---
title: 'Porady: ładowanie zasobu wstążki z aplikacji MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6a943f82fc9b438a74af3673e0210612183304c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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

