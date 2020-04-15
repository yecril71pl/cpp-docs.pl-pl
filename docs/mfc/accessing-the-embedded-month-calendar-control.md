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
ms.openlocfilehash: 69270cc5663406f2c5d38ffccdbd35f39298a3d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354183"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>Uzyskiwanie dostępu do osadzonego formantu kalendarza miesięcznego

Obiekt sterujący osadzonego kalendarza miesiąca `CDateTimeCtrl` jest dostępny z obiektu za pomocą wywołania funkcji elementu członkowskiego [GetMonthCalCtrl.](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)

> [!NOTE]
> Formant osadzonego kalendarza miesiąca jest używany tylko wtedy, gdy formant selektora daty i godziny nie ma ustawionego stylu **DTS_UPDOWN.**

Jest to przydatne, jeśli chcesz zmodyfikować niektóre atrybuty przed wyświetleniem formantu osadzonego. Aby to osiągnąć, obsłużyć powiadomienie **DTN_DROPDOWN,** pobrać formant kalendarza miesiąca (przy użyciu [CDateTimeCtrl::GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)) i dokonać zmian. Niestety kontrola kalendarza miesiąca nie jest trwała.

Innymi słowy, gdy użytkownik żąda wyświetlania formantu kalendarza miesiąca, tworzony jest kontrolka kalendarza nowego miesiąca (przed **powiadomieniem DTN_DROPDOWN).** Formant jest niszczony (po **powiadomieniu DTN_CLOSEUP)** po odrzuceniu przez użytkownika. Oznacza to, że wszystkie atrybuty, które można zmodyfikować, przed wyświetlaniem formantu osadzonego są tracone, gdy osadzony formant jest odrzucany.

W poniższym przykładzie przedstawiono tę procedurę, przy użyciu programu obsługi dla **powiadomienia DTN_DROPDOWN.** Kod zmienia kolor tła kontrolki kalendarza miesiąca, z wywołaniem [SetMonthCalColor](../mfc/reference/cdatetimectrl-class.md#setmonthcalcolor), na szary. Kod jest następujący:

[!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

Jak wspomniano wcześniej, wszystkie modyfikacje właściwości formantu kalendarza miesiąca zostaną utracone, z dwoma wyjątkami, gdy osadzony formant zostanie odrzucony. Pierwszy wyjątek, kolory kontroli kalendarza miesiąca, został już omówiony. Drugi wyjątek to czcionka używana przez formant kalendarza miesiąca. Czcionkę domyślną można zmodyfikować, wywołując [polecenie CDateTimeCtrl::SetMonthCalFont](../mfc/reference/cdatetimectrl-class.md#setmonthcalfont), przekazując uchwyt istniejącej czcionki. Poniższy przykład `m_dtPicker` (gdzie jest obiekt kontroli daty i godziny) pokazuje jedną możliwą metodę:

[!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

Po zmianie czcionki, z `CDateTimeCtrl::SetMonthCalFont`wywołaniem, nowa czcionka jest przechowywana i używana następnym razem, gdy kalendarz miesiąca ma być wyświetlany.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)
