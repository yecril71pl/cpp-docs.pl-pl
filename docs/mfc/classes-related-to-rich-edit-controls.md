---
title: Klasy związane z formantami edycji wzbogaconej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ee7b6400dcd5c91d054b31153c21008d5302bd0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401267"
---
# <a name="classes-related-to-rich-edit-controls"></a>Klasy związane z formantami edycji wzbogaconej

[CRichEditView](../mfc/reference/cricheditview-class.md), [CRichEditDoc](../mfc/reference/cricheditdoc-class.md), i [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md) klasy zapewniają funkcje formantu bogatej edycji ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) w kontekście architektury dokumentu/widoku MFC. `CRichEditView` przechowuje tekst i właściwości formatowania tekstu. `CRichEditDoc` przechowuje listę elementów klienta OLE, które znajdują się w widoku. `CRichEditCntrItem` udostępnia siebie kontener elementu klienta OLE. Aby zmodyfikować zawartość `CRichEditView`, użyj [CRichEditView::GetRichEditCtrl](../mfc/reference/cricheditview-class.md#getricheditctrl) dostępu do podstawowych kontrolki edycji wzbogaconej.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

