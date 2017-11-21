---
title: "Mapowanie komunikatów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 03a07410f6decb6497312a9f04b421bed367dfad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mapping-messages"></a>Mapowanie komunikatów
Każda klasa framework, który może odbierać wiadomości lub poleceń ma własną "komunikat mapy." Platformę używa mapy komunikatów do nawiązywania ich funkcje obsługi wiadomości i poleceń. Każda klasa pochodzi od klasy `CCmdTarget` może mieć mapy komunikatów. Inne artykuły mapy komunikatów szczegółowo opisano i sposobu ich używania.  
  
 Mimo nazwy "mapę komunikatów," wiadomość mapy obsługiwać oba komunikaty i polecenia — wszystkie trzy kategorie wiadomości na liście [kategorie komunikatów](../mfc/message-categories.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)

