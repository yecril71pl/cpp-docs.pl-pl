---
title: "Dzielenie wyrazów w formantach edycji wzbogaconej | Dokumentacja firmy Microsoft"
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
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 12ae5d682515a6f266b7e41a2ff89148ea98c0b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="word-breaks-in-rich-edit-controls"></a>Podziały wyrazów w formantach edycji wzbogaconej
Kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) wywołuje funkcję o nazwie "word podziału procedury" Aby znaleźć przerw między wyrazami i określić, gdzie może spowodować nieprawidłowe wierszy. Formant używa tych informacji podczas wykonywania operacji zawijania słów oraz podczas przetwarzania kombinacji klawiszy CTRL + Strzałka w lewo i CTRL + Strzałka w prawo. Aplikacja może wysyłać wiadomości do kontrolki edycji wzbogaconej zastąpić procedury dzielenia wyrazów domyślne, można pobrać informacji o dzielenie wyrazów i określić, co wiersz danego znaku znajduje się.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

