---
title: Uzyskiwanie dostępu do osadzonego formantu kalendarza miesięcznego
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], accessing month calendar
- CDateTimeCtrl class [MFC], accessing embedded control
- month calendar controls [MFC], embedded in date/time picker
- CMonthCalCtrl class [MFC], changing the font
- month calendar controls [MFC], changing the font
- DateTimePicker control [MFC]
ms.assetid: 355e97ed-cf81-4df3-a2f8-9ddbbde93227
ms.openlocfilehash: 66a9ef7fd49ea81ddac4779aa6d1c3f12fbe4c55
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617375"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>Uzyskiwanie dostępu do osadzonego formantu kalendarza miesięcznego

Dostęp do obiektu formantu kalendarza z osadzonym miesiącem można uzyskać z `CDateTimeCtrl` obiektu z wywołaniem funkcji składowej [GetMonthCalCtrl](reference/cdatetimectrl-class.md#getmonthcalctrl) .

> [!NOTE]
> Formant kalendarza z osadzonym miesiącem jest używany tylko wtedy, gdy kontrolka selektora daty i godziny nie ma ustawionego stylu **DTS_UPDOWN** .

Jest to przydatne, jeśli chcesz zmodyfikować pewne atrybuty przed wyświetleniem osadzonego formantu. Aby to osiągnąć, należy obsłużyć powiadomienie **DTN_DROPDOWN** , pobrać formant kalendarza miesięcznego (przy użyciu [Korzystanie CDateTimeCtrl:: GetMonthCalCtrl](reference/cdatetimectrl-class.md#getmonthcalctrl)) i wprowadzić modyfikacje. Niestety, formant kalendarza miesięcznego nie jest trwały.

Innymi słowy, gdy użytkownik zażąda wyświetlania kontrolki kalendarza miesięcznego, zostanie utworzony nowy, dwumiesięczny formant kalendarza (przed powiadomieniem **DTN_DROPDOWN** ). Formant jest niszczony (po **DTN_CLOSEUP** powiadomienia), gdy zostanie odrzucony przez użytkownika. Oznacza to, że wszelkie modyfikowane atrybuty przed wyświetleniem osadzonego formantu są tracone, gdy osadzony formant zostanie odrzucony.

Poniższy przykład ilustruje tę procedurę przy użyciu programu obsługi powiadomienia **DTN_DROPDOWN** . Kod zmienia kolor tła kontrolki kalendarza miesięcznego z wywołaniem do [SetMonthCalColor](reference/cdatetimectrl-class.md#setmonthcalcolor), szarym. Kod jest następujący:

[!code-cpp[NVC_MFCControlLadenDialog#5](codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

Jak wspomniano wcześniej, wszystkie modyfikacje właściwości kontrolki kalendarza miesięcznego są tracone z dwoma wyjątkami, gdy osadzony formant zostanie odrzucony. Pierwszy wyjątek, kolory kontrolki kalendarza miesięcznego, został już omówiony. Drugi wyjątek jest czcionką używaną przez formant kalendarza miesięcznego. Możesz zmodyfikować domyślną czcionkę, wykonując wywołanie [Korzystanie CDateTimeCtrl:: SetMonthCalFont](reference/cdatetimectrl-class.md#setmonthcalfont), przekazując uchwyt istniejącej czcionki. Poniższy przykład (gdzie `m_dtPicker` jest obiektem sterowania datą i godziną) ilustruje jedną z możliwych metod:

[!code-cpp[NVC_MFCControlLadenDialog#6](codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

Po zmianie czcionki z wywołaniem `CDateTimeCtrl::SetMonthCalFont` nowej czcionki jest zachowywana i używana przy następnym wyświetleniu kalendarza miesiąca.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CDateTimeCtrl](using-cdatetimectrl.md)<br/>
[Formanty](controls-mfc.md)
