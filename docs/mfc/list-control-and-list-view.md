---
title: Formant listy i widok listy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 893ff83067c2a7fbc6c375dd6ee03248114ca5ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="list-control-and-list-view"></a>Kontrolka listy i widok listy
Dla wygody MFC hermetyzuje kontrolki listy na dwa sposoby. Można użyć kontrolki listy:  
  
-   Bezpośrednio, poprzez zastosowanie [CListCtrl](../mfc/reference/clistctrl-class.md) obiekt klasy okien dialogowych.  
  
-   Pośrednio, za pomocą klasy [clistview —](../mfc/reference/clistview-class.md).  
  
 `CListView`ułatwia integrowanie formant listy o architekturze dokument/widok MFC, hermetyzując formantu znacznie jako [CEditView](../mfc/reference/ceditview-class.md) hermetyzuje formantu edycyjnego: kontrolki wypełnienia całego powierzchni widoku MFC. (Widok *jest* formantu rzutować `CListView`.)  
  
 A `CListView` obiekt dziedziczy [CCtrlView](../mfc/reference/cctrlview-class.md) i jego elementów bazowych klas i dodaje funkcję członkowską do pobrania podstawowej kontrolki listy. Używanie widoku elementów członkowskich do pracy z widok jako widok. Użyj [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl) funkcji członkowskiej, aby uzyskać dostęp do funkcji Członkowskich kontrolki listy. Użyj tych elementów członkowskich do:  
  
-   Dodawanie, usuwanie lub manipulowania "elementy" na liście.  
  
-   Ustawiać ani pobierać atrybuty kontrolki listy.  
  
 Można uzyskać odwołania do `CListCtrl` bazowy `CListView`, wywołaj `GetListCtrl` z klasy widoku listy:  
  
 [!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]  
  
 W tym temacie opisano zarówno sposoby używania kontrolki listy.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

