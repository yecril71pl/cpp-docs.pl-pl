---
title: Ustawianie klawisza dostępu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3987ddee98ae35e02a181e38cd71f181801aeb61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379648"
---
# <a name="setting-a-hot-key"></a>Ustawianie klawisza dostępu
Aplikacja może używać informacji dostarczonych przez klawisza dostępu ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) formantu w jeden z dwóch sposobów:  
  
-   Ustawianie globalnych klawisza dostępu do aktywacji okna nonchild wysyłając [WM_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284) wiadomości do okna do aktywacji.  
  
-   Konfigurowanie klawisza dostępu właściwe dla wątków przez wywołanie funkcji systemu Windows [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

