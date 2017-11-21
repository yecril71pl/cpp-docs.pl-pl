---
title: "Używanie niestandardowych ciągów formatu w selektora dat i godzin kontrolki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CDateTimeCtrl class [MFC], display styles
- DateTimePicker control [MFC], display styles
- DateTimePicker control [MFC]
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 95ce4882f05dece5fc00b6a00cb994e5e78b479d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Formanty](../mfc/controls-mfc.md)

