---
title: "Globalne klawisze dostępu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 48f3e2a1e0c1461180291342a8cd18682173e8bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="global-hot-keys"></a>Globalne klawisze dostępu
Globalne klawisza dostępu jest skojarzony z oknem nonchild konkretnego. Umożliwia użytkownikowi aktywować okna z dowolnym części systemu. Aplikacja ustawia globalne klawisza dostępu dla określonego okna, wysyłając [WM_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284) komunikat do tego okna. Na przykład jeśli `m_HotKeyCtrl` jest [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) obiektu i `pMainWnd` wskaźnik do okna do aktywacji, gdy zostanie naciśnięty klawisz dostępu, można użyć poniższego kodu, aby skojarzyć klawisz dostępu określonego w kontrolki z Okno wskazywana przez `pMainWnd`.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]  
  
 Przy każdym naciśnięciu klawisza dostępu globalny określone okno odbiera [WM_SYSCOMMAND](http://msdn.microsoft.com/library/windows/desktop/ms646360) komunikat, który określa **SC_HOTKEY** jako typ polecenia. Ten komunikat uaktywniane okna, który odbiera on. Ponieważ ten komunikat nie zawiera żadnych informacji dokładne klucza, który został naciśnięty, za pomocą tej metody nie zezwala na rozróżniania różnych klawisze dostępu, które mogą być dołączane do tej samej okna. Klawisz dostępu pozostaje ważny aż do aplikacji, która wysłała **WM_SETHOTKEY** kończy pracę.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

