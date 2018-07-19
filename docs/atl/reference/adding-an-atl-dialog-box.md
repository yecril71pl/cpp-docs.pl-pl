---
title: Dodawanie okna dialogowego ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab00af6480e8893226be460a3d7c5641b8755bcf
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953224"
---
# <a name="adding-an-atl-dialog-box"></a>Dodawanie okna dialogowego ATL
Aby dodać okno dialogowe ATL do projektu, projekt musi być projektu ATL lub projekt MFC, który obejmuje obsługę ATL. Możesz użyć [Kreator projektów ATL](../../atl/reference/atl-project-wizard.md) do tworzenia aplikacji biblioteki ATL, lub [Dodaj obiekt ATL do Twojej aplikacji MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) do zaimplementowania Obsługa ALT dla aplikacji MFC.  
  
 Domyślnie Kreator okna dialogowego ATL implementuje okno dialogowe pochodną [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Ta klasa zawiera obsługę hostowania kontrolki ActiveX i Windows. Jeśli nie mają obciążenie obsługi formantów ActiveX, gdy kreator został wygenerowany kod, należy zastąpić wszystkie wystąpienia elementu `CAxDialogImpl` z oboma [CSimpleDialog](../../atl/reference/csimpledialog-class.md) lub [CDialogImpl](../../atl/reference/cdialogimpl-class.md) jako klasę bazową .  
  
> [!NOTE]
>  `CSimpleDialog` tworzy tylko modalnych okien dialogowych, które obsługują tylko Windows wspólnych formantów. `CDialogImpl` Tworzy albo w modalnym lub niemodalnym dialogowych.  
  
### <a name="to-add-an-atl-dialog-resource-to-your-project"></a>Można dodać zasobu okna dialogowego ATL do projektu  
  
1.  Utwórz projekt ATL za pomocą [Kreator projektów ATL](../../atl/reference/atl-project-wizard.md).  
  
2.  Z [Widok klas](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy nazwę projektu i kliknij przycisk **Dodaj** z menu skrótów. Kliknij przycisk **Dodaj klasę**.  
  
3.  W okienku szablonów okna [Dodaj klasę](../../ide/add-class-dialog-box.md) okno dialogowe, kliknij przycisk **okno dialogowe ATL**. Kliknij przycisk **Otwórz** do wyświetlenia [Kreator okna dialogowego ATL](../../atl/reference/atl-dialog-wizard.md).  
  
 Aby uzyskać więcej informacji, zobacz [Implementowanie okna dialogowego](../../atl/implementing-a-dialog-box.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)   
 [Klasy okien](../../atl/atl-window-classes.md)   
 [Mapy komunikatów](../../atl/message-maps-atl.md)

