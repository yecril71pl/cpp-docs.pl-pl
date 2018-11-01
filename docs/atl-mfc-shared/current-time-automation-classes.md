---
title: 'Bieżący czas: Klasy automatyzacji'
ms.date: 11/04/2016
helpviewer_keywords:
- time, setting current
- current time, COleDateTime object
- procedures, getting current time
- Automation classes, current time
- time, getting current
ms.assetid: cc967f17-1189-4cf3-85f9-1969462d5f72
ms.openlocfilehash: 97984376057462daaebbf949e96131e91928a1ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596576"
---
# <a name="current-time-automation-classes"></a>Bieżący czas: Klasy automatyzacji

Poniższa procedura przedstawia sposób tworzenia `COleDateTime` obiektu i zainicjować go w bieżącym czasem.

## <a name="to-get-the-current-time"></a>Aby uzyskać bieżący czas

1. Tworzy obiekt `COleDateTime`.

1. Wywołaj `GetCurrentTime`.

   [!code-cpp[NVC_ATLMFC_Utilities#177](../atl-mfc-shared/codesnippet/cpp/current-time-automation-classes_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Data i godzina: obsługa automatyzacji](../atl-mfc-shared/date-and-time-automation-support.md)
