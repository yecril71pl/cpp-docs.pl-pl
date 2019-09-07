---
title: Formatowanie znaków w formantach edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
ms.openlocfilehash: 3ff9be0909a36179802e5f210e728c2bf57b1f02
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739514"
---
# <a name="character-formatting-in-rich-edit-controls"></a>Formatowanie znaków w formantach edycji wzbogaconej

Można używać funkcji składowych formantu edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) do formatowania znaków i pobierania informacji o formatowaniu. W przypadku znaków można określić krój, rozmiar, kolor i efekty, takie jak pogrubienie, kursywa i ochrona.

Formatowanie znaków można zastosować przy użyciu funkcji Członkowskich [SetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#setselectioncharformat) i [SetWordCharFormat](../mfc/reference/cricheditctrl-class.md#setwordcharformat) . Aby określić bieżące formatowanie znaków dla zaznaczonego tekstu, użyj funkcji składowej [GetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#getselectioncharformat) . Struktura [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) jest używana z tymi funkcjami składowymi w celu określenia atrybutów znaków. Jednym z ważnych elementów członkowskich **Charformat** jest **dwMask**. W `SetSelectionCharFormat` i`SetWordCharFormat`, **dwMask** określa, które atrybuty znaków będą ustawiane przez to wywołanie funkcji. `GetSelectionCharFormat`raportuje atrybuty pierwszego znaku w zaznaczeniu; **dwMask** określa atrybuty, które są spójne w zaznaczeniu.

Możesz również uzyskać i ustawić "domyślne formatowanie znaków", które jest formatowaniem stosowanym do dowolnych później wstawionych znaków. Na przykład jeśli aplikacja ustawi domyślne formatowanie znaków na pogrubiony, a użytkownik wpisze znak, ten znak jest pogrubiony. Aby uzyskać i ustawić domyślne formatowanie znaków, użyj funkcji składowych [GetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#getdefaultcharformat) i [SetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#setdefaultcharformat) .

Atrybut znaku "Protected" nie zmienia wyglądu tekstu. Jeśli użytkownik próbuje zmodyfikować chroniony tekst, kontrolka edycji wzbogaconej wyśle do okna nadrzędnego komunikat z powiadomieniem o **EN_PROTECTED** , zezwalając na okno nadrzędne na zezwolenie lub zablokowanie zmiany. Aby odebrać ten komunikat z powiadomieniem, należy włączyć go przy użyciu funkcji składowej [SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask) . Aby uzyskać więcej informacji na temat maski zdarzeń, zobacz [powiadomienia z kontrolki edycji wzbogaconej](../mfc/notifications-from-a-rich-edit-control.md)w dalszej części tego tematu.

Kolor pierwszego planu jest atrybutem znaku, ale kolor tła jest właściwością kontrolki edycji wzbogaconej. Aby ustawić kolor tła, użyj funkcji składowej [SetBackgroundColor](../mfc/reference/cricheditctrl-class.md#setbackgroundcolor) .

## <a name="see-also"></a>Zobacz także

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
