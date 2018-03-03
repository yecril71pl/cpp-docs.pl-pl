---
title: "Mapowanie komunikatów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c415b12b22c19a5e1f2d19fd9c808a98485eb7ae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mapping-messages"></a>Mapowanie komunikatów
Każda klasa framework, który może odbierać wiadomości lub poleceń ma własną "komunikat mapy." Platformę używa mapy komunikatów do nawiązywania ich funkcje obsługi wiadomości i poleceń. Każda klasa pochodzi od klasy `CCmdTarget` może mieć mapy komunikatów. Inne artykuły mapy komunikatów szczegółowo opisano i sposobu ich używania.  
  
 Mimo nazwy "mapę komunikatów," wiadomość mapy obsługiwać oba komunikaty i polecenia — wszystkie trzy kategorie wiadomości na liście [kategorie komunikatów](../mfc/message-categories.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)

