---
title: "ATL — okno dialogowe Dodawanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d8c9969f4747c6c3fa2a39b7b0452f6ac54c9d58
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-atl-dialog-box"></a>Dodawanie ATL — okno dialogowe
Aby dodać okna dialogowego ATL do projektu, projekt musi być Projekt ATL i MFC projekt, który obsługuje ATL. Można użyć [Kreator projektu ATL](../../atl/reference/atl-project-wizard.md) Aby utworzyć aplikację ATL lub [Dodaj obiekt ATL do aplikacji MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) ATL Obsługa aplikacji MFC.  
  
 Domyślnie Kreator okna dialogowego ATL implementuje okno dialogowe pochodną [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Ta klasa obsługuje hosting formantów ActiveX i systemu Windows. Jeśli nie chcesz koszty obsługi formantu ActiveX, gdy Kreator wygenerował kod, należy zastąpić wszystkie wystąpienia `CAxDialogImpl` przy użyciu jednej [CSimpleDialog](../../atl/reference/csimpledialog-class.md) lub [cdialogimpl —](../../atl/reference/cdialogimpl-class.md) jako klasy podstawowej .  
  
> [!NOTE]
>  `CSimpleDialog`tworzy tylko modalnych okien dialogowych, które obsługują tylko formanty standardowe systemu Windows. `CDialogImpl`Tworzy albo modalne i niemodalne okien dialogowych.  
  
### <a name="to-add-an-atl-dialog-resource-to-your-project"></a>Aby dodać zasób okna dialogowego ATL do projektu  
  
1.  Utwórz projekt ATL za pomocą [Kreator projektu ATL](../../atl/reference/atl-project-wizard.md).  
  
2.  Z [widoku klasy](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), kliknij prawym przyciskiem myszy nazwę projektu i kliknij przycisk **Dodaj** z menu skrótów. Kliknij przycisk **Dodaj klasę**.  
  
3.  W okienku szablonów [Dodaj klasę](../../ide/add-class-dialog-box.md) okno dialogowe, kliknij przycisk **okna dialogowego ATL**. Kliknij przycisk **Otwórz** do wyświetlenia [Kreator okna dialogowego ATL](../../atl/reference/atl-dialog-wizard.md).  
  
 Aby uzyskać więcej informacji, zobacz [implementacja okno dialogowe](../../atl/implementing-a-dialog-box.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)   
 [Klasy okien](../../atl/atl-window-classes.md)   
 [Mapy komunikatów](../../atl/message-maps-atl.md)

