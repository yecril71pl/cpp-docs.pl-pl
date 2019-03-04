---
title: Mapowanie komunikatów
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], about message maps
- mappings [MFC], commands
- commands [MFC], mapping
- command mapping [MFC]
- message handling [MFC], connecting to handler functions
- commands [MFC], connecting to handler functions
- mappings [MFC], messages
- messages [MFC], mapping
ms.assetid: 996f0652-0698-4b8c-b893-cdaa836d9d0f
ms.openlocfilehash: 82c55c82d6b7a3faa65906345137885555a57d08
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287287"
---
# <a name="mapping-messages"></a>Mapowanie komunikatów

Każda klasa framework, która może odbierać komunikaty lub poleceń ma swój własny "mapie komunikatów." Środowisko wykorzystuje mapy komunikatów, aby nawiązać ich funkcje obsługi wiadomości i poleceń. Dowolnej klasy pochodnej z klasy `CCmdTarget` może mieć mapy komunikatów. Inne artykuły dotyczące wyjaśnić mapy komunikatów szczegółowo oraz opisano, jak z nich korzystać.

Pomimo nazwy "mapie komunikatów," komunikat obsługiwać oba modele, mapy komunikaty i polecenia — wszystkie trzy kategorie wiadomości na liście [kategorie komunikatów](../mfc/message-categories.md).

## <a name="see-also"></a>Zobacz także

[Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)
