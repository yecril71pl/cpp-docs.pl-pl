---
title: Zastępowanie standardowego routingu poleceń
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
ms.openlocfilehash: 5383c1053894d44e23baf51b19ac3df4e60158e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410164"
---
# <a name="overriding-the-standard-command-routing"></a>Zastępowanie standardowego routingu poleceń

W rzadkich przypadkach po musi implementować różnice w routingu standardowa platforma można zastąpić go. Chodzi o to, można zmienić, routing w co najmniej jedną klasę przez zastąpienie `OnCmdMsg` w tych klas. To zrobić:

- W klasie, która dzieli kolejności do przekazania do obiektu inną niż domyślna.

- Nowy obiekt inny niż domyślny lub obiekty docelowe poleceń z kolei może przekazać co polecenia, aby.

Jeśli niektóre nowy obiekt Wstawianie routingu, swojej klasie musi być klasą elemencie docelowym polecenia. W Twojej wersji nadrzędnych `OnCmdMsg`, pamiętaj wywołać wersję, która jest zastąpienie. Zobacz [OnCmdMsg](../mfc/reference/ccmdtarget-class.md#oncmdmsg) funkcji składowej klasy typu `CCmdTarget` w *odwołanie MFC* i wersje tych klas jako `CView` i `CDocument` w kodzie źródłowym podane przykłady.

## <a name="see-also"></a>Zobacz także

[Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)
