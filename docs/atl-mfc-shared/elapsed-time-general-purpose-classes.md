---
title: 'Czas, który upłynął: Ogólnego przeznaczenia klas | Dokumentacja firmy Microsoft'
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
- elapsed time, calculating
- elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: e5c5d3d2-ce1d-409e-875c-98848434e716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff7ef11bb20124a05e2e85c408ce27de8f982546
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354269"
---
# <a name="elapsed-time-general-purpose-classes"></a>Czas, który upłynął: Klasy ogólnego przeznaczenia
Poniższa procedura przedstawia sposób obliczania różnicy między dwiema `CTime` obiektów i get `CTimeSpan` wynik.  
  
#### <a name="to-calculate-elapsed-time"></a>Aby obliczyć czas, który upłynął  
  
1.  Użyj `CTime` i `CTimeSpan` obiekty do obliczenia czas, który upłynął, w następujący sposób:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]  
  
     Po obliczonych `elapsedTime`, można użyć funkcji Członkowskich `CTimeSpan` wyodrębnić składniki wartość czasu, który upłynął.  
  
## <a name="see-also"></a>Zobacz też  
 [Data i godzina: klasy ogólnego przeznaczenia](../atl-mfc-shared/date-and-time-general-purpose-classes.md)

