---
title: Używanie niestandardowych ciągów formatu w selektora dat i godzin kontrolki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CDateTimeCtrl class [MFC], display styles
- DateTimePicker control [MFC], display styles
- DateTimePicker control [MFC]
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2b365439f1681cf72bd58218ea4f55fbb2f44c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-custom-format-strings-in-a-date-and-time-picker-control"></a>Używanie niestandardowych ciągów formatu w formancie selektora dat i godzin
Domyślnie formant selektora daty i godziny dostarcza trzy formacie typy (format każdego odpowiadającego stylu unikatowy) do wyświetlania bieżącej daty lub godziny:  
  
-   **DTS_LONGDATEFORMAT** Wyświetla datę w formacie długim generuje danych wyjściowych, takich jak "Środa, 3 stycznia 2000".  
  
-   **DTS_SHORTDATEFORMAT** Wyświetla datę w formacie krótkiej, generuje danych wyjściowych, takich jak "00-1-3".  
  
-   **DTS_TIMEFORMAT** Wyświetla czas w formacie długim generuje danych wyjściowych, takich jak "5:31:42 PM".  
  
 Jednak można dostosować wygląd daty lub godziny przy użyciu ciągu formatu niestandardowego. Ten niestandardowy ciąg składa się z istniejącego formatowania znaków, znaków nonformat lub obu. Po utworzeniu niestandardowy ciąg wywoływania [CDateTimeCtrl::SetFormat](../mfc/reference/cdatetimectrl-class.md#setformat) przekazując tekst niestandardowy. Formant selektora daty i godziny będzie wyświetlana wartość bieżącego przy użyciu ciągu formatu niestandardowego.  
  
 Poniższy przykład kodu (gdzie `m_dtPicker` jest `CDateTimeCtrl` obiektu) przedstawiono możliwe rozwiązanie:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#7](../mfc/codesnippet/cpp/using-custom-format-strings-in-a-date-and-time-picker-control_1.cpp)]  
  
 Oprócz ciągi formatu niestandardowego selektora daty i godziny określa również obsługa [pola wywołania zwrotnego](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

