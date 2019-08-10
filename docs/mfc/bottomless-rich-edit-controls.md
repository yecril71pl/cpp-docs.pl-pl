---
title: Formanty edycji wzbogaconej nieograniczone od dołu
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: d5650d34ffc350444061aa6147c38af016458811
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915268"
---
# <a name="bottomless-rich-edit-controls"></a>Formanty edycji wzbogaconej nieograniczone od dołu

W razie potrzeby aplikacja może zmienić rozmiar kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)), tak aby zawsze była taka sama, jak jej zawartość. Kontrolka edycji wzbogaconej obsługuje tę funkcję — nazywaną "dolną" funkcją, wysyłając jej okno nadrzędne w [EN_REQUESTRESIZE](/windows/desktop/Controls/en-requestresize) komunikat powiadomienia o każdym zmianie rozmiaru jego zawartości.

Podczas przetwarzania komunikatu powiadomienia **EN_REQUESTRESIZE** aplikacja powinna zmienić rozmiar kontrolki na wymiary w określonej strukturze [REQRESIZE](/windows/desktop/api/richedit/ns-richedit-reqresize) . Aplikacja może również przenieść wszystkie informacje blisko kontrolki, aby dopasować wysokość kontrolki. Aby zmienić rozmiar kontrolki, można użyć `CWnd` funkcji [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).

Można wymusić, aby do wysyłania komunikatu powiadomienia **EN_REQUESTRESIZE** za pomocą funkcji członkowskiej [REQUESTRESIZE](../mfc/reference/cricheditctrl-class.md#requestresize) . Ten komunikat może być przydatny w [](../mfc/reference/cwnd-class.md#onsize) programie obsługi OnSize.

Aby odbierać komunikaty powiadomień **EN_REQUESTRESIZE** , należy włączyć powiadomienie przy użyciu `SetEventMask` funkcji składowej.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
