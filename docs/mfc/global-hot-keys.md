---
title: Globalne klawisze dostępu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2ef1e2135ebd780938fb0ed194a93058fd010f6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209157"
---
# <a name="global-hot-keys"></a>Globalne klawisze dostępu
Globalny klawisz dostępu jest skojarzony z oknem nonchild określonej. Umożliwia użytkownikowi Uaktywnij okno z dowolnej części systemu. Aplikacja ustawia globalny klawisz dostępu określonego okna, wysyłając [WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) komunikat do tego okna. Na przykład jeśli `m_HotKeyCtrl` jest [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) obiektu i `pMainWnd` jest wskaźnikiem do okna, który będzie aktywowany po naciśnięciu klawisza dostępu, można Użyj poniższego kodu, aby skojarzyć klawisz dostępu określonego w kontrolki z Okno wskazywany przez `pMainWnd`.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]  
  
 Zawsze, gdy użytkownik naciśnie globalny klawisz dostępu, określone okno odbiera [WM_SYSCOMMAND](/windows/desktop/menurc/wm-syscommand) komunikat, który określa **SC_HOTKEY** jako typ polecenia. Ten komunikat aktywuje również okno, które otrzymuje go. Ponieważ ten komunikat nie zawiera żadnych informacji na temat dokładnego klucza, który został naciśnięty, przy użyciu tej metody nie zezwala na rozróżniania różne klawisze dostępu, które mogą być dołączone do tego samego okna. Klawisz skrótu pozostanie ważny aż do aplikacji, która wysłała **WM_SETHOTKEY** kończy działanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

