---
title: Drukowanie w formantach edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
ms.openlocfilehash: bf402f5495ad85eb0c5067d60fcedfe29e6350bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641210"
---
# <a name="printing-in-rich-edit-controls"></a>Drukowanie w formantach edycji wzbogaconej

Można stwierdzić, kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) do renderowania danych wyjściowych dla określonego urządzenia, takie jak drukarki. Można również określić, że urządzenie wyjściowe, które kontrolki edycji wzbogaconej formatuje jego tekstu.

Aby sformatować część zawartości kontrolki edycji wzbogaconej dla określonego urządzenia, możesz użyć [FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange) funkcja elementu członkowskiego. [FORMATRANGE](/windows/desktop/api/richedit/ns-richedit-_formatrange) struktury używane z tą funkcją określa zakres tekstu do formatowania, a także kontekstu urządzenia (DC) dla urządzeń docelowych.

Po sformatowaniu tekst na urządzeniach, może wysłać dane wyjściowe do urządzenia za pomocą [DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband) funkcja elementu członkowskiego. Używając wielokrotnie `FormatRange` i `DisplayBand`, można zaimplementować aplikację, która wyświetla zawartość kontrolki edycji wzbogaconej. (Pasma jest dzielenie danych wyjściowych na mniejsze części na potrzeby drukowania).

Możesz użyć [SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice) funkcja elementu członkowskiego, aby określić urządzenie docelowe, dla którego kontrolki edycji wzbogaconej formatuje jego tekstu. Ta funkcja jest przydatne w przypadku typu WYSIWYG (wyświetlanych jest, co można uzyskać) formatowania, w której aplikacja umieszcza tekst przy użyciu domyślnej drukarki miar czcionek zamiast na ekranie.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

