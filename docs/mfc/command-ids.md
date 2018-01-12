---
title: "Identyfikatory poleceń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b651c734fbd7098705801aefcaa490293a4d661d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="command-ids"></a>Identyfikatory poleceń
Polecenie szczegółowo opisano za pomocą jego Identyfikatora polecenia wyłącznie (zakodowane w **WM_COMMAND** komunikat). Ten identyfikator jest przypisany do obiektu interfejsu użytkownika, który generuje polecenia. Zazwyczaj identyfikatory są nazywane funkcji obiektu interfejsu użytkownika, które są przypisane.  
  
 Na przykład element Wyczyść wszystko w menu Edycja mogą być przypisywane Identyfikatora takich jak **id_edit_clear_all —**. Biblioteka klas powoduje wstępne definiowanie niektóre identyfikatory, szczególnie w przypadku poleceń w ramach obsługi przez siebie, takich jak **id_edit_clear_all —** lub `ID_FILE_OPEN`. Utworzysz innych identyfikatorów poleceń samodzielnie.  
  
 Podczas tworzenia własnych menu w programie Visual C++ edytora menu, jest dobrym rozwiązaniem, które należy wykonać w bibliotece klas programu do konwencji nazewnictwa jak pokazano `ID_FILE_OPEN`. [Polecenia standardowe](../mfc/standard-commands.md) wyjaśniono standardowych poleceń zdefiniowanych przez biblioteki klas.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty interfejsu użytkownika i identyfikatory poleceń](../mfc/user-interface-objects-and-command-ids.md)

