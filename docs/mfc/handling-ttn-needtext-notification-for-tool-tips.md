---
title: Obsługa powiadomienia TTN_NEEDTEXT w przypadku etykietek narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TTN_NEEDTEXT
dev_langs:
- C++
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e3b54ebc4c624b3be098f2bbf3ec30c6b70a38c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372434"
---
# <a name="handling-ttnneedtext-notification-for-tool-tips"></a>Obsługa powiadomienia TTN_NEEDTEXT w przypadku etykietek narzędzi

Jako część [Włączanie etykietek narzędzi](../mfc/enabling-tool-tips.md), które ułatwią obsługę **TTN_NEEDTEXT** wiadomości, dodając następujący wpis do okna właściciela mapy komunikatów:

[!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]

*memberFxn*<br/>
Funkcja elementu członkowskiego, wywoływana, gdy tekst jest wymagany w przypadku tego przycisku.

Należy zauważyć, że identyfikator etykietki narzędzia jest zawsze 0.

Deklarowanie funkcji obsługi w definicji klasy w następujący sposób:

[!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]

gdzie kursywą parametry są następujące:

*id*<br/>
Identyfikator formantu wysyłającego powiadomienia. Nie używany. Identyfikator formantu jest pobierana z **NMHDR** struktury.

*pNMHDR*<br/>
Wskaźnik do [NMTTDISPINFO](/windows/desktop/api/commctrl/ns-commctrl-tagnmttdispinfoa) struktury. Ta struktura jest również omówione w dalszych [struktura TOOLTIPTEXT](../mfc/tooltiptext-structure.md).

*pResult*<br/>
Wskaźnik do kodu wyniku można ustawić przed zwróceniem. **TTN_NEEDTEXT** obsługi można zignorować *pResult* parametru.

Na przykład obsługi powiadomień widoku formularza:

[!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]

Wywołaj `EnableToolTips` (ten fragment z `OnInitDialog`):

[!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

