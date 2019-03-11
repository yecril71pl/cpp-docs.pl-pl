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
ms.openlocfilehash: f1183bc5fd42a59c73556d6fdecfd45c781e8cd7
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739731"
---
# <a name="current-time-automation-classes"></a>Bieżący czas: Klasy automatyzacji

Poniższa procedura przedstawia sposób tworzenia `COleDateTime` obiektu i zainicjować go w bieżącym czasem.

## <a name="to-get-the-current-time"></a>Aby uzyskać bieżący czas

1. Tworzy obiekt `COleDateTime`.

1. Wywołaj `GetCurrentTime`.

   [!code-cpp[NVC_ATLMFC_Utilities#177](../atl-mfc-shared/codesnippet/cpp/current-time-automation-classes_1.cpp)]

## <a name="see-also"></a>Zobacz także

[Data i godzina: Obsługa automatyzacji](../atl-mfc-shared/date-and-time-automation-support.md)
