---
title: Formanty edycji wzbogaconej nieograniczone od dołu
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: 4affdbeed723ea83beda785116dc4c45771073b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509150"
---
# <a name="bottomless-rich-edit-controls"></a>Formanty edycji wzbogaconej nieograniczone od dołu

W razie potrzeby aplikacja może zmienić rozmiar kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)), tak aby zawsze była taka sama, jak jej zawartość. Kontrolka edycji wzbogaconej obsługuje tę funkcję — nazywaną "dolną" funkcją, wysyłając jej okno nadrzędne w [EN_REQUESTRESIZE](/windows/win32/Controls/en-requestresize) komunikat powiadomienia o każdym zmianie rozmiaru jego zawartości.

Podczas przetwarzania komunikatu powiadomienia **EN_REQUESTRESIZE** aplikacja powinna zmienić rozmiar kontrolki na wymiary w określonej strukturze [REQRESIZE](/windows/win32/api/richedit/ns-richedit-reqresize) . Aplikacja może również przenieść wszystkie informacje blisko kontrolki, aby dopasować wysokość kontrolki. Aby zmienić rozmiar kontrolki, można użyć `CWnd` funkcji [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).

Można wymusić, aby do wysyłania komunikatu powiadomienia **EN_REQUESTRESIZE** za pomocą funkcji członkowskiej [REQUESTRESIZE](../mfc/reference/cricheditctrl-class.md#requestresize) . Ten komunikat może być przydatny w [](../mfc/reference/cwnd-class.md#onsize) programie obsługi OnSize.

Aby odbierać komunikaty powiadomień **EN_REQUESTRESIZE** , należy włączyć powiadomienie przy użyciu `SetEventMask` funkcji składowej.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
