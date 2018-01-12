---
title: "Obiekty interfejsu użytkownika i identyfikatory poleceń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- keyboard shortcuts, associating with IDs
- MFC, command routing
- toolbar controls [MFC], command ID
- menu items, associating with IDs
- user interface objects [MFC], associating with IDs
- command IDs, user interface objects
- command routing [MFC], MFC
- command handling [MFC], user-interface objects
ms.assetid: 4ea19e9b-ed1e-452e-bd33-7f509107a45b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e085c6d9e4d030c8db44e11e570ffa1033abee35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="user-interface-objects-and-command-ids"></a>Obiekty interfejsu użytkownika i identyfikatory poleceń
Elementy menu, przycisków paska narzędzi i klawisze skrótów są "obiekty interfejsu użytkownika" może generować poleceń. Każdy obiekt interfejsu użytkownika ma identyfikator. Obiekt interfejsu użytkownika należy skojarzyć z polecenia, przypisując ten sam identyfikator obiektu i polecenia. Zgodnie z objaśnieniem w [wiadomości](../mfc/messages.md), polecenia są zaimplementowane jako specjalnych wiadomości. Na rysunku "Poleceń w ramach" poniżej pokazano, jak zarządza poleceń w ramach. Gdy obiekt interfejsu użytkownika generuje polecenia, takich jak `ID_EDIT_CLEAR_ALL`, jeden z obiektów w aplikacji obsługuje polecenie — na ilustracji poniżej obiektu dokumentu `OnEditClearAll` funkcja jest wywoływana za pośrednictwem mapy komunikatów dokumentu.  
  
 ![Polecenia w strukturze](../mfc/media/vc385p1.gif "vc385p1")  
Polecenia w strukturze  
  
 Na rysunku "Polecenia aktualizacji w ramach" poniżej pokazano, jak MFC aktualizuje obiektów interfejsu użytkownika, takich jak elementy menu i przycisków paska narzędzi. Przed menu górnego poziomu lub podczas wykonywania pętli bezczynności w przypadku przycisków paska narzędzi, MFC kieruje polecenie aktualizacji. Na poniższej ilustracji, obiektu dokumentu wywołuje program obsługi poleceń jego aktualizacji `OnUpdateEditClearAll`, aby włączyć lub wyłączyć obiektu interfejsu użytkownika.  
  
 ![Polecenie aktualizacji w ramach](../mfc/media/vc385p2.png "vc385p2")  
Polecenie aktualizacji w ramach  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)

