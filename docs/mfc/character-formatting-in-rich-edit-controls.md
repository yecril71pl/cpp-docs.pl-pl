---
title: Formatowanie znaków w formantach edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
ms.openlocfilehash: a7467f9cd6a14dc6dfc2c03b6eb35f71802454fb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268645"
---
# <a name="character-formatting-in-rich-edit-controls"></a>Formatowanie znaków w formantach edycji wzbogaconej

Można użyć funkcji składowych kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) do formatowania znaków i, aby pobrać informacje o formatowaniu. Znaki można określić krój czcionki, rozmiar, kolor i efektów, takich jak pogrubienie, kursywa, a chronione.

Można zastosować formatowanie przy użyciu znaków [SetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#setselectioncharformat) i [SetWordCharFormat](../mfc/reference/cricheditctrl-class.md#setwordcharformat) funkcji elementów członkowskich. Aby określić bieżący znak formatowanie do zaznaczonego tekstu, należy użyć [GetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#getselectioncharformat) funkcja elementu członkowskiego. [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) struktury jest używany z tych funkcji elementów członkowskich do określenia atrybuty znaków. Jedną z ważnych elementów członkowskich **CHARFORMAT** jest **dwMask**. W `SetSelectionCharFormat` i `SetWordCharFormat`, **dwMask** określa atrybuty znaków zostanie ustawiony przez wywołanie tej funkcji. `GetSelectionCharFormat` Raporty atrybuty pierwszy znak w zaznaczeniu; **dwMask** określa atrybuty, które są spójne zaznaczenia.

Można również pobieranie i ustawianie "domyślnego znaków formatowania," który jest sformatowanie znaków następnie wstawiono. Na przykład jeśli użytkownik wpisze znak aplikacja ustawia domyślny znak odpowiadający ustawieniom lokalnym pogrubienie, ten znak jest pogrubiony. Aby uzyskać i ustawianie domyślnego formatowania znaków, należy użyć [GetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#getdefaultcharformat) i [SetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#setdefaultcharformat) funkcji elementów członkowskich.

Atrybut "chroniony" znak nie zmienia się wygląd tekstu. Jeśli użytkownik próbuje zmodyfikować chroniony plik tekstowy, kontrolki edycji wzbogaconej wysyła okna nadrzędnego **EN_PROTECTED** komunikat powiadomienia, dzięki czemu okno nadrzędne umożliwić lub uniemożliwić zmiany. Ten komunikat powiadomienia, należy je włączyć za pomocą [seteventmask —](../mfc/reference/cricheditctrl-class.md#seteventmask) funkcja elementu członkowskiego. Aby uzyskać więcej informacji na temat maski zdarzeń, zobacz [powiadomień w kontrolce edycji wzbogaconej](../mfc/notifications-from-a-rich-edit-control.md)w dalszej części tego tematu.

Kolor pierwszego planu jest atrybutem znaków, ale kolor tła jest właściwość formantu bogatej edycji. Aby ustawić kolor tła, użyj [SetBackgroundColor](../mfc/reference/cricheditctrl-class.md#setbackgroundcolor) funkcja elementu członkowskiego.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
