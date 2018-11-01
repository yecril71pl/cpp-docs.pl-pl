---
title: Zastępowanie standardowego routingu poleceń
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
ms.openlocfilehash: 132831939c05f7e8f84c306f5d08bba9cd5e8ea4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648448"
---
# <a name="overriding-the-standard-command-routing"></a>Zastępowanie standardowego routingu poleceń

W rzadkich przypadkach po musi implementować różnice w routingu standardowa platforma można zastąpić go. Chodzi o to, można zmienić, routing w co najmniej jedną klasę przez zastąpienie `OnCmdMsg` w tych klas. To zrobić:

- W klasie, która dzieli kolejności do przekazania do obiektu inną niż domyślna.

- Nowy obiekt inny niż domyślny lub obiekty docelowe poleceń z kolei może przekazać co polecenia, aby.

Jeśli niektóre nowy obiekt Wstawianie routingu, swojej klasie musi być klasą elemencie docelowym polecenia. W Twojej wersji nadrzędnych `OnCmdMsg`, pamiętaj wywołać wersję, która jest zastąpienie. Zobacz [OnCmdMsg](../mfc/reference/ccmdtarget-class.md#oncmdmsg) funkcji składowej klasy typu `CCmdTarget` w *odwołanie MFC* i wersje tych klas jako `CView` i `CDocument` w kodzie źródłowym podane przykłady.

## <a name="see-also"></a>Zobacz też

[Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)

