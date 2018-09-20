---
title: Uzyskiwanie dostępu do miesiąca osadzonego formantu kalendarza | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DateTimePicker control [MFC], accessing month calendar
- CDateTimeCtrl class [MFC], accessing embedded control
- month calendar controls [MFC], embedded in date/time picker
- CMonthCalCtrl class [MFC], changing the font
- month calendar controls [MFC], changing the font
- DateTimePicker control [MFC]
ms.assetid: 355e97ed-cf81-4df3-a2f8-9ddbbde93227
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a92660223c84c5f53bc848e72b03316602180d36
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430296"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>Uzyskiwanie dostępu do osadzonego formantu kalendarza miesięcznego

Obiekt formantu kalendarza osadzone miesiąca jest możliwy z `CDateTimeCtrl` obiektu z wywołaniem [GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl) funkcja elementu członkowskiego.

> [!NOTE]
>  Formant kalendarza miesięcznego osadzony jest używana tylko wtedy, gdy kontrolka selektora daty i godziny nie ma **DTS_UPDOWN** stylu zestawu.

Jest to przydatne, jeśli chcesz zmodyfikować niektóre atrybuty, przed wyświetleniem osadzonego formantu. W tym celu należy obsługiwać **dtn_dropdown —** powiadomień, pobierania formant kalendarza miesięcznego (przy użyciu [CDateTimeCtrl::GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)) i wprowadzić modyfikacje. Niestety formant kalendarza miesięcznego nie jest trwały.

Innymi słowy, gdy użytkownik zażąda wyświetlanie formant kalendarza miesięcznego, formant kalendarza nowego miesiąca jest tworzony (przed **dtn_dropdown —** powiadomień). Zniszczenia kontrolki (po **dtn_closeup —** powiadomień) podczas ukryty przez użytkownika. Oznacza to, wszelkie atrybuty, które zmodyfikować przed wyświetleniem formantu osadzonego zostaną utracone, gdy osadzonego formantu jest odrzucane.

W poniższym przykładzie pokazano tej procedury przy użyciu programu obsługi dla **dtn_dropdown —** powiadomień. Kod zmienia kolor tła kontrolki kalendarza miesięcznego wywołaniem [SetMonthCalColor](../mfc/reference/cdatetimectrl-class.md#setmonthcalcolor), na szary. Kod jest w następujący sposób:

[!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

Jak wspomniano wcześniej, wszelkie modyfikacje właściwości formantu kalendarza miesięcznego podczas osadzonego formantu jest odrzucane są tracone, z dwoma wyjątkami. Pierwszy wyjątek kolory formant kalendarza miesięcznego, Omówiliśmy już. Drugi wyjątek to czcionka używana przez formant kalendarza miesięcznego. Można zmodyfikować domyślną czcionkę wywołuje element [CDateTimeCtrl::SetMonthCalFont](../mfc/reference/cdatetimectrl-class.md#setmonthcalfont), przekazywanie uchwyt istniejących czcionki. Poniższy przykład (gdzie `m_dtPicker` jest obiektem kontrolki Data i godzina) przedstawia jedną z możliwych metod:

[!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

Po czcionka została zmieniona, z wywołaniem `CDateTimeCtrl::SetMonthCalFont`, przechowywanym i wykorzystywanym przy następnym miesięczny kalendarz zostanie wyświetlona nowa czcionka.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

