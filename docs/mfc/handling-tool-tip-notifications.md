---
title: Obsługa powiadomień dotyczących etykietek narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0449877f9894685ea724e3ad00c028e3e57f50d9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409759"
---
# <a name="handling-tool-tip-notifications"></a>Obsługa powiadomień dotyczących etykietek narzędzi

Po określeniu **TBSTYLE_TOOLTIPS** styl, na pasku narzędzi, tworzy i którymi zarządza formantem etykietki narzędzia. Etykietka narzędzia jest niewielkie okno podręczne zawiera wiersz tekstu opisującego przycisku paska narzędzi. Etykietka narzędzia która jest ukryta, pojawiają się tylko po użytkownik umieszcza kursor na przycisku paska narzędzi i pozostawi je istnieje dla około połowie drugi. Etykietka narzędzia która jest wyświetlana obok kursora.

Przed wyświetleniem etykietka narzędzia która **TTN_NEEDTEXT** komunikatu powiadomienia są wysyłane do okna właściciela paska narzędzi można pobrać opisowy tekst dla przycisku. Jeśli okno właściciela paska narzędzi jest `CFrameWnd` okna narzędzia wskazówki są wyświetlane bez wykonywania dodatkowych działań, ponieważ `CFrameWnd` ma domyślny program obsługi dla **TTN_NEEDTEXT** powiadomień. Jeśli okno właściciela paska narzędzi nie pochodzi od `CFrameWnd`, takie jak widoku okna dialogowego pole lub formularza, należy dodać wpis do okna właściciela mapy komunikatów i zapewniają obsługę powiadamiania w mapie wiadomości. Wpis do okna właściciela mapy wiadomości jest następująca:

[!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]

## <a name="remarks"></a>Uwagi

*memberFxn*<br/>
Funkcja elementu członkowskiego, wywoływana, gdy tekst jest wymagany w przypadku tego przycisku.

Należy zauważyć, że identyfikator etykietki narzędzia jest zawsze 0.

Oprócz **TTN_NEEDTEXT** powiadomienia formantem etykietki narzędzia można wysyłanie powiadomień do formantu paska narzędzi:

|Powiadomienia|Znaczenie|
|------------------|-------------|
|**TTN_NEEDTEXTA**|Formantem etykietki narzędzia wymaga tekst w formacie ASCII (tylko Windows 95)|
|**TTN_NEEDTEXTW**|Formantem etykietki narzędzia wymaga tekst UNICODE (tylko Windows NT)|
|**TBN_HOTITEMCHANGE**|Wskazuje, że gorąca (wyróżniony) element został zmieniony.|
|**NM_RCLICK —**|Wskazuje, że użytkownik ma kliknięto prawym przyciskiem myszy przycisk.|
|**TBN_DRAGOUT**|Wskazuje, użytkownik kliknął element button i przeciągnąć kursor poza przycisk. Umożliwia aplikacji do wdrożenia przeciągnij i upuść na przycisku paska narzędzi. Po odebraniu tego powiadomienia, aplikacji będzie rozpocząć przeciąganie i upuszczanie operacji.|
|**TBN_DROPDOWN —**|Wskazuje, po kliknięciu przycisku, który używa **TBSTYLE_DROPDOWN** stylu.|
|**TBN_GETOBJECT**|Wskazuje, użytkownik przenieść wskaźnik na przycisku, który używa **TBSTYLE_DROPPABLE** stylu.|

Przykład funkcji obsługi i dowiedzieć się więcej o Włączanie etykietek narzędzi, zobacz [etykietek narzędzi](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).

## <a name="see-also"></a>Zobacz też

[Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

