---
title: 'Kontrolki ActiveX MFC: Zwracanie kodów błędów z metody | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdcd18a80b430a0a8576effaaa46215dd5eb9600
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36927922"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>Kontrolki ActiveX MFC: zwracanie kodów błędów z metody
W tym artykule opisano sposób zwracania kodów błędów z metody formantu ActiveX.  
  
 Aby wskazać, że wystąpił błąd w metodzie, należy używać [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror) funkcji członkowskiej, która przyjmuje SCODE (kod stanu), jako parametr. Można użyć wstępnie zdefiniowanych SCODE lub zdefiniuj własny.  
  
> [!NOTE]
>  `ThrowError` ma być używane tylko jako środek zwróciła błąd z Get właściwości lub zestawu funkcji lub metody automatyzacji. Są to jedyna razy, które będą program obsługi wyjątku odpowiednie znajduje się on na stosie.  
  
 Funkcje pomocy istnieje dla najbardziej typowe wstępnie SCODEs, takich jak [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), i [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).  
  
 Listę wstępnie zdefiniowanych SCODEs i instrukcje na temat definiowania SCODEs niestandardowych, zobacz sekcję [obsługi błędów w tym formancie ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) w formantach ActiveX: Tematy zaawansowane.  
  
 Aby uzyskać więcej informacji na wyjątki w innych obszarach kodu raportowania, zobacz [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) i sekcji [obsługi błędów w tym formancie ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) w formantach ActiveX: Tematy zaawansowane.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

