---
title: Zmienianie stylów kontrolki listy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4919d9fd947a489ee9535abd5aa57d7861ba5a37
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197997"
---
# <a name="changing-list-control-styles"></a>Zmienianie stylów kontrolki listy
Można zmienić styl okna kontrolki listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) w dowolnym momencie po jego utworzeniu. Zmiana stylu okna, możesz zmienić rodzaj widoku, który korzysta z kontrolki. Na przykład, aby emulować w Eksploratorze, może być podasz w menu i przycisków paska narzędzi do przełączania sterowania między różne widoki: widoku ikon, widoku listy i tak dalej.  
  
 Na przykład po wybraniu elementu menu, możesz wykonać wywołanie do [GetWindowLong](https://msdn.microsoft.com/library/windows/desktop/ms633584) można pobrać bieżącego stylu kontrolki, a następnie wywołać [SetWindowLong](https://msdn.microsoft.com/library/windows/desktop/ms633591) zresetować stylu. Aby uzyskać więcej informacji, zobacz [za pomocą kontrolki widoku listy](/windows/desktop/Controls/using-list-view-controls) w zestawie Windows SDK.  
  
 Dostępne style są wymienione w [Utwórz](../mfc/reference/clistctrl-class.md#create). Style **LVS_ICON**, **LVS_SMALLICON**, **LVS_LIST**, i **LVS_REPORT** wyznaczyć widoki kontrolne cztery listy.  
  
## <a name="extended-styles"></a>Rozszerzone style  
 Oprócz standardowych stylów kontrolki listy istnieje inny zestaw, określane jako rozszerzone style. Te style omówione w [rozszerzone style widoku listy](/windows/desktop/Controls/extended-list-view-styles) w zestawie Windows SDK oferują różne przydatne funkcje, które dostosować zachowanie kontroli nad listy. Aby zaimplementować to zachowanie niektórych stylu (takie jak wybór aktywowaniu), wywoływania [CListCtrl::SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle), przekazanie wymaganych stylu. W poniższym przykładzie pokazano wywołanie funkcji:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]  
  
> [!NOTE]
>  Do wyboru po wskazaniu wskaźnikiem do pracy, musisz również posiadać albo **LVS_EX_ONECLICKACTIVATE** lub **LVS_EX_TWOCLICKACTIVATE** włączona.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

