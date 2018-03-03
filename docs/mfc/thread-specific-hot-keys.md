---
title: "Klawisze dostępu właściwe dla wątków | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 89c6ae27dacf5b8637c914c92b6805b1cc405353
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="thread-specific-hot-keys"></a>Klawisze dostępu właściwe dla wątków
Aplikacja ustawia klawisza dostępu właściwe dla wątków ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) przy użyciu systemu Windows **RegisterHotKey** funkcji. Gdy użytkownik naciśnie klawisz dostępu właściwe dla wątków, system Windows zapisuje [WM_HOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646279) wiadomości na początek kolejki komunikatów dla wątku. **WM_HOTKEY** komunikat zawiera wirtualnego kod klucza, shift stanu i Identyfikatora użytkownika określonego klawisza dostępu, który został naciśnięty. Listę standardowych wirtualnego kodów klucza Zobacz Winuser.h. Aby uzyskać więcej informacji dotyczących tej metody, zobacz [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309).  
  
 Należy pamiętać, że flagi stanu shift używane w wywołaniu **RegisterHotKey** nie są takie same jak zwracany przez [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) funkcja członkowska; musisz wykonuje te flagi przed wywołaniem **RegisterHotKey**.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

