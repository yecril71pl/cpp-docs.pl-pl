---
title: "Mapowanie komunikatów systemu Windows na klasę | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4701b0ae9f71099febb1a239cea6285fb0a7b229
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mapping-windows-messages-to-your-class"></a>Mapowanie komunikatów systemu Windows na klasę
Twoje okno dialogowe do obsługi komunikatów systemu Windows, należy zastąpić funkcje obsługi odpowiednie. Aby to zrobić, użyj okna właściwości do [mapy komunikatów](../mfc/reference/mapping-messages-to-functions.md) do klasy okien dialogowych. Zapisuje wpisu mapy komunikatów dla każdego komunikatu i dodaje funkcje Członkowskie obsługi wiadomości do klasy. Edytor kodu źródłowego języka Visual C++ umożliwia pisanie kodu w programy obsługi wiadomości.  
  
 Możesz też przesłonić funkcji Członkowskich [cdialog —](../mfc/reference/cdialog-class.md) i jej klas podstawowych, szczególnie [CWnd](../mfc/reference/cwnd-class.md).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Obsługa i mapowanie komunikatów](../mfc/message-handling-and-mapping.md)  
  
-   [Powszechnie zastępowane funkcje Członkowskie](../mfc/commonly-overridden-member-functions.md)  
  
-   [Powszechnie dodawane funkcje Członkowskie](../mfc/commonly-added-member-functions.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Okna dialogowe](../mfc/dialog-boxes.md)   
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

