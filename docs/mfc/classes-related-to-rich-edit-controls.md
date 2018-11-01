---
title: Klasy związane z formantami edycji wzbogaconej
ms.date: 11/04/2016
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
ms.openlocfilehash: 92134d0bd4d02bff7aeadd5e9ca7438c61de3bec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586163"
---
# <a name="classes-related-to-rich-edit-controls"></a>Klasy związane z formantami edycji wzbogaconej

[CRichEditView](../mfc/reference/cricheditview-class.md), [CRichEditDoc](../mfc/reference/cricheditdoc-class.md), i [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md) klasy zapewniają funkcje formantu bogatej edycji ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) w kontekście architektury dokumentu/widoku MFC. `CRichEditView` przechowuje tekst i właściwości formatowania tekstu. `CRichEditDoc` przechowuje listę elementów klienta OLE, które znajdują się w widoku. `CRichEditCntrItem` udostępnia siebie kontener elementu klienta OLE. Aby zmodyfikować zawartość `CRichEditView`, użyj [CRichEditView::GetRichEditCtrl](../mfc/reference/cricheditview-class.md#getricheditctrl) dostępu do podstawowych kontrolki edycji wzbogaconej.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

