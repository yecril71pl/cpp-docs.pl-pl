---
title: Obsługa powiadomienia TTN_NEEDTEXT w przypadku etykietek narzędzi
ms.date: 11/04/2016
f1_keywords:
- TTN_NEEDTEXT
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
ms.openlocfilehash: a63154f3da539676f31709899568b6486dc6017e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508528"
---
# <a name="handling-ttn_needtext-notification-for-tool-tips"></a>Obsługa powiadomienia TTN_NEEDTEXT w przypadku etykietek narzędzi

W ramach [włączania etykietek narzędzi](../mfc/enabling-tool-tips.md)można obsługiwać komunikat **TTN_NEEDTEXT** , dodając następujący wpis do mapy komunikatów Twojego okna właściciela:

[!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]

*memberFxn*<br/>
Funkcja członkowska, która ma być wywoływana, gdy dla tego przycisku jest wymagany tekst.

Należy pamiętać, że identyfikator etykietki narzędzia ma zawsze wartość 0.

Zadeklaruj funkcję programu obsługi w definicji klasy w następujący sposób:

[!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]

gdzie są pisane kursywnie parametry:

*id*<br/>
Identyfikator kontrolki, która wysłała powiadomienie. Nie używany. Identyfikator kontrolki jest pobierany ze struktury **NMHDR** .

*pNMHDR*<br/>
Wskaźnik do struktury [NMTTDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmttdispinfow) . Ta struktura jest również omówiona dokładniej w [strukturze ToolTipText](../mfc/tooltiptext-structure.md).

*pResult*<br/>
Wskaźnik do kodu wyniku, który można ustawić przed zwróceniem. Procedury obsługi **TTN_NEEDTEXT** mogą ignorować parametr *pResult* .

Przykładem programu obsługi powiadomień w widoku formularza:

[!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]

Wywołanie `EnableToolTips` (ten fragment został pobrany `OnInitDialog`z):

[!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]

## <a name="see-also"></a>Zobacz także

[Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)
