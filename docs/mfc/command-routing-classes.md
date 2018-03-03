---
title: "Klasy routingu poleceń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.command
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c7e49c92b909abb01f3daec9e16f0e08b2a31c89
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="command-routing-classes"></a>Klasy routingu poleceń
Jako użytkownik wchodzi w interakcję z aplikacją, wybierając z menu lub przycisków pasek sterowania myszą, aplikacja wysyła komunikaty z obiektu dotyczy interfejsu użytkownika do odpowiedniego obiektu docelowym polecenia. Pochodne klasy docelowej polecenia `CCmdTarget` obejmują [CWinApp](../mfc/reference/cwinapp-class.md), [CWnd](../mfc/reference/cwnd-class.md), [cdoctemplate —](../mfc/reference/cdoctemplate-class.md), [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), i pochodne klasy. Platforma obsługuje polecenie automatycznego routingu, aby polecenia mogą być obsługiwane przez obiekt najbardziej odpowiednia aktualnie aktywne w aplikacji.  
  
 Obiekt klasy `CCmdUI` są przekazywane do polecenia update celów polecenia interfejsu użytkownika ([on_update_command_ui —](reference/message-map-macros-mfc.md#on_update_command_ui)) programów obsługi, aby aktualizować stan interfejsu użytkownika dla określonego polecenia (na przykład w celu wyboru lub usuń wyboru z elementów menu). Wywołania funkcji Członkowskich `CCmdUI` obiekt, aby zaktualizować stan obiektu interfejsu użytkownika. Ten proces jest taki sam, czy obiekt interfejsu użytkownika, skojarzony z konkretnego polecenia jest element menu lub przycisku lub oba.  
  
 [CCmdTarget —](../mfc/reference/ccmdtarget-class.md)  
 Służy jako klasa podstawowa dla wszystkich klas obiektów, które mogą być odbierane i odpowiadać na komunikaty.  
  
 [Ccmdui —](../mfc/reference/ccmdui-class.md)  
 Udostępnia interfejs programistyczny dla aktualizowanie obiektów interfejsu użytkownika, takich jak elementy menu lub przycisków pasek sterowania. Obiekt docelowy polecenia włącza, wyłącza, sprawdza lub usuwa obiekt interfejsu użytkownika z tym obiektem.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

