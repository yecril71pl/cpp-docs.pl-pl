---
title: Ustawianie stanu dnia miesiąca w formancie kalendarza | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 6d4254448e3f8f5a23acd9a303788fd13afb2f84
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950798"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Ustawianie stanu dnia formantu kalendarza miesięcznego
Jeden z atrybutów formant kalendarza miesięcznego jest możliwość przechowywania informacji o określonych jako stanu dnia formantu, dla każdego dnia miesiąca. Te informacje jest używany do wyróżnienia niektórych dat w miesiącu aktualnie wyświetlany.  
  
> [!NOTE]
>  `CMonthCalCtrl` Obiekt musi mieć styl MCS_DAYSTATE, aby wyświetlić informacje o stanie dnia.  
  
 Informacje o stanie dnia jest wyrażona jako typ danych 32-bitowy, **MONTHDAYSTATE**. Każdy bit w **MONTHDAYSTATE** pole bitowe (od 1 do 31) reprezentuje stan dzień w miesiącu. Jeśli bit jest włączona, zostanie wyświetlony odpowiedni dzień pogrubiona; w przeciwnym razie będą wyświetlane nie wyróżnieniem.  
  
 Istnieją dwie metody do ustawiania stanu dnia formantu kalendarza miesięcznego: jawnie w wyniku wywołania [CMonthCalCtrl::SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) lub obsługa mcn_getdaystate — powiadomienie.  
  
## <a name="handling-the-mcngetdaystate-notification-message"></a>Obsługa mcn_getdaystate — powiadomienie  
 Aby określić sposób wyświetlania dni w ciągu widoczny miesięcy przez formant jest wysyłany komunikat mcn_getdaystate —.  
  
> [!NOTE]
>  Ponieważ formant buforuje poprzedniego i następnego miesiąca, w odniesieniu do widoczny miesiąc otrzymasz powiadomienie za każdym razem, gdy wybrano na nowy miesiąc.  
  
 Aby poprawnie obsługiwać tego komunikatu, należy określić, ile miesiące są informacje o stanie dnia żądania, zainicjowania tablicy **MONTHDAYSTATE** struktury o odpowiednie wartości i zainicjować elementu członkowskiego struktury pokrewne przy użyciu nowych informacji. Poniższej procedury, której opisano kroki niezbędne założono, że `CMonthCalCtrl` obiektu o nazwie *m_monthcal* i tablica **MONTHDAYSTATE** obiektów, *mdState*.  
  
#### <a name="to-handle-the-mcngetdaystate-notification-message"></a>Do obsługi mcn_getdaystate — powiadomienie  
  
1.  W oknie właściwości, Dodaj obsługi powiadomień dla wiadomości mcn_getdaystate — *m_monthcal* obiektu (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).  
  
2.  W treści program obsługi Dodaj następujący kod:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]  
  
     Konwertuje przykładzie *pNMHDR* wskaźnika prawidłowego typu, określa, ile miesięcy informacje są żądane (`pDayState->cDayState`). Dla każdego miesiąca, bieżący bitfield (`pDayState->prgDayState[i]`) jest ustawiana na zero, a następnie uruchomienie daty są ustawione (w tym przypadku 15 dnia każdego miesiąca).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

