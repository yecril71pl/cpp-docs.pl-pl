---
title: "On_update_command_ui — makro | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ON_UPDATE_COMMAND_UI
dev_langs: C++
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 64b9c77d8c851364790d61e7844b46f25880168c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="onupdatecommandui-macro"></a>ON_UPDATE_COMMAND_UI — Makro
Użyj **właściwości** okno, aby połączyć obiekt interfejsu użytkownika do programu obsługi aktualizacji poleceń w obiekcie docelowym polecenia. Automatycznie połączy Identyfikatora obiektu interfejsu użytkownika do `ON_UPDATE_COMMAND_UI` makro i utworzyć program obsługi w obiekcie, który będzie obsługiwał aktualizacji. Zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md) Aby uzyskać więcej informacji.  
  
 Na przykład, aby zaktualizować wyczyść wszystkie polecenia w menu Edycja programu, należy użyć **właściwości** okno, aby dodać wpis mapy komunikatów w wybranej klasy deklaracji funkcji programu obsługi aktualizacji poleceń o nazwie `OnUpdateEditClearAll` w klasie Deklaracja i szablonu funkcji jest puste w pliku implementacji klasy. Prototyp funkcja wygląda następująco:  
  
 [!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]  
  
 Wszystkie programy obsługi, pokazuje funkcji, takich jak **afx_msg** — słowo kluczowe. Tak jak wszystkie programy obsługi aktualizacji, zajmuje jeden argument, wskaźnik do `CCmdUI` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: aktualizowanie obiektów interfejsu użytkownika](../mfc/how-to-update-user-interface-objects.md)

