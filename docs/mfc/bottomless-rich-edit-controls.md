---
title: Formanty edycji wzbogaconej nieograniczone od dołu
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: 1c5578181b580ddb07b69f5fd2e91aea4b85a72b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624873"
---
# <a name="bottomless-rich-edit-controls"></a>Formanty edycji wzbogaconej nieograniczone od dołu

Aplikację można zmienić rozmiar kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)), tak aby zawsze jest taki sam rozmiar jak jego zawartość. Kontrolki edycji wzbogaconej obsługuje to tak zwane "nieograniczone" funkcje, wysyłając okna nadrzędnego [EN_REQUESTRESIZE](/windows/desktop/Controls/en-requestresize) wiadomość z powiadomieniem zawsze wtedy, gdy zmienia się rozmiar jego zawartość.

Podczas przetwarzania **EN_REQUESTRESIZE** komunikatu powiadomienia aplikacja powinna rozmiar formantu do wymiarów w określonym [REQRESIZE](/windows/desktop/api/richedit/ns-richedit-_reqresize) struktury. Aplikacja może również przenieść żadnych informacji obok kontrolki, aby uwzględnić zmiany formantu w wysokości. Aby zmienić rozmiar kontrolki, można użyć `CWnd` funkcja [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).

Można wymusić kontrolki edycji wzbogaconej nieograniczone wysyłać **EN_REQUESTRESIZE** komunikatu powiadomienia za pomocą [RequestResize](../mfc/reference/cricheditctrl-class.md#requestresize) funkcja elementu członkowskiego. Ten komunikat może być przydatne w [OnSize](../mfc/reference/cwnd-class.md#onsize) programu obsługi.

Aby otrzymać **EN_REQUESTRESIZE** komunikaty powiadomień, musi włączyć powiadomienia, za pomocą `SetEventMask` funkcja elementu członkowskiego.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

