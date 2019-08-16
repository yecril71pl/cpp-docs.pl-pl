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
ms.openlocfilehash: 1f68fb62335219ea498163e6124c8e91e49f2938
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511023"
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd

W tym artykule opisano Włączanie etykietek narzędzi dla kontrolek znajdujących się w oknie, które nie pochodzi od [obiektu CFrameWnd](../mfc/reference/cframewnd-class.md). Etykietki [narzędzi](../mfc/toolbar-tool-tips.md) artykułów zawierają informacje o etykietach narzędzi dla formantów w `CFrameWnd`.

Tematy omówione w tej rodzinie artykułów obejmują:

- [Włączanie etykietek narzędzi](../mfc/enabling-tool-tips.md)

- [Obsługa powiadomienia TTN_NEEDTEXT w przypadku etykietek narzędzi](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)

- [Struktura TOOLTIPTEXT](../mfc/tooltiptext-structure.md)

Etykietki narzędzi są automatycznie wyświetlane dla przycisków i innych kontrolek zawartych w oknie nadrzędnym `CFrameWnd`pochodnym. Dzieje się tak `CFrameWnd` , ponieważ ma domyślną procedurę obsługi dla powiadomienia [TTN_GETDISPINFO](/windows/win32/Controls/ttn-getdispinfo) , która obsługuje powiadomienia **TTN_NEEDTEXT** z kontrolek etykietek narzędzi skojarzonych z kontrolkami.

Jednak ta domyślna procedura obsługi nie jest wywoływana, gdy powiadomienia **TTN_NEEDTEXT** są wysyłane z kontrolki etykietki narzędzia skojarzonej z kontrolką w oknie `CFrameWnd`, które nie jest, takie jak kontrolka w oknie dialogowym lub widok formularza. W związku z tym, niezbędne jest udostępnienie funkcji obsługi komunikatu powiadomienia **TTN_NEEDTEXT** w celu wyświetlenia etykietek narzędzi dla formantów podrzędnych.

Domyślne wskazówki dotyczące narzędzi podane dla systemu Windows przez [CWnd:: EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips) nie mają skojarzonych z nimi tekstu. Aby pobrać tekst etykietki narzędzia do wyświetlenia, powiadomienie **TTN_NEEDTEXT** jest wysyłane do okna nadrzędnego kontrolki etykietki narzędzia tuż przed wyświetleniem okna etykietki narzędzia. Jeśli nie ma programu obsługi dla tej wiadomości, aby przypisać pewną wartość do elementu członkowskiego *pszText* struktury **ToolTipText** , nie będzie wyświetlany tekst etykietki narzędzia.

## <a name="see-also"></a>Zobacz także

[Etykietki narzędzi](../mfc/tool-tips.md)
