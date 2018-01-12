---
title: "Ustawianie stanu dnia miesiąca w formancie kalendarza | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MCN_GETDAYSTATE
dev_langs: C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c634815065c68cceb3c528222c0fd60e19b6827
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Ustawianie stanu dnia formantu kalendarza miesięcznego
Jeden z atrybutów formant kalendarza miesięcznego jest możliwość przechowywania informacji o określonych jako stanu dnia formantu, dla każdego dnia miesiąca. Te informacje jest używany do wyróżnienia niektórych dat w miesiącu aktualnie wyświetlany.  
  
> [!NOTE]
>  `CMonthCalCtrl` Obiekt musi mieć **MCS_DAYSTATE** stylu, aby wyświetlić informacje o stanie dnia.  
  
 Informacje o stanie dnia jest wyrażona jako typ danych 32-bitowy, **MONTHDAYSTATE**. Każdy bit w **MONTHDAYSTATE** pole bitowe (od 1 do 31) reprezentuje stan dzień w miesiącu. Jeśli bit jest włączona, zostanie wyświetlony odpowiedni dzień pogrubiona; w przeciwnym razie będą wyświetlane nie wyróżnieniem.  
  
 Istnieją dwie metody do ustawiania stanu dnia formantu kalendarza miesięcznego: jawnie w wyniku wywołania [CMonthCalCtrl::SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) lub obsługa **mcn_getdaystate —** wiadomość z powiadomieniem.  
  
## <a name="handling-the-mcngetdaystate-notification-message"></a>Obsługa mcn_getdaystate — powiadomienie  
 **Mcn_getdaystate —** komunikatów są wysyłane przez formant ustalenie, jak powinny być wyświetlane dni w ciągu widoczny miesięcy.  
  
> [!NOTE]
>  Ponieważ formant buforuje poprzedniego i następnego miesiąca, w odniesieniu do widoczny miesiąc otrzymasz powiadomienie za każdym razem, gdy wybrano na nowy miesiąc.  
  
 Aby poprawnie obsługiwać tego komunikatu, należy określić, ile miesiące są informacje o stanie dnia żądania, zainicjowania tablicy **MONTHDAYSTATE** struktury o odpowiednie wartości i zainicjować elementu członkowskiego struktury pokrewne przy użyciu nowych informacji. Poniższej procedury, której opisano kroki niezbędne założono, że `CMonthCalCtrl` obiektu o nazwie `m_monthcal` i tablica **MONTHDAYSTATE** obiektów, `mdState`.  
  
#### <a name="to-handle-the-mcngetdaystate-notification-message"></a>Do obsługi mcn_getdaystate — powiadomienie  
  
1.  W oknie właściwości, Dodaj procedurę obsługi powiadomień dla **mcn_getdaystate —** wiadomości do `m_monthcal` obiektu (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).  
  
2.  W treści program obsługi Dodaj następujący kod:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]  
  
     Konwertuje przykładzie `pNMHDR` wskaźnika prawidłowego typu, określa, ile miesięcy informacje są żądane (`pDayState->cDayState`). Dla każdego miesiąca, bieżący bitfield (`pDayState->prgDayState[i]`) jest ustawiana na zero, a następnie uruchomienie daty są ustawione (w tym przypadku 15 dnia każdego miesiąca).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

