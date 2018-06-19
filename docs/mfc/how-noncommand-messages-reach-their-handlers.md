---
title: Jak komunikaty niebędące poleceniami docierają do swoich programów obsługi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3999c74bf7a612acb998e7a044c12948d7679d9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343885"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Jak komunikaty niebędące poleceniami docierają do swoich programów obsługi
W odróżnieniu od polecenia standardowe komunikaty systemu Windows nie pobrać kierowane do celów podporządkowania, ale są zazwyczaj obsługiwane przez okno, do której system Windows wysyła wiadomość. Okno może być główne okno ramowe, podrzędnego okna MDI, formantu standardowego, okno dialogowe, widoku lub innego rodzaju okna podrzędnego.  
  
 W czasie wykonywania, każde okno systemu Windows jest dołączony do obiektu okna (pochodzi bezpośrednio lub pośrednio od `CWnd`) mający własną skojarzone mapy i obsługi funkcji obsługi wiadomości. Platforma korzysta z mapy komunikatów — podobnie jak w przypadku polecenia — do mapowania obsługi wiadomości przychodzących.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)

