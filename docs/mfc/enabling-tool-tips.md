---
title: Włączanie etykietek narzędzi
ms.date: 11/04/2016
helpviewer_keywords:
- initializing tool tips [MFC]
- enabling tool tips [MFC]
- tool tips [MFC], initializing
- tool tips [MFC], enabling
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
ms.openlocfilehash: 892ed76ef7e021544505600110cd2569d6078312
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174955"
---
# <a name="enabling-tool-tips"></a>Włączanie etykietek narzędzi

Można włączyć narzędzie Porada obsługę formantów podrzędnych okna (np. kontrolki na formularzu widoku lub okno dialogowe).

### <a name="to-enable-tool-tips-for-the-child-controls-of-a-window"></a>Aby włączyć etykietki narzędzi dla formantów podrzędnych okna

1. Wywołaj `EnableToolTips` okna, dla którego chcesz podać etykietek narzędzi.

1. Podaj ciąg dla każdego formantu w Twojej [powiadomienia TTN_NEEDTEXT](../mfc/handling-ttn-needtext-notification-for-tool-tips.md) programu obsługi. Program obsługi jest w mapie komunikatów okna, który zawiera formanty podrzędne (na przykład klasy widoku formularza). Ta procedura obsługi powinna wywołać funkcję, identyfikuje formant i ustawia **pszText** do określania tekstu, używane przez formantem etykietki narzędzia.

## <a name="see-also"></a>Zobacz także

[Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)
