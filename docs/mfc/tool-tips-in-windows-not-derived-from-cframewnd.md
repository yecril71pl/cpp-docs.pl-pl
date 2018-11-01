---
title: Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd
ms.date: 11/04/2016
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
ms.openlocfilehash: 2545bda725428835c256ad81edc9070bd004d474
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620301"
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd

Rodzina tego artykułu opisano włączanie etykietek narzędzi dla formantów znajdujących się w oknie, który nie pochodzi od [CFrameWnd](../mfc/reference/cframewnd-class.md). Artykuł [etykietek narzędzi pasków narzędzi](../mfc/toolbar-tool-tips.md) informacje na temat etykietek narzędzi dla formantów w `CFrameWnd`.

Tematy omówione w tej rodzinie artykułu obejmują:

- [Włączanie etykietek narzędzi](../mfc/enabling-tool-tips.md)

- [Obsługa powiadomienia TTN_NEEDTEXT w przypadku etykietek narzędzi](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)

- [Struktura TOOLTIPTEXT](../mfc/tooltiptext-structure.md)

Etykietki narzędzi są automatycznie wyświetlane w przypadku przycisków i innych kontrolek znajdujących się w oknie nadrzędnym pochodną `CFrameWnd`. Jest to spowodowane `CFrameWnd` ma domyślny program obsługi dla [TTN_GETDISPINFO](/windows/desktop/Controls/ttn-getdispinfo) powiadomienie, które obsługuje **TTN_NEEDTEXT** powiadomienia za pomocą narzędzia Porada formanty powiązane z kontrolkami.

Jednak to domyślny program obsługi nie jest wywoływana, gdy **TTN_NEEDTEXT** powiadomienie jest wysyłane z formantem etykietki narzędzia, powiązany z kontrolką w oknie, który nie jest `CFrameWnd`, takie jak formant w okno dialogowe lub widok formularza. Dlatego jest niezbędne do zapewnienia funkcji obsługi, aby uzyskać **TTN_NEEDTEXT** komunikatu powiadomienia w celu wyświetlenia etykietki narzędzi dla formantów podrzędnych.

Domyślnej etykietki narzędzia, podany dla aplikacji dla systemu windows przez [CWnd::EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips) nie zawierają tekstu skojarzonych z nimi. Aby pobrać tekst etykietki narzędzia wyświetlić, **TTN_NEEDTEXT** powiadomienie jest wysyłane do okna nadrzędnego formantem etykietki narzędzia, po prostu, przed wyświetleniem okna narzędzia porada. Jeśli nie istnieje żadna procedura obsługi dla tego komunikatu przypisać jakąś wartość, aby *pszText* członkiem **TOOLTIPTEXT** struktury, nie będzie żadnych tekst wyświetlany dla etykietki narzędzia.

## <a name="see-also"></a>Zobacz też

[Etykietki narzędzi](../mfc/tool-tips.md)

