---
title: 'Czas, który upłynął: Klasy automatyzacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- adding dates
- calculating dates and times
- dates, calculating intervals
- elapsed time, calculating in Automation
- Automation classes, elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: 26b34b37-c10e-4b91-82c3-1dc5ffb5361f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1abf6274137ae67b159ad43612d24020a0d14e9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354971"
---
# <a name="elapsed-time-automation-classes"></a>Czas, który upłynął: Klasy automatyzacji
Ta procedura przedstawia sposób obliczania różnicy między dwiema `CTime` obiektów i get `CTimeSpan` wynik.  
  
#### <a name="to-calculate-elapsed-time"></a>Aby obliczyć czas, który upłynął  
  
1.  Utwórz dwa `COleDateTime` obiektów.  
  
2.  Wartość dla jednego z `COleDateTime` obiekty do bieżącego czasu.  
  
3.  Wykonaj niektórych czasochłonnym zadaniem.  
  
4.  Ustaw innych `COleDateTime` obiektu do bieżącego czasu.  
  
5.  Zająć różnicę między dwiema wartościami godziny.  
  
     [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Data i godzina: obsługa automatyzacji](../atl-mfc-shared/date-and-time-automation-support.md)

