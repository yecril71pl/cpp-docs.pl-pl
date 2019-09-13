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
ms.openlocfilehash: b8a91c8b0c3bdef9256628b9226c5f3ff154ed7d
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907527"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Ustawianie stanu dnia formantu kalendarza miesięcznego

Jednym z atrybutów formantu kalendarza miesięcznego jest możliwość przechowywania informacji, nazywanych stanem dnia kontrolki, dla każdego dnia miesiąca. Te informacje służą do podkreślenia niektórych dat dla aktualnie wyświetlanego miesiąca.

> [!NOTE]
>  Aby `CMonthCalCtrl` wyświetlić informacje o stanie dnia, obiekt musi mieć styl MCS_DAYSTATE.

Informacje o stanie dnia są wyrażane jako 32-bitowy typ danych, **MONTHDAYSTATE**. Każdy bit w **MONTHDAYSTATE** polu bitowym (od 1 do 31) reprezentuje stan dnia w miesiącu. Jeśli bit jest włączony, odpowiedni dzień będzie wyświetlany pogrubiony; w przeciwnym razie będzie wyświetlana bez wyróżniania.

Istnieją dwie metody ustawiania stanu dnia formantu kalendarza miesięcznego: jawne wywołanie [CMonthCalCtrl:: SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) lub przez obsługę wiadomości z powiadomieniem MCN_GETDAYSTATE.

## <a name="handling-the-mcn_getdaystate-notification-message"></a>Obsługa komunikatu powiadomienia MCN_GETDAYSTATE

Komunikat MCN_GETDAYSTATE jest wysyłany przez formant, aby określić, jak powinny być wyświetlane dni w widocznych miesiącach.

> [!NOTE]
>  Ponieważ kontrolka przechowuje w pamięci podręcznej poprzednie i następujące miesiące, w odniesieniu do widocznego miesiąca, to powiadomienie będzie wysyłane za każdym razem, gdy zostanie wybrany nowy miesiąc.

Aby prawidłowo obsłużyć ten komunikat, należy określić, ile miesięcy informacje o stanie są żądane, zainicjować tablicę struktur **MONTHDAYSTATE** z prawidłowymi wartościami i zainicjować element członkowski struktury powiązanej z nowym zawartych. Poniższa procedura `CMonthCalCtrl` , szczegółowo niezbędne kroki, zakłada, że masz obiekt o nazwie *m_monthcal* i tablicę obiektów **MONTHDAYSTATE** , *mdState*.

#### <a name="to-handle-the-mcn_getdaystate-notification-message"></a>Aby obsłużyć komunikat powiadomienia MCN_GETDAYSTATE

1. Za pomocą [kreatora klas](reference/mfc-class-wizard.md)Dodaj procedurę obsługi powiadomień dla komunikatu MCN_GETDAYSTATE do obiektu *M_monthcal* (zobacz [Mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).

1. W treści programu obsługi Dodaj następujący kod:

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   Przykład konwertuje wskaźnik *pNMHDR* na właściwy typ, a następnie określa, ile miesięcy informacji jest żądanych (`pDayState->cDayState`). Dla każdego miesiąca bieżąca pole bitowe (`pDayState->prgDayState[i]`) jest inicjowana do zera, a następnie są ustawiane daty w tym przypadku (w tym przypadku 15. każdego miesiąca).

## <a name="see-also"></a>Zobacz także

[Korzystanie z CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
