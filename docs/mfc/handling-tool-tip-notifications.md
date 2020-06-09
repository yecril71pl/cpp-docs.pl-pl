---
title: Obsługa powiadomień dotyczących etykietek narzędzi
ms.date: 11/04/2016
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
ms.openlocfilehash: 41e3dbfc2269f5fbf3c12dc00c19f8a2253fd16a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626445"
---
# <a name="handling-tool-tip-notifications"></a>Obsługa powiadomień dotyczących etykietek narzędzi

Po określeniu stylu **TBSTYLE_TOOLTIPS** pasek narzędzi tworzy formant etykietki narzędzia i zarządza nim. Etykietka narzędzia jest małym okienkiem podręcznym zawierającym wiersz tekstu opisujący przycisk paska narzędzi. Etykietka narzędzia jest ukryta, pojawia się tylko wtedy, gdy użytkownik umieści kursor na przycisku paska narzędzi i pozostawia go na około pół sekundy. Zostanie wyświetlona etykietka narzędzia obok kursora.

Przed wyświetleniem etykietki narzędzia do okna właściciela paska narzędzi zostanie wysłany komunikat z powiadomieniem o **TTN_NEEDTEXT** . Jeśli okno właściciela paska narzędzi jest `CFrameWnd` oknem, etykietki narzędzi są wyświetlane bez dodatkowych nakładów pracy, ponieważ `CFrameWnd` program ma domyślną procedurę obsługi dla powiadomienia **TTN_NEEDTEXT** . Jeśli okno właściciela paska narzędzi nie pochodzi od elementu `CFrameWnd` , takiego jak okno dialogowe lub widok formularza, należy dodać wpis do mapy komunikatów okna właściciela i udostępnić program obsługi powiadomień w mapie wiadomości. Wpis w mapie komunikatów Twojego okna właściciela jest następujący:

[!code-cpp[NVC_MFCControlLadenDialog#40](codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]

## <a name="remarks"></a>Uwagi

*memberFxn*<br/>
Funkcja członkowska, która ma być wywoływana, gdy dla tego przycisku jest wymagany tekst.

Należy pamiętać, że identyfikator etykietki narzędzia ma zawsze wartość 0.

Oprócz powiadomienia **TTN_NEEDTEXT** , formant etykietki narzędzia może wysyłać następujące powiadomienia do kontrolki paska narzędzi:

|Powiadomienie|Znaczenie|
|------------------|-------------|
|**TTN_NEEDTEXTA**|Kontrolka etykietki narzędzia wymaga tekstu ASCII (tylko system Windows 95)|
|**TTN_NEEDTEXTW**|Kontrolka etykietki narzędzia wymaga tekstu UNICODE (tylko system Windows NT)|
|**TBN_HOTITEMCHANGE**|Wskazuje, że element gorąca (wyróżniony) został zmieniony.|
|**NM_RCLICK**|Oznacza, że użytkownik kliknął przycisk prawym przyciskiem myszy.|
|**TBN_DRAGOUT**|Oznacza, że użytkownik kliknął przycisk i przeciąga wskaźnik poza przycisk. Dzięki temu aplikacja może zaimplementować przeciąganie i upuszczanie z przycisku paska narzędzi. Po odebraniu tego powiadomienia aplikacja rozpocznie operację przeciągania i upuszczania.|
|**TBN_DROPDOWN**|Oznacza, że użytkownik kliknął przycisk, który używa stylu **TBSTYLE_DROPDOWN** .|
|**TBN_GETOBJECT**|Oznacza, że użytkownik przeniósł wskaźnik myszy nad przyciskiem, który używa stylu **TBSTYLE_DROPPABLE** .|

Aby zapoznać się z przykładową funkcją obsługi i uzyskać więcej informacji na temat włączania etykietek narzędzi, zobacz [porady dotyczące narzędzi](tool-tips-in-windows-not-derived-from-cframewnd.md).

## <a name="see-also"></a>Zobacz też

[Korzystanie z CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[Formanty](controls-mfc.md)
