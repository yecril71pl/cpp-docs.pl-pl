---
title: 'Upłynęło czasu: Klasy automatyzacji | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: d8f36c48cf654379e9db3a99c2404732dca30f63
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860325"
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

## <a name="see-also"></a>Zobacz też

[Data i godzina: obsługa automatyzacji](../atl-mfc-shared/date-and-time-automation-support.md)
