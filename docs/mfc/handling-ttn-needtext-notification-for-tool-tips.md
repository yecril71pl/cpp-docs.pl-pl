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
ms.openlocfilehash: 75850dbf92587cf654d4f7a39ea54af1fd9dd5bd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620084"
---
# <a name="handling-ttn_needtext-notification-for-tool-tips"></a>Obsługa powiadomienia TTN_NEEDTEXT w przypadku etykietek narzędzi

W ramach [włączania etykietek narzędzi](enabling-tool-tips.md)można obsłużyć **TTN_NEEDTEXT** komunikat, dodając następujący wpis do mapy komunikatów Twojego okna właściciela:

[!code-cpp[NVC_MFCControlLadenDialog#40](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]

*memberFxn*<br/>
Funkcja członkowska, która ma być wywoływana, gdy dla tego przycisku jest wymagany tekst.

Należy pamiętać, że identyfikator etykietki narzędzia ma zawsze wartość 0.

Zadeklaruj funkcję programu obsługi w definicji klasy w następujący sposób:

[!code-cpp[NVC_MFCControlLadenDialog#53](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]

gdzie są pisane kursywnie parametry:

*#c1*<br/>
Identyfikator kontrolki, która wysłała powiadomienie. Nie używany. Identyfikator kontrolki jest pobierany ze struktury **NMHDR** .

*pNMHDR*<br/>
Wskaźnik do struktury [NMTTDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmttdispinfow) . Ta struktura jest również omówiona dokładniej w [strukturze ToolTipText](tooltiptext-structure.md).

*pResult*<br/>
Wskaźnik do kodu wyniku, który można ustawić przed zwróceniem. Procedury obsługi **TTN_NEEDTEXT** mogą ignorować parametr *pResult* .

Przykładem programu obsługi powiadomień w widoku formularza:

[!code-cpp[NVC_MFCControlLadenDialog#54](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]

Wywołanie `EnableToolTips` (ten fragment został pobrany z `OnInitDialog` ):

[!code-cpp[NVC_MFCControlLadenDialog#55](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd](tool-tips-in-windows-not-derived-from-cframewnd.md)
