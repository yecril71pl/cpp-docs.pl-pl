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
ms.openlocfilehash: c9e3115000b7b45d9b48a1ac0d274eb32c11f4d0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218882"
---
# <a name="bottomless-rich-edit-controls"></a>Formanty edycji wzbogaconej nieograniczone od dołu
Aplikację można zmienić rozmiar kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)), tak aby zawsze jest taki sam rozmiar jak jego zawartość. Kontrolki edycji wzbogaconej obsługuje to tak zwane "nieograniczone" funkcje, wysyłając okna nadrzędnego [EN_REQUESTRESIZE](/windows/desktop/Controls/en-requestresize) wiadomość z powiadomieniem zawsze wtedy, gdy zmienia się rozmiar jego zawartość.  
  
 Podczas przetwarzania **EN_REQUESTRESIZE** komunikatu powiadomienia aplikacja powinna rozmiar formantu do wymiarów w określonym [REQRESIZE](/windows/desktop/api/richedit/ns-richedit-_reqresize) struktury. Aplikacja może również przenieść żadnych informacji obok kontrolki, aby uwzględnić zmiany formantu w wysokości. Aby zmienić rozmiar kontrolki, można użyć `CWnd` funkcja [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).  
  
 Można wymusić kontrolki edycji wzbogaconej nieograniczone wysyłać **EN_REQUESTRESIZE** komunikatu powiadomienia za pomocą [RequestResize](../mfc/reference/cricheditctrl-class.md#requestresize) funkcja elementu członkowskiego. Ten komunikat może być przydatne w [OnSize](../mfc/reference/cwnd-class.md#onsize) programu obsługi.  
  
 Aby otrzymać **EN_REQUESTRESIZE** komunikaty powiadomień, musi włączyć powiadomienia, za pomocą `SetEventMask` funkcja elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

