---
title: 'Bieżący czas: Klasy automatyzacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- time, setting current
- current time, COleDateTime object
- procedures, getting current time
- Automation classes, current time
- time, getting current
ms.assetid: cc967f17-1189-4cf3-85f9-1969462d5f72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9f267653f87ffcaf357a20abd5d72fd148d7900
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753438"
---
# <a name="current-time-automation-classes"></a>Bieżący czas: Klasy automatyzacji

Poniższa procedura przedstawia sposób tworzenia `COleDateTime` obiektu i zainicjować go w bieżącym czasem.

#### <a name="to-get-the-current-time"></a>Aby uzyskać bieżący czas

1. Tworzy obiekt `COleDateTime`.

2. Wywołaj `GetCurrentTime`.

   [!code-cpp[NVC_ATLMFC_Utilities#177](../atl-mfc-shared/codesnippet/cpp/current-time-automation-classes_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Data i godzina: obsługa automatyzacji](../atl-mfc-shared/date-and-time-automation-support.md)

