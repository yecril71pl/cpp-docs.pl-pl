---
title: Łączenie Menu wyskakującego z Twoją aplikacją | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- pop-up menus, connecting to applications
- context menus, connecting to applications
- menus, pop-up
- shortcut menus, connecting to applications
ms.assetid: 295cbf0e-6416-478e-bc3d-472fb98e0e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5bfe5c4dba3dc8e86eb9a47a6e163af94872b933
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641265"
---
# <a name="connecting-a-pop-up-menu-to-your-application"></a>Łączenie menu wyskakującego z Twoją aplikacją
### <a name="to-connect-a-pop-up-menu-to-your-application"></a>Aby nawiązać połączenie aplikacji menu podręcznego  
  
1.  Dodaj program obsługi komunikatów dla WM_CONTEXTMENU (na przykład). Aby uzyskać więcej informacji, zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md).  
  
2.  Dodaj następujący kod do obsługi komunikatów:  
  
    ```cpp  
    CMenu menu;  
    VERIFY(menu.LoadMenu(IDR_MENU1));  
    CMenu* pPopup = menu.GetSubMenu(0);  
    ASSERT(pPopup != NULL);  
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());  
    ```  
  
    > [!NOTE]
    >  [CPoint](../atl-mfc-shared/reference/cpoint-class.md) przekazywane przez komunikat program obsługi jest we współrzędnych ekranu.  
  
## <a name="requirements"></a>Wymagania  
 MFC  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie menu wyskakujących](../windows/creating-pop-up-menus.md)   
 [Edytor menu](../windows/menu-editor.md)   