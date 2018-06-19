---
title: Formanty edycji wzbogaconej nieograniczone od dołu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f2b08f6c04d345b4ae3ab32c6d0f17a1d8a4647
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343314"
---
# <a name="bottomless-rich-edit-controls"></a>Formanty edycji wzbogaconej nieograniczone od dołu
Aplikację można zmienić rozmiar kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)), który jest zawsze taki sam rozmiar jak jego zawartość. Kontrolki zaawansowanej edycji obsługuje to tak zwane "nieograniczone od dołu" funkcje wysyłając jej okna nadrzędnego [EN_REQUESTRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787983) komunikatu powiadomienia przy każdej zmianie rozmiaru jego zawartość.  
  
 Podczas przetwarzania **EN_REQUESTRESIZE** komunikatu powiadomienia aplikacja powinna rozmiar formantu w celu wymiary w określonym [REQRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787950) struktury. Aplikacja może również przenieść wszystkie informacje w pobliżu kontroli umożliwiających zmianę wysokość formantu. Aby zmienić rozmiar formantu, można użyć `CWnd` funkcja [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).  
  
 Możesz wymusić kontrolki edycji wzbogaconej nieograniczone od dołu do wysyłania **EN_REQUESTRESIZE** komunikatu powiadomienia za pomocą [RequestResize](../mfc/reference/cricheditctrl-class.md#requestresize) funkcję elementu członkowskiego. Ten komunikat może być przydatne w [OnSize](../mfc/reference/cwnd-class.md#onsize) programu obsługi.  
  
 Aby otrzymywać **EN_REQUESTRESIZE** komunikatów powiadomień, należy włączyć powiadomienia za pomocą `SetEventMask` funkcji członkowskiej.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

