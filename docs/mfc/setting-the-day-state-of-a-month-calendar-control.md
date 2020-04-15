---
title: Ustawianie stanu dnia formantu kalendarza miesięcznego
ms.date: 11/04/2016
f1_keywords:
- MCN_GETDAYSTATE
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
ms.openlocfilehash: 9892f2d853687787dd76428fc9bc95f3a4f74565
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365428"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Ustawianie stanu dnia formantu kalendarza miesięcznego

Jednym z atrybutów kontroli kalendarza miesiąca jest możliwość przechowywania informacji, określane jako stan dnia kontroli, dla każdego dnia miesiąca. Te informacje są używane do podkreślenia niektórych dat dla aktualnie wyświetlanego miesiąca.

> [!NOTE]
> Obiekt `CMonthCalCtrl` musi mieć styl MCS_DAYSTATE, aby wyświetlić informacje o stanie dnia.

Informacje o stanie dnia są wyrażane jako typ danych 32-bitowych, **MONTHDAYSTATE**. Każdy bit w polu bitowym **MONTHDAYSTATE** (od 1 do 31) reprezentuje stan dnia w miesiącu. Jeśli bit jest włączony, odpowiedni dzień będzie wyświetlany pogrubioną czcionką; w przeciwnym razie będzie wyświetlany bez nacisku.

Istnieją dwie metody ustawiania stanu dnia kontroli kalendarza miesiąca: jawnie z wywołaniem [CMonthCalCtrl::SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) lub obsługi MCN_GETDAYSTATE komunikat powiadomienia.

## <a name="handling-the-mcn_getdaystate-notification-message"></a>Obsługa komunikatu powiadomienia o MCN_GETDAYSTATE

Komunikat MCN_GETDAYSTATE jest wysyłany przez formant, aby określić, jak dni w widocznych miesiącach powinny być wyświetlane.

> [!NOTE]
> Ponieważ formant buforuje poprzednie i kolejne miesiące, w odniesieniu do widocznego miesiąca, otrzymasz to powiadomienie za każdym razem, gdy zostanie wybrany nowy miesiąc.

Aby poprawnie obsługiwać ten komunikat, należy określić, ile miesięcy dni informacje o stanie jest wymagane dla, zainicjować tablicę **MONTHDAYSTATE** struktur z odpowiednimi wartościami i zainicjować powiązanego elementu członkowskiego struktury z nowymi informacjami. Poniższa procedura, szczegółowo niezbędne kroki, zakłada, `CMonthCalCtrl` że masz obiekt o nazwie *m_monthcal* i tablicy **MONTHDAYSTATE** obiektów, *mdState*.

#### <a name="to-handle-the-mcn_getdaystate-notification-message"></a>Aby obsłużyć komunikat powiadomienia o MCN_GETDAYSTATE

1. Za pomocą [Kreatora klas](reference/mfc-class-wizard.md)dodaj program obsługi powiadomień dla MCN_GETDAYSTATE do obiektu *m_monthcal* (patrz [Mapowanie komunikatów do funkcji).](../mfc/reference/mapping-messages-to-functions.md)

1. W treści programu obsługi dodaj następujący kod:

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   W przykładzie konwertuje wskaźnik *pNMHDR* na odpowiedni typ, a następnie określa, ile miesięcy informacji jest wymaganych (`pDayState->cDayState`). Dla każdego miesiąca bieżące`pDayState->prgDayState[i]`pole bitowe ( ) jest inicjowane do zera, a następnie ustawiane są wymagane daty (w tym przypadku 15 każdego miesiąca).

## <a name="see-also"></a>Zobacz też

[Korzystanie z CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)
