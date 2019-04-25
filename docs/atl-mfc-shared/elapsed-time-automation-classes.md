---
title: 'Upłynęło czasu: Klasy automatyzacji'
ms.date: 11/04/2016
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
ms.openlocfilehash: d6a77d57a88166354fcb222c0da09690426108e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235798"
---
# <a name="elapsed-time-automation-classes"></a>Upłynęło czasu: Klasy automatyzacji

Ta procedura pokazuje, jak można obliczyć różnicę między dwoma `CTime` obiektów i get `CTimeSpan` wynik.

## <a name="to-calculate-elapsed-time"></a>Do obliczania upływu czasu

1. Utworzyć dwa `COleDateTime` obiektów.

1. Ustawić jeden z `COleDateTime` obiekty do bieżącego czasu.

1. Wykonywać pewne bardzo czasochłonnym zadaniem.

1. Ustaw innych `COleDateTime` obiekt do bieżącego czasu.

1. Podjąć różnicę między dwiema wartościami godziny.

   [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]

## <a name="see-also"></a>Zobacz także

[Data i godzina: Obsługa automatyzacji](../atl-mfc-shared/date-and-time-automation-support.md)
