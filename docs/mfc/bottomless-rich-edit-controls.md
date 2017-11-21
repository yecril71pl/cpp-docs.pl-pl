---
title: "Formanty edycji wzbogaconej nieograniczone od dołu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e0b86dfa8a5efc5b7bfce7b7e0704dd030b8a937
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="bottomless-rich-edit-controls"></a>Formanty edycji wzbogaconej nieograniczone od dołu
Aplikację można zmienić rozmiar kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)), który jest zawsze taki sam rozmiar jak jego zawartość. Kontrolki zaawansowanej edycji obsługuje to tak zwane "nieograniczone od dołu" funkcje wysyłając jej okna nadrzędnego [EN_REQUESTRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787983) komunikatu powiadomienia przy każdej zmianie rozmiaru jego zawartość.  
  
 Podczas przetwarzania **EN_REQUESTRESIZE** komunikatu powiadomienia aplikacja powinna rozmiar formantu w celu wymiary w określonym [REQRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787950) struktury. Aplikacja może również przenieść wszystkie informacje w pobliżu kontroli umożliwiających zmianę wysokość formantu. Aby zmienić rozmiar formantu, można użyć `CWnd` funkcja [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).  
  
 Możesz wymusić kontrolki edycji wzbogaconej nieograniczone od dołu do wysyłania **EN_REQUESTRESIZE** komunikatu powiadomienia za pomocą [RequestResize](../mfc/reference/cricheditctrl-class.md#requestresize) funkcję elementu członkowskiego. Ten komunikat może być przydatne w [OnSize](../mfc/reference/cwnd-class.md#onsize) programu obsługi.  
  
 Aby otrzymywać **EN_REQUESTRESIZE** komunikatów powiadomień, należy włączyć powiadomienia za pomocą `SetEventMask` funkcji członkowskiej.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

