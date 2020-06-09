---
title: Włączanie etykietek narzędzi
ms.date: 11/04/2016
helpviewer_keywords:
- initializing tool tips [MFC]
- enabling tool tips [MFC]
- tool tips [MFC], initializing
- tool tips [MFC], enabling
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
ms.openlocfilehash: bdd5c54f9174c42e17db0be7e13ea31acfea2dcf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615727"
---
# <a name="enabling-tool-tips"></a>Włączanie etykietek narzędzi

Można włączyć obsługę etykiet podrzędnych dla kontrolek potomnych okna (takich jak kontrolki w widoku formularza lub okna dialogowego).

### <a name="to-enable-tool-tips-for-the-child-controls-of-a-window"></a>Aby włączyć etykietki narzędzi dla formantów podrzędnych okna

1. Wywołaj `EnableToolTips` okno, dla którego chcesz podać etykietki narzędzi.

1. Podaj ciąg dla każdej kontrolki w programie obsługi [powiadomień TTN_NEEDTEXT](handling-ttn-needtext-notification-for-tool-tips.md) . Program obsługi znajduje się w mapie komunikatów okna, które zawiera kontrolki podrzędne (na przykład Klasa widoku formularza). Ta procedura obsługi powinna wywołać funkcję, która identyfikuje kontrolkę i ustawia **pszText** do określenia tekstu używanego przez formant etykietki narzędzia.

## <a name="see-also"></a>Zobacz też

[Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd](tool-tips-in-windows-not-derived-from-cframewnd.md)
