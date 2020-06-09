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
ms.openlocfilehash: 584649a2bb2d9a118e390aebf9f7411c3123b1a3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620713"
---
# <a name="classes-related-to-rich-edit-controls"></a>Klasy związane z formantami edycji wzbogaconej

Klasy [CRichEditView](reference/cricheditview-class.md), [CRichEditDoc](reference/cricheditdoc-class.md)i [CRichEditCntrItem](reference/cricheditcntritem-class.md) zapewniają funkcje kontrolki edycji wzbogaconej ([CRichEditCtrl](reference/cricheditctrl-class.md)) w kontekście architektury dokumentu/widoku MFC. `CRichEditView`Zachowuje cechę tekstu i formatowania tekstu. `CRichEditDoc`zachowuje listę elementów klienta OLE, które znajdują się w widoku. `CRichEditCntrItem`zapewnia dostęp po stronie kontenera do elementu klienta OLE. Aby zmodyfikować zawartość elementu `CRichEditView` , użyj [CRichEditView:: GetRichEditCtrl](reference/cricheditview-class.md#getricheditctrl) w celu uzyskania dostępu do źródłowej kontrolki edycji wzbogaconej.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CRichEditCtrl](using-cricheditctrl.md)<br/>
[Formanty](controls-mfc.md)
