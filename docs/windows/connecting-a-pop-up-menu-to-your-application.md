---
title: Łączenie Menu wyskakującego z Twoją aplikacją C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- menus [C++], pop-up
- shortcut menus [C++], connecting to applications
ms.assetid: 295cbf0e-6416-478e-bc3d-472fb98e0e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e9a5123481999328e8d3e010f752a27ecef27557
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313276"
---
# <a name="connecting-a-pop-up-menu-to-your-c-application"></a>Łączenie Menu wyskakującego z Twoją aplikacją C++

### <a name="to-connect-a-pop-up-menu-to-your-application"></a>Aby nawiązać połączenie aplikacji menu podręcznego

1. Dodaj program obsługi komunikatów dla WM_CONTEXTMENU (na przykład). Aby uzyskać więcej informacji, zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md).

2. Dodaj następujący kod do obsługi komunikatów:

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md) przekazywane przez komunikat program obsługi jest we współrzędnych ekranu.

## <a name="requirements"></a>Wymagania

MFC

## <a name="see-also"></a>Zobacz też

[Tworzenie menu wyskakujących](../windows/creating-pop-up-menus.md)  
[Edytor menu](../windows/menu-editor.md)  