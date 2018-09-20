---
title: Mapowanie komunikatów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7324da5eaff15d240cabbaede2c2982021361257
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410984"
---
# <a name="mapping-messages"></a>Mapowanie komunikatów

Każda klasa framework, która może odbierać komunikaty lub poleceń ma swój własny "mapie komunikatów." Środowisko wykorzystuje mapy komunikatów, aby nawiązać ich funkcje obsługi wiadomości i poleceń. Dowolnej klasy pochodnej z klasy `CCmdTarget` może mieć mapy komunikatów. Inne artykuły dotyczące wyjaśnić mapy komunikatów szczegółowo oraz opisano, jak z nich korzystać.

Pomimo nazwy "mapie komunikatów," komunikat obsługiwać oba modele, mapy komunikaty i polecenia — wszystkie trzy kategorie wiadomości na liście [kategorie komunikatów](../mfc/message-categories.md).

## <a name="see-also"></a>Zobacz też

[Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)

