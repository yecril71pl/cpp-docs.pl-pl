---
title: 'Upłynęło czasu: Klasy ogólnego przeznaczenia'
ms.date: 11/04/2016
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
ms.openlocfilehash: ebaf77b34411cd55cb3a028bcce9109613b63ed9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676754"
---
# <a name="elapsed-time-general-purpose-classes"></a>Upłynęło czasu: Klasy ogólnego przeznaczenia

Poniższa procedura pokazuje, jak obliczyć różnicę między dwoma `CTime` obiektów i get `CTimeSpan` wynik. Użyj `CTime` i `CTimeSpan` obiekty do obliczania upływu czasu, w następujący sposób:

   [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]

Gdy obliczonych `elapsedTime`, można użyć funkcji składowych `CTimeSpan` można wyodrębnić składniki wartość czasu, który upłynął.

