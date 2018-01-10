---
title: "Czas, który upłynął: Klasy automatyzacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0e4cf7fef17499910d9664ab26fa1b07438e7900
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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

