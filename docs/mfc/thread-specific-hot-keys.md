---
title: Klawisze dostępu właściwe dla wątków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdd6cf2f2bb76c30f4cc00d75eb55d7d2c01fa7e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="thread-specific-hot-keys"></a>Klawisze dostępu właściwe dla wątków
Aplikacja ustawia klawisza dostępu właściwe dla wątków ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) przy użyciu systemu Windows **RegisterHotKey** funkcji. Gdy użytkownik naciśnie klawisz dostępu właściwe dla wątków, system Windows zapisuje [WM_HOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646279) wiadomości na początek kolejki komunikatów dla wątku. **WM_HOTKEY** komunikat zawiera wirtualnego kod klucza, shift stanu i Identyfikatora użytkownika określonego klawisza dostępu, który został naciśnięty. Listę standardowych wirtualnego kodów klucza Zobacz Winuser.h. Aby uzyskać więcej informacji dotyczących tej metody, zobacz [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309).  
  
 Należy pamiętać, że flagi stanu shift używane w wywołaniu **RegisterHotKey** nie są takie same jak zwracany przez [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) funkcja członkowska; musisz wykonuje te flagi przed wywołaniem **RegisterHotKey**.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

