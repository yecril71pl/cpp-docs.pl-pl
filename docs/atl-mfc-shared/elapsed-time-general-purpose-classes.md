---
title: 'Upłynęło czasu: Klasy ogólnego przeznaczenia | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: ff07c1b26649ffd591bcab9917cf45fa4c67f30a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43756519"
---
# <a name="elapsed-time-general-purpose-classes"></a>Upłynęło czasu: Klasy ogólnego przeznaczenia

Poniższa procedura pokazuje, jak obliczyć różnicę między dwoma `CTime` obiektów i get `CTimeSpan` wynik. Użyj `CTime` i `CTimeSpan` obiekty do obliczania upływu czasu, w następujący sposób:

   [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]

Gdy obliczonych `elapsedTime`, można użyć funkcji składowych `CTimeSpan` można wyodrębnić składniki wartość czasu, który upłynął.  

