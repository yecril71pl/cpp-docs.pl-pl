---
title: "Uzyskiwanie dostępu do osadzonych miesiąca w formancie kalendarza | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e37d23a7d5d860d55e18f709c873a40d8f24f1c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="accessing-the-embedded-month-calendar-control"></a>Uzyskiwanie dostępu do osadzonego formantu kalendarza miesięcznego
Obiekt formantu osadzonego miesiąc kalendarza jest możliwy z `CDateTimeCtrl` obiektu o wywołaniu [GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl) funkcję elementu członkowskiego.  
  
> [!NOTE]
>  Formant kalendarza miesięcznego osadzonych jest używana tylko wtedy, gdy formant selektora daty i godziny nie ma **DTS_UPDOWN** styl zestawu.  
  
 Jest to przydatne, jeśli chcesz zmodyfikować niektóre atrybuty, przed wyświetleniem osadzonego formantu. W tym celu należy obsługiwać **dtn_dropdown —** powiadomień, pobrać formant kalendarza miesięcznego (przy użyciu [CDateTimeCtrl::GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)) i wprowadzić modyfikacje. Niestety w formancie kalendarza miesięcznego nie jest trwały.  
  
 Innymi słowy, gdy użytkownik zażąda wyświetlanie w formancie kalendarza miesięcznego, formancie kalendarza miesięcznego nowy jest tworzony (przed **dtn_dropdown —** powiadomień). Formantu zostanie zniszczony (po **dtn_closeup —** powiadomień) odrzucania przez użytkownika. Oznacza to, czy wszystkie atrybuty, które można zmodyfikować, przed wyświetleniem osadzonego formantu, zostaną utracone odrzucania osadzonego formantu.  
  
 W poniższym przykładzie pokazano tej procedury przy użyciu programu obsługi dla **dtn_dropdown —** powiadomień. Kod zmienia kolor tła w formancie kalendarza miesięcznego wywołaniem [SetMonthCalColor](../mfc/reference/cdatetimectrl-class.md#setmonthcalcolor), aby szary. Kod jest następujący:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]  
  
 Jak wspomniano wcześniej, wszystkie zmiany właściwości formantu kalendarza miesięcznego zostaną utracone z dwoma wyjątkami na odrzucania osadzonego formantu. Już został omówiony pierwszy wyjątek, kolory w formancie kalendarza miesięcznego. Drugi wyjątek to czcionkę używaną przez formant kalendarza miesięcznego. Można zmodyfikować domyślną czcionkę wywołania do [CDateTimeCtrl::SetMonthCalFont](../mfc/reference/cdatetimectrl-class.md#setmonthcalfont), przekazywanie dojście istniejących czcionki. Poniższy przykład (gdzie `m_dtPicker` jest obiekt formantu Data i godzina) przedstawia jedną z możliwych metod:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]  
  
 Gdy czcionka została zmieniona, w wyniku wywołania `CDateTimeCtrl::SetMonthCalFont`, nowych czcionek są przechowywane i użyte przy następnym kalendarza miesięcznego ma być wyświetlany.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

