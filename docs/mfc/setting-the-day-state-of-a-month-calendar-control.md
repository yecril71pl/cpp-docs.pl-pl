---
title: Ustawianie stanu dnia miesiąca w kalendarzu kontrolki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MCN_GETDAYSTATE
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b443e1758f766b7fa2dd9a0169ab98172423779d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439345"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Ustawianie stanu dnia formantu kalendarza miesięcznego

Jeden z atrybutów kontrolkę kalendarza miesięcznego jest możliwość przechowywania informacji, nazywane stanu dnia formantu, dla każdego dnia miesiąca. Te informacje są używane w celu wyróżnienia określonych dat w miesiącu, aktualnie wyświetlany.

> [!NOTE]
>  `CMonthCalCtrl` Obiekt musi mieć styl MCS_DAYSTATE, aby wyświetlić informacje o stanie dnia.

Informacje o stanie dnia jest wyrażona jako typu danych 32-bitowych **MONTHDAYSTATE**. Każdy bit w **MONTHDAYSTATE** pole bitowe (od 1 do 31) reprezentuje stan dzień w miesiącu. Jeśli bit jest włączony, zostanie wyświetlony odpowiedni dzień pogrubiona; w przeciwnym razie zostanie wyświetlony ze nie szczególnym.

Istnieją dwie metody do ustawiania stanu dnia formantu kalendarza miesięcznego: jawnie wywołaniem [CMonthCalCtrl::SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) lub dzięki obsłudze mcn_getdaystate — powiadomienie.

## <a name="handling-the-mcngetdaystate-notification-message"></a>Obsługa mcn_getdaystate — powiadomienie

Komunikat mcn_getdaystate — jest wysyłany przez kontrolkę ustalenie, jak powinna być wyświetlana dni w ciągu miesięcy widoczne.

> [!NOTE]
>  Ponieważ kontrolki buforuje poprzednich i następnych miesięcy, w odniesieniu do widocznych miesiąca, otrzymasz to powiadomienie za każdym razem, gdy wybrano nowego miesiąca.

Aby poprawnie obsłużyć ten komunikat, należy określić liczbę miesięcy są informacje o stanie dnia żądania, zainicjować tablicę **MONTHDAYSTATE** struktury z odpowiednimi wartościami i inicjowania elementu członkowskiego struktury pokrewne o nowe informacje. W poniższej procedurze, ze szczegółami dotyczącymi niezbędne kroki przyjęto, że masz `CMonthCalCtrl` obiektu o nazwie *m_monthcal* oraz tablicę **MONTHDAYSTATE** obiektów *mdState*.

#### <a name="to-handle-the-mcngetdaystate-notification-message"></a>Aby obsłużyć mcn_getdaystate — powiadomienie

1. W oknie właściwości. Dodawanie obsługi powiadomienie do wiadomości mcn_getdaystate — *m_monthcal* obiekt (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).

1. W treści procedury obsługi Dodaj następujący kod:

     [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

     Przykład konwertuje *pNMHDR* wskaźnik do odpowiedniego typu, określa liczbę miesięcy informacje są żądane (`pDayState->cDayState`). W każdym miesiącu, a bieżąca bitfield (`pDayState->prgDayState[i]`) jest ustawiana na zero, a następnie wymagane daty są ustawione (w tym przypadku 15 dnia każdego miesiąca).

## <a name="see-also"></a>Zobacz też

[Korzystanie z CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

