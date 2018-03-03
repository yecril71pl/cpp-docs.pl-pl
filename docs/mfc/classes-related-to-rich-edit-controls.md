---
title: "Klasy związane z formantami edycji wzbogaconej | Dokumentacja firmy Microsoft"
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
- rich edit controls [MFC], and CRichEditItem
- CRichEditCtrl class [MFC], related classes
- CRichEditDoc class [MFC], Rich Edit controls
- rich edit controls [MFC], classes related to
- classes [MFC], related to rich edit controls
- rich edit controls [MFC], and CRichEditView
- CRichEditCtrlItem class and CRichEditCtrl
- rich edit controls [MFC], and CRichEditDoc
- CRichEditView class [MFC], and CRichEditCtrl
ms.assetid: 4b31c2cc-6ea1-4146-b7c5-b0b5b419f14d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a8373435f1f97b6b2038e5769c853d521b906715
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="classes-related-to-rich-edit-controls"></a>Klasy związane z formantami edycji wzbogaconej
[Cricheditview —](../mfc/reference/cricheditview-class.md), [cricheditdoc —](../mfc/reference/cricheditdoc-class.md), i [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md) klasy udostępniania funkcji elementu kontrolki zaawansowanej edycji ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) w ramach architektury dokument/widok MFC. `CRichEditView`przechowuje tekst i właściwości formatowania tekstu. `CRichEditDoc`przechowuje listę elementów klienta OLE, które znajdują się w widoku. `CRichEditCntrItem`udostępnia kontener po stronie klienta elementu OLE. Aby zmodyfikować zawartość `CRichEditView`, użyj [CRichEditView::GetRichEditCtrl](../mfc/reference/cricheditview-class.md#getricheditctrl) do dostępu do podstawowych kontrolka zaawansowanej edycji.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

