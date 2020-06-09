---
title: Formanty edycji wzbogaconej nieograniczone od dołu
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: 567bb5b7f2eb2c203b40b9f1f6add82f5451d672
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616421"
---
# <a name="bottomless-rich-edit-controls"></a>Formanty edycji wzbogaconej nieograniczone od dołu

W razie potrzeby aplikacja może zmienić rozmiar kontrolki edycji wzbogaconej ([CRichEditCtrl](reference/cricheditctrl-class.md)), tak aby zawsze była taka sama, jak jej zawartość. Kontrolka edycji wzbogaconej obsługuje tę funkcję — nazywaną "dolną" funkcją, wysyłając jej okno nadrzędne [EN_REQUESTRESIZE](/windows/win32/Controls/en-requestresize) komunikat powiadomienia za każdym razem, gdy zmieniany jest rozmiar jego zawartości.

Podczas przetwarzania komunikatu powiadomienia **EN_REQUESTRESIZE** aplikacja powinna zmienić rozmiar kontrolki na wymiary w określonej strukturze [REQRESIZE](/windows/win32/api/richedit/ns-richedit-reqresize) . Aplikacja może również przenieść wszystkie informacje blisko kontrolki, aby dopasować wysokość kontrolki. Aby zmienić rozmiar kontrolki, można użyć `CWnd` funkcji [SetWindowPos](reference/cwnd-class.md#setwindowpos).

Można wymusić, aby za pomocą funkcji składowej REQUESTRESIZE **EN_REQUESTRESIZE** wysyłać komunikat z powiadomieniem [RequestResize](reference/cricheditctrl-class.md#requestresize) o nieprawidłowej edycji. Ten komunikat może być przydatny w programie obsługi [OnSize](reference/cwnd-class.md#onsize) .

Aby otrzymywać **EN_REQUESTRESIZE** komunikatów powiadomień, należy włączyć powiadomienie przy użyciu `SetEventMask` funkcji składowej.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CRichEditCtrl](using-cricheditctrl.md)<br/>
[Formanty](controls-mfc.md)
