---
title: Identyfikatory poleceń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0dc27e39f6e2753b7b468e39c283d58c3e585d6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341475"
---
# <a name="command-ids"></a>Identyfikatory poleceń
Polecenie szczegółowo opisano za pomocą jego Identyfikatora polecenia wyłącznie (zakodowane w **WM_COMMAND** komunikat). Ten identyfikator jest przypisany do obiektu interfejsu użytkownika, który generuje polecenia. Zazwyczaj identyfikatory są nazywane funkcji obiektu interfejsu użytkownika, które są przypisane.  
  
 Na przykład element Wyczyść wszystko w menu Edycja mogą być przypisywane Identyfikatora takich jak **id_edit_clear_all —**. Biblioteka klas powoduje wstępne definiowanie niektóre identyfikatory, szczególnie w przypadku poleceń w ramach obsługi przez siebie, takich jak **id_edit_clear_all —** lub `ID_FILE_OPEN`. Utworzysz innych identyfikatorów poleceń samodzielnie.  
  
 Podczas tworzenia własnych menu w programie Visual C++ edytora menu, jest dobrym rozwiązaniem, które należy wykonać w bibliotece klas programu do konwencji nazewnictwa jak pokazano `ID_FILE_OPEN`. [Polecenia standardowe](../mfc/standard-commands.md) wyjaśniono standardowych poleceń zdefiniowanych przez biblioteki klas.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty interfejsu użytkownika i identyfikatory poleceń](../mfc/user-interface-objects-and-command-ids.md)

