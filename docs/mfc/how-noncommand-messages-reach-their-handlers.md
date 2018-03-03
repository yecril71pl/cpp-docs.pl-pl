---
title: "Jak komunikaty niebędące poleceniami docierają do swoich programów obsługi | Dokumentacja firmy Microsoft"
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
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 33d0d65c9916cfc571ecfd623138938c0c883ba5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Jak komunikaty niebędące poleceniami docierają do swoich programów obsługi
W odróżnieniu od polecenia standardowe komunikaty systemu Windows nie pobrać kierowane do celów podporządkowania, ale są zazwyczaj obsługiwane przez okno, do której system Windows wysyła wiadomość. Okno może być główne okno ramowe, podrzędnego okna MDI, formantu standardowego, okno dialogowe, widoku lub innego rodzaju okna podrzędnego.  
  
 W czasie wykonywania, każde okno systemu Windows jest dołączony do obiektu okna (pochodzi bezpośrednio lub pośrednio od `CWnd`) mający własną skojarzone mapy i obsługi funkcji obsługi wiadomości. Platforma korzysta z mapy komunikatów — podobnie jak w przypadku polecenia — do mapowania obsługi wiadomości przychodzących.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)

